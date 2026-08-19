---
name: Manage UserGems target accounts
description: >-
  Add and remove target accounts so UserGems sources prospects against them,
  routing results back to the right report, signal and CRM record. Use when an
  external system (ICP model, warehouse, CRM view) decides which companies should
  be worked.
api: openapi/usergems-accounts-api-openapi.yml
operations:
  - addAccount
  - deleteAccount
generated: '2026-08-13'
method: generated
source: >-
  openapi/usergems-accounts-api-openapi.yml +
  https://help.usergems.com/article/using-the-usergems-api
---

# Manage UserGems target accounts

## Before you start

- `X-Api-Key: <key>` on every request; one company-wide key, no sandbox.
- Write-only surface — you cannot list, read back, or verify an account.
- 20 requests/second, one account per request.
- Base URL: `https://api.usergems.com/v1`.
- The target **report** must already exist in UserGems. The API references it,
  it does not create it.

## Step 1 — add an account (`addAccount`)

```
curl -X POST "https://api.usergems.com/v1/account" \
  -H "X-Api-Key: $USERGEMS_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "reportId": 12345,
    "name": "Acme Corp",
    "domain": "acme.com",
    "signal": "High Intent Account",
    "salesforceId": "0014x00000ABCDeAAA",
    "customId": "acct_8891"
  }'
```

**`reportId` is required in practice.** The Developer Hub lists it as optional;
UserGems' own Help Center says omitting it fails with `422`. Always send it.

- `name` and `domain` are both required; **`domain` is the matching key**, so
  repeated calls upsert.
- `salesforceId` and `customId` are cross-reference handles into the customer's
  own systems — populate at least one so prospects can be routed back.
- `signal` associates prospects sourced for this account with a workflow.
- `custom` is a free-form string returned to you with the prospects UserGems
  delivers.

Success is `200` with `{"message": "Account added"}` — an enqueueing
acknowledgement, not confirmation the account is being worked.

## Step 2 — remove an account (`deleteAccount`)

```
curl -X DELETE "https://api.usergems.com/v1/account" \
  -H "X-Api-Key: $USERGEMS_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{ "reportName": "Q2-Enterprise-ICP", "name": "Acme Corp", "domain": "acme.com" }'
```

**Add and delete are asymmetric.** Adding takes `reportId`; deleting takes
`reportName`. Different field, different value — keep both mapped in whatever
you use as your source of truth, because the API will not tell you which report
an account currently sits in.

`name` and `domain` are required. `reportName`, `signal`, `salesforceId` and
`customId` narrow the deletion to one routing context.

## Throughput planning

There is no bulk endpoint. To sync N accounts you make N requests, capped at 20
per second, on a company-wide budget shared with every other integration that
holds the same key. For a 50,000-account sync, budget ~42 minutes at the limit
and coordinate with any other system using that key.

## Errors and retries

See `errors/usergems-problem-types.yml`. `422` almost always means a missing
`reportId`. `429` means you exceeded 20 rps — no `Retry-After` is returned, so
back off exponentially. `addAccount` is safe to replay (matches on `domain`);
treat `deleteAccount` as non-replayable.
