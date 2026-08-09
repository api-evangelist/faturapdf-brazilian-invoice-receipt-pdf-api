---
name: Attach a PIX QR code to an invoice PDF
description: >-
  Render a scannable PIX QR on a Brazilian fatura by supplying a BR Code the issuer's own bank
  or PSP already generated — and know where the boundary is, because this API never mints one.
api: openapi/faturapdf-brazilian-invoice-receipt-pdf-api-openapi-original.yml
operations: [generateInvoice]
generated: '2026-08-09'
method: generated
source: >-
  Grounded in the generateInvoice operation and the pix_copia_cola field in the harvested
  OpenAPI, plus https://faturapdf.com/guides/pix-br-code-format/.
---

# Attach a PIX QR code to an invoice PDF

## The boundary — read this first

The API **renders** a PIX code; it does **not** create one. `pix_copia_cola` takes an EMV
"copia e cola" BR Code string that the issuer's own bank or PSP already issued. The provider is
explicit about why: minting a payload would imply a claim about who owns a PIX key, which is not
theirs to make.

So: never fabricate a BR Code, never assemble one from a key you were not given, and never guess
a CRC. If the user has no BR Code, that is the blocker to solve first — from their PSP's API, or
with the provider's client-side builder at `https://faturapdf.com/pix.html`.

## Where the BR Code comes from

1. **Dynamic** — request it from the issuer's PSP/bank API per invoice. Correct when you need
   per-invoice reconciliation.
2. **Static** — one BR Code for the issuer's PIX key, optionally with an amount. Fine for
   low-volume or fixed-price billing; reconciliation is then manual.

The format is EMV TLV with a CRC-16/CCITT-FALSE at the end, field by field at
`https://faturapdf.com/guides/pix-br-code-format/`. Two limits bite in practice: the merchant
name is capped at 25 characters and the city at 15.

## Call `generateInvoice`

`POST /invoice` with the normal body, plus:

- `forma_pagamento: "PIX"` — the printed label.
- `pix_copia_cola: "<the BR Code string>"` — max 600 characters.

If `pix_copia_cola` is omitted, no PIX section appears on the document at all.

Everything else is unchanged: `emitente` needs a valid `documento`, prices go in reais not cents,
totals are computed by the API, and `data` should be explicit so the output is reproducible.

## Verify the result

The QR is a real scannable bitmap, not decoration — open the returned PDF and scan it with a
phone before shipping the integration. Median render is around 34 ms with a PIX QR embedded and
3 ms without (the provider's own measurement over 200 local runs, network excluded), so the QR
is the expensive part and still trivial.

## Failure modes specific to this flow

- A malformed or over-length `pix_copia_cola` returns `400 invalid_params` — the message names
  the field. Never retry unchanged.
- A QR that renders but does not scan means the BR Code itself is wrong (usually a bad CRC or an
  over-length name/city field). That is a problem at the source, not at this API.
- Everything else follows the standard table in
  `errors/faturapdf-brazilian-invoice-receipt-pdf-api-problem-types.yml`.
