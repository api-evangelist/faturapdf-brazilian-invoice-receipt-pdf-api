---
name: Generate a Brazilian invoice (fatura) PDF
description: >-
  Turn issuer, customer and line items into a ready-to-send Brazilian fatura PDF, with
  check-digit-validated CPF/CNPJ, BRL formatting and correct retry handling.
api: openapi/faturapdf-brazilian-invoice-receipt-pdf-api-openapi-original.yml
operations: [generateInvoice]
generated: '2026-08-09'
method: generated
source: >-
  Grounded in operationIds verified verbatim in the harvested OpenAPI, plus
  conventions/, errors/ and sandbox/ in this repo.
---

# Generate a Brazilian invoice (fatura) PDF

## What this does

One synchronous call: POST JSON, receive the bytes of a finished PDF. Nothing is stored
server-side and there is no document to fetch afterwards — **you own retention. Save the
bytes when you get them.**

This produces a *formatted commercial document*, not a Nota Fiscal Eletronica. It does not
talk to SEFAZ, issues no NF-e/NFC-e/NFS-e, and produces no chave de acesso or DANFE. If the
user needs a legal nota fiscal, stop and say so.

## Before you call

1. Base URL is the gateway: `https://brazilian-invoice-receipt-pdf-api-cpf-cnpj.p.rapidapi.com`.
   **Never call `faturapdf.com` directly** — it answers `401 {"error":"unauthorized"}`.
2. Auth: header `X-RapidAPI-Key` (server-side credential; never put it in a browser bundle).
   Recommended companion: `X-RapidAPI-Host: brazilian-invoice-receipt-pdf-api-cpf-cnpj.p.rapidapi.com`.
3. Optional liveness probe: `healthCheck` — the origin copy at `https://faturapdf.com/health`
   is public, unauthenticated and unmetered, so use that one for preflight instead of spending quota.
4. Validate CPF/CNPJ locally first (mod-11, published at
   `https://faturapdf.com/guides/cpf-cnpj-check-digit-algorithm/`). A bad check digit is a
   400 and a wasted document from the monthly quota.

## Call `generateInvoice`

`POST /invoice`, `Content-Type: application/json`.

Required: `emitente` (issuer — its `documento` is mandatory), `destinatario` (customer —
`documento` optional), `itens` (1–200 lines, each with `descricao` and `valor_unitario`).

Rules that matter:

- Send **reais, not cents**: `349.90`, never `34990`. The API converts to integer cents
  internally, so no floating-point artefact reaches the document.
- **Never send totals.** `subtotalItem`, `subtotal` and `total` are computed by the API.
- Send `data` explicitly (`AAAA-MM-DD` or `DD/MM/AAAA`). If you omit it the server stamps
  today, and the same payload then renders differently across midnight UTC.
- `tipo` defaults to `fatura`. `desconto` is a flat amount off the subtotal; the total never
  goes negative. `mostrar_valor_por_extenso: true` prints the total in Portuguese words.
- Optional `pix_copia_cola`: a BR Code **the caller's own bank/PSP already issued**. The API
  renders it as a QR; it never mints PIX payloads. Do not fabricate one.

## Read the response correctly

**Branch on the status code before touching the body.** A 200 is raw `application/pdf` bytes;
everything else is JSON `{error, message}`. Decoding the success body as text corrupts the PDF
and throws away the real error.

## Handle failures

| Status | `error` | Do |
|---|---|---|
| 400 | `invalid_json` | Fix your serialization. Never retry. |
| 400 | `invalid_params` | `message` lists every problem at once, semicolon-separated, including which CPF/CNPJ failed. Fix and resubmit. Never retry unchanged. |
| 401 | `unauthorized` | Wrong key, or you called the origin instead of the gateway. |
| 405 | `method_not_allowed` | You sent GET. Both endpoints are POST-only. |
| 413 | `payload_too_large` | Over ~200 KB or more than 200 items. Split the document. |
| 429 | — | Gateway quota exhausted. In a batch job treat as fatal for the run. |
| 500 / 504 | `render_failed` / `render_timeout` | Retry with backoff. |

Retryable set: `408, 429, 500, 502, 503, 504`. Backoff 400 ms, 800 ms, 1600 ms with ±30% jitter.

**Retries are safe.** Generation is a pure function of the payload and nothing is persisted, so
a retry cannot create a duplicate document. There is no idempotency key and none is needed.

## After

Persist the bytes immediately (object store, attachment, DB blob). Regenerating months later
from live data can silently produce a different document from the one the customer received.
