# Legal & General (legal-and-general)

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
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

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

## What Legal & General *does* publish (enrichment round 2026-07-25)

Legal & General is closed on the API and unusually open on the front end. Its [Canopy design system](https://github.com/Legal-and-General/canopy) is a genuine, actively released open-source project — and it is **agent-native**:

- **84 installable agent skills** — 69 component best-practice skills and 15 per-major-version migration skills, MIT licensed, installed with `npx skills add Legal-and-General/canopy`, compatible with GitHub Copilot, Claude Code, Cursor and 40+ other agents. See [`skills/_index.yml`](skills/_index.yml) and the [published catalog](https://github.com/Legal-and-General/canopy/blob/master/docs/COPILOT_SKILLS.md).
- **Four Copilot coding agents** in `.github/agents/` (Dependency Updater, Migration Guide Writer, Migration Skill Generator, Best Practice Skill Generator) — documented in [`docs/AGENTIC_AI.md`](https://github.com/Legal-and-General/canopy/blob/master/docs/AGENTIC_AI.md).
- **Dated release history** — semver via semantic-release, currently **v37.0.0 (2026-07-23)**, 20 releases between 2026-06-30 and 2026-07-23.
- **A published breaking-change policy** ([`docs/BREAKING_CHANGES.md`](https://github.com/Legal-and-General/canopy/blob/master/docs/BREAKING_CHANGES.md)) and a **repository security policy** ([`docs/SECURITY.md`](https://github.com/Legal-and-General/canopy/blob/master/docs/SECURITY.md)) — the only vulnerability-reporting route Legal & General publishes anywhere.
- **`@legal-and-general/canopy`** ships through **GitHub Packages**, not public npm, so even the design system needs an authenticated token. No package exists on npm, PyPI, Maven Central, NuGet, pkg.go.dev, RubyGems, Packagist or crates.io.

Two previously unrecorded API hosts were found in DNS this round, and both confirm the partner-gated pattern rather than contradicting it: **`api.landg.com`** resolves but has TCP/443 filtered (no TLS handshake completes), and **`sandbox.legalandgeneral.com`** resolves to CloudFront and returns HTTP 403 on every path. Neither is a public sandbox or a developer portal.

There is still **no corporate security.txt, no bug bounty, no trust centre, no named certification, no status page and no `/.well-known/` document on any host** — 25 well-known probes across five hosts, all 404.

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
