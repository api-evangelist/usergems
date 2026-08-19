---
name: Honor a UserGems data-subject erasure request
description: >-
  Remove a person from all UserGems tracking to satisfy a GDPR or CCPA
  right-to-erasure request. Use when a privacy workflow, DSAR queue or support
  process needs a subject purged from the sales-intelligence layer.
api: openapi/usergems-privacy-api-openapi.yml
operations:
  - privacyDelete
generated: '2026-08-13'
method: generated
source: >-
  openapi/usergems-privacy-api-openapi.yml +
  https://app.usergems.com/api/documentation
---

# Honor a UserGems data-subject erasure request

## When to use this rather than `deleteContact`

- `deleteContact` removes a contact from tracking scopes you choose — one
  relationship type, one signal, or all of them. It is an operational action.
- `privacyDelete` is the **regulatory** action: it removes the email address
  from UserGems tracking entirely, and it is the endpoint UserGems documents for
  GDPR and CCPA erasure obligations.

Use `privacyDelete` for any request that arrives as a data-subject right, and
record it as such in your own audit trail — UserGems returns no receipt beyond
an acknowledgement message.

## Call it (`privacyDelete`)

```
curl -X POST "https://api.usergems.com/v1/privacy/delete" \
  -H "X-Api-Key: $USERGEMS_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{ "email": "jane@example.com" }'
```

`email` is the only field and it is required. Success is `200` with
`{"message": "Contact removed"}`.

## What you must handle yourself

1. **Verify the subject before calling.** There is no read operation, so you
   cannot check that the email is tracked, and you cannot confirm afterwards
   that it was removed. Your own DSAR record is the only evidence trail.
2. **Treat it as irreversible.** Re-adding via `addContact` would create new
   tracking, not restore the prior record — and would itself be a new processing
   decision you may not be entitled to make.
3. **This is a high-consequence call on a shared credential.** The same
   company-wide `X-Api-Key` that ingests contacts also authorizes erasure. If an
   agent holds that key, erasure is inside its blast radius; gate this operation
   behind human approval.
4. **Downstream systems are not covered.** `privacyDelete` removes the subject
   from UserGems. Records UserGems previously wrote into Salesforce, HubSpot,
   Outreach, Salesloft or an ad audience are governed by those systems and must
   be handled separately.

## Errors

Same flat envelope and status set as the rest of the API — see
`errors/usergems-problem-types.yml`. On `429` (20 rps limit) back off and retry;
the operation matches on `email`, so a replay after a genuine failure is safe.
On `500`/`503`, retry, then escalate to support@usergems.com if the erasure
deadline is at risk.
