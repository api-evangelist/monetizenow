---
name: Record usage and bill an invoice
description: Report metered usage events against a subscription, check consumption, preview the invoice, and collect payment.
api: openapi/monetizenow-openapi.json
base_url: https://api.monetizeplatform.com
auth: x-api-key header
operations:
- recordEvents
- getUsageConsumption
- previewInvoice
- getInvoiceById
- payInvoice
source: https://docs.monetizenow.io/reference
method: generated
verified: '2026-08-13'
verified_against: openapi/monetizenow-openapi.json
---

# Record usage and bill an invoice

Use this flow for consumption/usage-based billing: meter events, verify consumption, then invoice and collect.

## Preconditions
- Tenant API key on the `x-api-key` header; base URL `https://api.monetizeplatform.com`.
- An active subscription with a usage-based rate.
- Note the split base path: usage operations live under `/usage`, everything else under `/api`.

## Steps
1. **Record usage** — `recordEvents` (`POST /usage/events`). This is a BATCH endpoint capped at **100 events per request**. It can return partial success: the body is `{status: SUCCESS | PARTIAL | FAILED, failedEvents: [...]}`, so a 2xx does not mean every event landed — always inspect `status` and `failedEvents`. Use `editEventUnits` (`PUT /usage/events/{id}`) / `voidEvent` (`PUT /usage/events/{id}/void`) to correct mistakes.
2. **Verify consumption** — `getUsageConsumption` (`GET /usage/consumption`), `getUsageConsumptionPerDay` (`GET /usage/consumption/perDay/v2`) and `getEvents` (`GET /usage/events`) to confirm what was ingested before the bill run. **Reads are eventually consistent**: near-immediate for events timestamped within 45 days, up to **6 hours** for events older than 45 days. Do not treat an immediate read-back miss as a lost event.
3. **Preview the invoice** — `previewInvoice` (`GET /api/billGroups/{billGroupId}/invoices/preview`) to see charges before finalizing.
4. **Retrieve the invoice** — `getInvoiceById` (`GET /api/invoices/{invoiceId}`) or `getInvoiceByAccountAndBillGroup` after the bill run generates it.
5. **Collect payment** — `payInvoice` (`POST /api/accounts/{accountId}/payments/invoice/{invoiceId}/pay`), `invoiceManualPayment` for offline payments, or `payAllInvoicesByBillGroup` to sweep a bill group.

## Conventions & error handling
- Payments are processed via Stripe under the hood; use `retrievePaymentMethodList` (`GET /api/accounts/{accountId}/paymentMethods`) / `createSetupIntent` to manage stored methods.
- React to `invoice.created` and `invoice.paid` webhooks. See `asyncapi/monetizenow-webhooks.yml`.
- Errors: `400` bad request, `404` "Usage record could not be found for the given event identifier", `500` contact support. `401` = bad key (returned by the gateway, undocumented). See `errors/monetizenow-problem-types.yml`.
- No rate limits are published beyond the 100-event batch cap. See `rate-limits/monetizenow-rate-limits.yml`.
