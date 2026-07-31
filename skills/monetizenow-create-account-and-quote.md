---
name: Create an account and build a quote
description: Create a customer account in MonetizeNow, build a quote with offerings, process it, and send it for acceptance.
api: MonetizeNow API
base_url: https://api.monetizeplatform.com
auth: x-api-key header
operations:
- createAccount
- createNetNewQuote
- saveQuoteOffering
- processQuote
- sendQuote
- acceptQuote
source: https://docs.monetizenow.io/reference
method: generated
---

# Create an account and build a quote

Use this flow to stand up a new customer and get them a quote through MonetizeNow's quote-to-cash API.

## Preconditions
- A tenant API key. Send it on every request as the `x-api-key` header.
- Base URL: `https://api.monetizeplatform.com` (paths are under `/api`).
- A product catalog (products -> offerings -> rates) already configured in the tenant.

## Steps
1. **Create the account** — `createAccount`. Optionally set a caller-owned custom id so the account is addressable/idempotent via `getAccountByCustomId`.
2. **Create a net-new quote** — `createNetNewQuote`, linking it to the account (and an opportunity if you use CRM sync).
3. **Add offerings** — `saveQuoteOffering` for each offering/line the customer is buying; pull available offerings with `getAllOffering` and rates with `getAllRatesByOfferingId`.
4. **Process the quote** — `processQuote` to price and validate it against the rules/approval engine.
5. **Send the quote** — `sendQuote` to deliver it to the buyer (optionally routed through e-signature).
6. **Accept** — `acceptQuote` once the buyer signs; acceptance produces the contract/subscription downstream.

## Conventions & error handling
- Idempotency: prefer custom-id addressing (`*ByCustomId`) so retries don't duplicate accounts/contacts. See `conventions/monetizenow-conventions.yml`.
- Errors: `401` = bad/missing `x-api-key`; `500` = contact support. See `errors/monetizenow-problem-types.yml`.
- Subscribe to `quote.processed` / `quote.accepted` webhooks to react asynchronously. See `asyncapi/monetizenow-webhooks.yml`.
