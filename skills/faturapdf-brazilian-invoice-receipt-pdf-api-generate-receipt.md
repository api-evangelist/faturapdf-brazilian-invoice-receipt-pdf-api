---
name: Generate a Brazilian receipt (recibo) PDF
description: >-
  Produce a Brazilian recibo — the "Recebemos de ..." statement, the amount spelled out in
  Portuguese and a signature line — from the same payload shape as an invoice.
api: openapi/faturapdf-brazilian-invoice-receipt-pdf-api-openapi-original.yml
operations: [generateReceipt, generateInvoice]
generated: '2026-08-09'
method: generated
source: >-
  Grounded in operationIds verified verbatim in the harvested OpenAPI, plus conventions/ and
  errors/ in this repo.
---

# Generate a Brazilian receipt (recibo) PDF

## When to use a recibo

A *recibo* is proof that money was received; a *fatura* is a request for payment. Use this for
freelancer proof-of-payment, marketplace payouts to Brazilian sellers, and any record of a
completed transaction. It is **not** an NF-e or NFS-e — no tax authority authorizes it. If the
transaction legally requires a nota fiscal, say so rather than shipping a recibo in its place.

## Two ways to get one

- `generateReceipt` — `POST /receipt`. Same body as the invoice; `tipo` is forced to `"recibo"`
  server-side. Use this when you only ever emit receipts.
- `generateInvoice` — `POST /invoice` with `tipo: "recibo"`. Use this when one code path emits
  both document kinds.

Both produce identical output for the same payload.

## What changes versus a fatura

- Layout swaps the itemized table for a narrative "Recebemos de ..." statement line.
- The amount is spelled out in Portuguese **automatically** — you do not need
  `mostrar_valor_por_extenso` (that field is the opt-in for invoices only).
- A signature line is drawn with the issuer's name and CPF/CNPJ.
- `vencimento` (due date) is meaningless on a receipt; omit it.

## Call it

`POST /receipt`, `Content-Type: application/json`, header `X-RapidAPI-Key`, against
`https://brazilian-invoice-receipt-pdf-api-cpf-cnpj.p.rapidapi.com`.

Minimum body: `emitente` (with a valid `documento`), `destinatario`, and one entry in `itens`
with `descricao` and `valor_unitario`. Add `numero` for your own record number and
`forma_pagamento` for how the money arrived.

Send `data` explicitly so the document is reproducible; omitted, the server stamps today.

## Read the response

Status first, body second. `200` is raw `application/pdf` bytes. Anything else is JSON
`{error, message}` — see
`errors/faturapdf-brazilian-invoice-receipt-pdf-api-problem-types.yml` for the full table.
The one you will hit most is `400 invalid_params` from a CPF/CNPJ whose mod-11 check digit is
wrong; the message names the offending party.

## Retry and persistence

Retry only `408, 429, 500, 502, 503, 504`, with exponential backoff and jitter. Retries cannot
duplicate anything — the call is stateless and no document is stored. Save the returned bytes
yourself; there is no URL to fetch them from later.
