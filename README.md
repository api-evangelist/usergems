# UserGems (usergems)

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

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
