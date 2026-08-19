# FaturaPDF — Brazilian Invoice & Receipt PDF API (faturapdf-brazilian-invoice-receipt-pdf-api)

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
