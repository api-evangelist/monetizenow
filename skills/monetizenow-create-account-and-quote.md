---
name: Create an account and build a quote
description: Create a customer account in MonetizeNow, build a quote with offerings, process it, and send it for acceptance.
api: openapi/monetizenow-openapi.json
base_url: https://api.monetizeplatform.com
auth: x-api-key header
operations:
- createAccount
- createNetNewQuote
- saveQuoteOffering
- processQuote
- sendQuote
- acceptQuote_1
source: https://docs.monetizenow.io/reference
method: generated
verified: '2026-08-13'
verified_against: openapi/monetizenow-openapi.json
---

# Create an account and build a quote

Use this flow to stand up a new customer and get them a quote through MonetizeNow's quote-to-cash API.

## Preconditions
- A tenant API key. Send it on every request as the `x-api-key` header. The key is tenant-wide and unscoped.
- Base URL: `https://api.monetizeplatform.com` (CPQ/billing paths are under `/api`; usage paths are under `/usage`).
- A product catalog (products -> offerings -> rates) already configured in the tenant.

## Steps
1. **Create the account** — `createAccount` (`POST /api/accounts`). Set a caller-owned custom id so the account is addressable and the create is idempotent via `getAccountByCustomId` (`GET /api/accounts/customId/{customId}`).
2. **Create a net-new quote** — `createNetNewQuote` (`POST /api/quotes`), linking it to the account (and an opportunity via `createOpportunity` if you use CRM sync).
3. **Add offerings** — `saveQuoteOffering` (`POST /api/quotes/{quoteId}/quoteOfferings`) for each offering/line the customer is buying; pull available offerings with `getAllOffering` (`GET /api/offerings`) and rates with `getAllRatesByOfferingId` (`GET /api/offerings/{offeringId}/rates`).
4. **Process the quote** — `processQuote` (`POST /api/quotes/{quoteId}/process`) to price and validate it against the rules/approval engine.
5. **Send the quote** — `sendQuote` (`POST /api/quotes/{quoteId}/send`) to deliver it to the buyer (optionally routed through e-signature).
6. **Accept** — `acceptQuote_1` (`POST /api/quotes/{quoteId}/accept`) once the buyer signs; acceptance produces the contract/subscription downstream.

## Conventions & error handling
- Idempotency: there is NO `Idempotency-Key` header. Prefer custom-id addressing (`*ByCustomId`) so retries don't duplicate accounts/contacts; a repeat create with the same custom id returns `409 Custom Id already exists`, which is the success signal for a retry, not a failure. See `conventions/monetizenow-conventions.yml`.
- Pagination on list operations is page-number: `?currentPage=N&pageSize=N`.
- Errors: `400` bad request, `403` principal unauthorized, `404` not found by id, `409` wrong state / duplicate custom id, `500` contact support. `401` = bad/missing `x-api-key` and is returned by the gateway but is not documented on any operation. Bodies are `{status, message}` JSON, not RFC 9457. See `errors/monetizenow-problem-types.yml`.
- No rate limits or `Retry-After` are published; back off conservatively. See `rate-limits/monetizenow-rate-limits.yml`.
- Subscribe to `quote.processed` / `quote.accepted` webhooks to react asynchronously. Deliveries carry no signature — verify by re-reading the resource. See `asyncapi/monetizenow-webhooks.yml`.
