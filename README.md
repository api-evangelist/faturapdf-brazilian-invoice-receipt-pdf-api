# FaturaPDF — Brazilian Invoice & Receipt PDF API (faturapdf-brazilian-invoice-receipt-pdf-api)

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

HTTP API that converts a JSON payload into a Brazilian invoice (fatura) or receipt (recibo) PDF. Fiscal-native features include mod-11 checksum-validated CPF/CNPJ, BRL formatting (R$ 1.234,56 computed in integer cents), DD/MM/AAAA dates, the total spelled out in Portuguese, and optional rendering of a caller-supplied PIX BR Code as a scannable QR. Rendered with a pure-JS engine (pdf-lib), no headless browser. Explicitly NOT an NF-e/NFS-e fiscal issuer — it produces a formatted commercial document, not a tax-authority-authorized record. Consumed through the RapidAPI gateway (the origin host is not directly callable) and metered per document, with a free tier of 20 documents a month and no credit card. The provider also publishes free, keyless, client-side tools: an invoice/receipt generator, a CPF/CNPJ generator-validator and a PIX BR Code builder, two of them embeddable as iframes.

**APIs.json:** [https://faturapdf-brazilian-invoice-receipt-pdf-api.apievangelist.com/apis.yml](https://faturapdf-brazilian-invoice-receipt-pdf-api.apievangelist.com/apis.yml)

## Tags

- Invoices
- Receipts
- PDF Generation
- Documents
- Brazil
- Billing
- CPF Validation
- CNPJ Validation
- PIX
- Fintech
- Data Validation

## Timestamps

- **Created:** 2026-08-07
- **Modified:** 2026-08-09

## APIs

### FaturaPDF — Brazilian Invoice & Receipt PDF API Documents API

Geração de fatura/recibo em PDF

- **Human URL:** [https://faturapdf.com/guides/](https://faturapdf.com/guides/)
- **Base URL:** `https://brazilian-invoice-receipt-pdf-api-cpf-cnpj.p.rapidapi.com`

#### Tags

- documents

#### Properties

- [OpenAPI](openapi/faturapdf-brazilian-invoice-receipt-pdf-api-documents-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/faturapdf-brazilian-invoice-receipt-pdf-api-documents-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/faturapdf-brazilian-invoice-receipt-pdf-api-documents-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [L L M S Txt](https://faturapdf.com/llms.txt)
- [Documentation](https://faturapdf.com/guides/)

## Common Properties

- [M C P Server](mcp/faturapdf-brazilian-invoice-receipt-pdf-api-mcp.yml)
- [Developer Portal](https://faturapdf.com/)
- [Documentation](https://faturapdf.com/guides/)
- [API Reference](https://faturapdf.com/openapi.yaml)
- [Getting Started](https://faturapdf.com/guides/generate-invoice-pdf-nodejs/)
- [Support](https://rapidapi.com/leosanchees2014/api/brazilian-invoice-receipt-pdf-api-cpf-cnpj)
- [Pricing](https://faturapdf.com/#pricing)
- [Sign Up](https://rapidapi.com/leosanchees2014/api/brazilian-invoice-receipt-pdf-api-cpf-cnpj)
- [Terms of Service](https://faturapdf.com/terms/)
- [Privacy Policy](https://faturapdf.com/terms/#what-happens-to-the-data-you-send)
- [Status Page](https://faturapdf.com/health)
- [Security](https://faturapdf.com/.well-known/security.txt)
- [OpenAPI](openapi/_original/faturapdf-brazilian-invoice-receipt-pdf-api-openapi-original.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [L L Ms Txt](llms/faturapdf-brazilian-invoice-receipt-pdf-api-llms.txt)
- [Well Known](well-known/faturapdf-brazilian-invoice-receipt-pdf-api-well-known.yml)
- [Security Txt](well-known/faturapdf-brazilian-invoice-receipt-pdf-api-security.txt)
- [Agentic Access](agentic-access/faturapdf-brazilian-invoice-receipt-pdf-api-agentic-access.yml)
- [Vulnerability Disclosure](security/faturapdf-brazilian-invoice-receipt-pdf-api-vulnerability-disclosure.yml)
- [Domain Security](security/faturapdf-brazilian-invoice-receipt-pdf-api-domain-security.yml)
- [Authentication](authentication/faturapdf-brazilian-invoice-receipt-pdf-api-authentication.yml)
- [Conventions](conventions/faturapdf-brazilian-invoice-receipt-pdf-api-conventions.yml)
- [Idempotency](conventions/faturapdf-brazilian-invoice-receipt-pdf-api-conventions.yml)
- [Error Catalog](errors/faturapdf-brazilian-invoice-receipt-pdf-api-problem-types.yml)
- [Lifecycle](lifecycle/faturapdf-brazilian-invoice-receipt-pdf-api-lifecycle.yml)
- [Conformance](conformance/faturapdf-brazilian-invoice-receipt-pdf-api-conformance.yml)
- [Sandbox](sandbox/faturapdf-brazilian-invoice-receipt-pdf-api-sandbox.yml)
- [Components](components/faturapdf-brazilian-invoice-receipt-pdf-api-components.yml)
- [Data Model](data-model/faturapdf-brazilian-invoice-receipt-pdf-api-data-model.yml)
- [Overlay](overlays/faturapdf-brazilian-invoice-receipt-pdf-api-openapi-overlay.yaml)
- [Examples](examples/faturapdf-brazilian-invoice-receipt-pdf-api-generate-invoice-example.json)
- [Plans](plans/faturapdf-brazilian-invoice-receipt-pdf-api-plans.yml)
- [Rate Limits](rate-limits/faturapdf-brazilian-invoice-receipt-pdf-api-rate-limits.yml)
- [Agent Skill](skills/_index.yml)

## Maintainers

**FN:** FaturaPDF — Brazilian Invoice & Receipt PDF API
**Email:** leo.sanchees2014+arenaalfa@gmail.com
**URL:** https://faturapdf.com/
