# UserGems (usergems)

UserGems is a San Francisco-based sales intelligence platform that tracks champion job changes and surfaces buying signals so sales and marketing teams can prioritize outbound and ABM motions. The platform packages 30+ native signals (job changes, contact-level intent, M&A, hiring, web visits), Gem-E AI agents for prospect list building and email personalization, and custom AI scoring trained on 600+ closed-won patterns.

**URL:** [Visit APIs.json](https://raw.githubusercontent.com/api-evangelist/usergems/refs/heads/main/apis.yml)

**Run:** [Capabilities Using Naftiko](https://github.com/naftiko/fleet?utm_source=api-evangelist&utm_medium=readme&utm_campaign=company-api-evangelist&utm_content=repo)

## Tags

 - Sales Intelligence, Outbound, ABM, Champion Tracking, Job Changes, Buying Signals, AI Scoring, Sales Engagement, CRM, Revenue Operations, GTM

## Timestamps

- **Created:** 2026-05-25
- **Modified:** 2026-05-25

## APIs

### UserGems API

Outbound REST API for programmatically adding and removing tracked contacts, adding and removing target accounts, and honoring data-subject deletion requests. Base URL `https://api.usergems.com/v1`. Authentication via `X-Api-Key` header. Five operations across three business surfaces: Contacts, Accounts, Privacy.

**Human URL:** [https://app.usergems.com/api/documentation](https://app.usergems.com/api/documentation)

- [Documentation](https://app.usergems.com/api/documentation)
- [Product Page](https://www.usergems.com/product/api)
- [OpenAPI](openapi/usergems-api-openapi.yml)
- [JSON Schema — Contact](json-schema/usergems-contact-schema.json)
- [JSON Schema — Account](json-schema/usergems-account-schema.json)
- [JSON-LD Context](json-ld/usergems-context.jsonld)
- [Naftiko Capability — Contacts](capabilities/contacts-contacts.yaml)
- [Naftiko Capability — Accounts](capabilities/accounts-accounts.yaml)
- [Naftiko Capability — Privacy](capabilities/privacy-privacy.yaml)
- [Spectral Rules](rules/usergems-rules.yml)
- [Example — Add Contact](examples/usergems-add-contact-example.json)
- [Example — Add Account](examples/usergems-add-account-example.json)
- [Example — Privacy Delete](examples/usergems-privacy-delete-example.json)

## Operations

| Method | Path | Summary |
|---|---|---|
| POST | `/contact` | Add a contact to track for job changes |
| DELETE | `/contact` | Remove a tracked contact |
| POST | `/account` | Add a target account for prospect sourcing |
| DELETE | `/account` | Remove a target account |
| POST | `/privacy/delete` | Honor a data-subject deletion request |

## Authentication

All requests must include an `X-Api-Key: <your_api_key>` header. API keys are issued by emailing `support@usergems.com`.

## Integrations

| Category | Tools |
|---|---|
| CRM | Salesforce, HubSpot, Microsoft Dynamics |
| Sales Engagement | Outreach, Salesloft, Gong Engage |
| Marketing Automation | HubSpot Marketing, Marketo |
| Advertising | LinkedIn Ads, Meta Ads, Google Ads |
| Productivity | Chrome Extension |

## Commercial Surface

UserGems is sales-led; pricing is quoted via demo. Public materials advertise an ROI money-back guarantee: if $100K spend does not generate $100K in pipeline, UserGems refunds the difference.

- [Plans](plans/usergems-plans-pricing.yml) — API Commons Plans 0.1
- [Rate Limits](rate-limits/usergems-rate-limits.yml) — API Commons Rate Limits 0.1 (includes downstream Salesforce 20K/24h cap)
- [FinOps](finops/usergems-finops.yml) — FOCUS-aligned billing surface

## Compliance

SOC 2 Type 2, GDPR, and CCPA compliance posture per the UserGems Trust Center.

## Maintainers

- Kin Lane — [info@apievangelist.com](mailto:info@apievangelist.com) — [@apievangelist](https://twitter.com/apievangelist) — [apievangelist.com](https://apievangelist.com)
