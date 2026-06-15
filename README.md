# UserGems (usergems)

UserGems is a San Francisco-based sales intelligence platform that tracks champion job changes and surfaces buying signals so sales and marketing teams can prioritize outbound and ABM motions. The platform packages 30+ native signals (job changes, contact-level intent, M&A, hiring, web visits), Gem-E AI agents for prospect list building and email personalization, and custom AI scoring trained on 600+ closed-won patterns. UserGems exposes a public REST API at api.usergems.com/v1 that lets customers programmatically add and remove contacts to track for job changes, add and remove target accounts, and honor data-subject deletion requests. The API uses an X-Api-Key header for authentication and processes submissions asynchronously. Native integrations include Salesforce, HubSpot, Microsoft Dynamics, Outreach, Salesloft, Gong Engage, Marketo, LinkedIn Ads, Meta Ads, and Google Ads.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/usergems/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/usergems/refs/heads/main/apis.yml)

## Scope

- **Position:** Consuming
- **Access:** 3rd-Party

## Tags

- Sales Intelligence
- Outbound
- ABM
- Champion Tracking
- Job Changes
- Buying Signals
- AI Scoring
- Sales Engagement
- CRM
- Revenue Operations
- GTM

## Timestamps

- **Created:** 2026-05-25
- **Modified:** 2026-05-25

## APIs

### UserGems API

The UserGems outbound REST API lets customers programmatically add and remove contacts UserGems should track for job changes, add and remove target accounts to source prospects against, and submit data-subject deletion requests. API key auth via X-Api-Key header; base URL https://api.usergems.com/v1. Five operations across three business surfaces.

- **Human URL:** [https://app.usergems.com/api/documentation](https://app.usergems.com/api/documentation)

#### Tags

- Sales Intelligence
- Contacts
- Accounts
- Privacy

#### Properties

- [Documentation](https://app.usergems.com/api/documentation)
- [Documentation](https://www.usergems.com/product/api)
- [OpenAPI](openapi/usergems-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/usergems-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/usergems-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [JSON Schema](json-schema/usergems-contact-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON Schema](json-schema/usergems-account-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON-LD](json-ld/usergems-context.jsonld) — [JSON-LD](https://www.w3.org/TR/json-ld11/)
- [Example](examples/usergems-add-contact-example.json)
- [Example](examples/usergems-add-account-example.json)
- [Example](examples/usergems-privacy-delete-example.json)
- [Spectral Rules](rules/usergems-rules.yml)

## Common Properties

- [Website](https://www.usergems.com)
- [Portal](https://www.usergems.com/product)
- [Documentation](https://app.usergems.com/api/documentation)
- [Documentation](https://help.usergems.com)
- [Documentation](https://help.usergems.com/article/usergems-implementation-guide-salesforce-crm)
- [Documentation](https://help.usergems.com/article/usergems-implementation-guide-hubspot-crm)
- [Documentation](https://help.usergems.com/article/how-many-salesforce-api-calls-does-usergems-use)
- [Documentation](https://help.usergems.com/article/usergems-outreach-configuration)
- [Product](https://www.usergems.com/product/api)
- [Sign Up](https://www.usergems.com/demo)
- [Pricing](https://www.usergems.com/pricing)
- [Blog](https://www.usergems.com/blog)
- [Customers](https://www.usergems.com/customers)
- [Careers](https://www.usergems.com/careers)
- [Contact](https://www.usergems.com/contact)
- [Support](mailto:support@usergems.com)
- [Privacy Policy](https://www.usergems.com/legal/privacy)
- [Terms of Service](https://www.usergems.com/legal/terms)
- [Trust Center](https://www.usergems.com/security)
- [LinkedIn](https://www.linkedin.com/company/usergems)
- [Twitter](https://twitter.com/usergems)
- [GitHub Organization](https://github.com/usergems)
- [Plans](plans/usergems-plans-pricing.yml)
- [Rate Limits](rate-limits/usergems-rate-limits.yml)
- [Fin Ops](finops/usergems-finops.yml)
- [Integrations](undefined)
- [Features](undefined)

## Maintainers

**FN:** Kin Lane
**Email:** info@apievangelist.com
**URL:** https://apievangelist.com
