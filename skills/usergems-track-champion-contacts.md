---
name: Track champion contacts in UserGems
description: >-
  Push contacts into UserGems so it tracks them for job changes, attaching a
  relationship type and custom Signal Fields so the resulting job-change events
  can drive a campaign. Use when a system of record (product DB, warehouse, CRM
  export) holds people worth following when they move.
api: openapi/usergems-contacts-api-openapi.yml
operations:
  - addContact
  - deleteContact
generated: '2026-08-13'
method: generated
source: >-
  openapi/usergems-contacts-api-openapi.yml +
  https://help.usergems.com/article/using-the-usergems-api
---

# Track champion contacts in UserGems

## Before you start

- Auth is a single header: `X-Api-Key: <key>`. There is **one key per company**,
  retrieved from Settings → Connected Applications in the UserGems app. There is
  no sandbox key and no per-integration key, so **every call you make writes to
  live data**.
- This API is **write-only**. There is no GET, no list, no lookup. You cannot
  check whether a contact already exists before or after writing.
- Rate limit is **20 requests per second**, one record per request. There is no
  bulk endpoint and no documented `Retry-After`, so back off on `429` yourself.
- Base URL: `https://api.usergems.com/v1`.

## Step 1 — decide whether you need a Signal

If you only want job-change tracking, omit `signal` entirely. If you want the
contact to feed a Custom Signal (and therefore audiences, scoring and Gem-E
personalization), the Signal must already exist in UserGems with ingestion
method **API**. Create it first in-product; the API only references it by name.

## Step 2 — push the contact (`addContact`)

`POST /contact` with `Content-Type: application/json`.

```
curl -X POST "https://api.usergems.com/v1/contact" \
  -H "X-Api-Key: $USERGEMS_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "email": "jane@example.com",
    "firstName": "Jane",
    "lastName": "Smith",
    "company": "Acme Corp",
    "relationshipType": "Champion",
    "linkedinUrl": "https://www.linkedin.com/in/janesmith",
    "signal": "Credit Limit Exceeded",
    "creditsUsed": 1250
  }'
```

- `email` is the only required field and is **the matching key**. Repeat calls
  for the same email upsert rather than duplicate.
- If you have no email, send a name (`firstName` + `lastName`, or `fullName`)
  **and** `company`.
- `relationshipType` accepts Closed Won Opp Contact, Champion, User, Open Opp
  Contact, Closed Lost Opp Contact, Prospect, Other, or any type the customer
  created in UserGems settings.
- `creditsUsed` above is a **Signal Field**, not a defined property. Any extra
  top-level string property becomes one; up to 100 per contact, names must be
  distinct. This is how you attach the business context Gem-E can reference.
- `custom` is a separate free-form string that UserGems round-trips back to you
  on the eventual job-change event — use it as your correlation handle, since
  there is no request-id header.

Success is `200` with `{"message": "Contact added to queue"}`. That confirms
**enqueueing, not completion**. Do not treat it as proof the record landed; a
contact pushed for job-change tracking will not surface in the prospects
overview until a job change actually fires.

## Step 3 — remove a contact (`deleteContact`)

```
curl -X DELETE "https://api.usergems.com/v1/contact" \
  -H "X-Api-Key: $USERGEMS_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{ "email": "jane@example.com", "relationshipType": "Champion" }'
```

**Scope this deliberately.** `relationshipType` and `signal` are optional, and
leaving both out removes the contact from *all* relationship types and *all*
signals — not just the one you were working with. Always send the narrowest
scope you mean.

Note the reference ambiguity: the Developer Hub labels these fields "Query
Parameters" while its own curl example sends them in a JSON body. Follow the
curl example.

## Errors

Flat `{"message": "..."}` envelope, no error codes, no field-level detail.
`400` bad request · `401` missing/invalid key · `403` not entitled · `405` wrong
method (remember: no GET exists) · `406` non-JSON requested · `429` over 20 rps ·
`500`/`503` retry later. Full catalog: `errors/usergems-problem-types.yml`.

## Retry rules

- `429`, `500`, `503`: retry with exponential backoff. Writes match on `email`,
  so a replayed `addContact` upserts safely.
- **Never blind-retry `deleteContact`.** There is no idempotency key and no way
  to read state back, so a retried delete after a timeout is indistinguishable
  from a second deliberate delete.
