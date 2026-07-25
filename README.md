# Legal & General (legal-and-general)

Legal & General Group plc is a FTSE 100 United Kingdom life insurer, retirement and institutional asset manager headquartered in London and regulated by the FCA and PRA. Its lines of business are life and protection insurance (term life, critical illness, income protection), workplace and individual pensions, annuities and bulk-purchase annuity/pension risk transfer, equity release through Legal & General Home Finance, and asset management through Legal & General Investment Management. It distributes almost entirely through regulated intermediaries — financial advisers, mortgage brokers and employee-benefit consultants — and its API posture follows that model exactly.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/legal-and-general/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/legal-and-general/refs/heads/main/apis.yml)

## API Posture — No Public API

Legal & General publishes **no public, self-serve developer portal**, **no public API reference**, and **no downloadable OpenAPI or Swagger definition**. Reviewed 2026-07-25:

- `developer.`, `developers.`, `docs.`, `api.` and `apis.legalandgeneral.com` — **no DNS record**
- `/developers`, `/developer`, `/api`, `/partners`, `/integrations` — **HTTP 404**
- `/openapi.json`, `/swagger.json`, `/api-docs` — **HTTP 404**
- `/.well-known/openid-configuration`, `/.well-known/oauth-authorization-server` — **HTTP 404**

The nearest integration surface is the [adviser area](https://www.legalandgeneral.com/adviser/) (HTTP 200), which is a **login wall** for regulated financial advisers, not a developer portal. It carries Login and Register links and exposes no reference documentation, schemas or self-serve credentials.

Legal & General's APIs are real but **bilateral and partner-gated**, announced by the counterparty rather than published by Legal & General:

- Legal & General Home Finance real-time equity release **quotations, KFIs and applications** into Iress' *The Exchange* adviser portal
- Equivalent API links into the **Air Sourcing** and **Advise Wise** platforms
- Legal & General Mortgage Club API integration with **Kensington Mortgages**
- Protection **quote-and-apply** through **OLP Connect** and the Existing Business Agent Hub, behind adviser login

### Quote / Bind / Issue / FNOL

| Verb | Exposed | Access |
| --- | --- | --- |
| Quote | Yes | Partner-only (adviser platforms, OLP Connect) |
| Bind | Yes | Partner-only |
| Issue | No | None documented |
| FNOL / Claims | No | None documented |

### ACORD Posture

**No ACORD reference found.** No occurrence of ACORD, AL3, ACORD XML, ACORD certified or NGDS appears anywhere in Legal & General's public surface. That is expected — ACORD's AL3/IVANS agency-download rails are a US property-and-casualty phenomenon, and Legal & General is a UK life, health and pensions carrier. The functional UK equivalent it does use is **Origo**, the UK life and pensions messaging and standards body: Unipass digital certificates as adviser identity, Origo's Unipass Letter of Authority (adopted for workplace pensions), and Origo Track My Apps for adviser case tracking.

### Auth

No public API authentication scheme is documented. Adviser access uses session login with optional **Unipass X.509 digital certificate** association. Partner integration credentialing is bilateral and unpublished.

### Webhooks / Events / Postman / GraphQL

None. No event catalog, no AsyncAPI, no public Postman workspace, no GraphQL surface, no published `.proto`. Absence is the finding.

## Tags

- Insurance
- United Kingdom
- Life Insurance
- Health Insurance
- Employee Benefits
- Pensions
- Annuities
- Asset Management
- Underwriting
- Carrier
- Broker
- Partner Gated
- No Public API

## Timestamps

- **Created:** 2026-07-25
- **Modified:** 2026-07-25

## APIs

None listed. There is no real, documented, publicly accessible Legal & General API to catalog. See [review.yml](review.yml) for the full probe record and provenance.

## Links

- [Website](https://www.legalandgeneral.com/)
- [Corporate Website](https://group.legalandgeneral.com/)
- [Newsroom](https://group.legalandgeneral.com/en/newsroom/press-releases)
- [GitHub Organization](https://github.com/Legal-and-General) — front-end design system (Canopy) only, no API artifacts
- [Login](https://www.legalandgeneral.com/log-in/)
