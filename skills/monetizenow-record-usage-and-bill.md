---
name: Record usage and bill an invoice
description: Report metered usage events against a subscription, check consumption, preview the invoice, and collect payment.
api: MonetizeNow API
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
---

# Record usage and bill an invoice

Use this flow for consumption/usage-based billing: meter events, verify consumption, then invoice and collect.

## Preconditions
- Tenant API key on the `x-api-key` header; base URL `https://api.monetizeplatform.com`.
- An active subscription with a usage-based rate.

## Steps
1. **Record usage** — `recordEvents` to submit metered events (MonetizeNow's metering ingests high event volume). Use `editEventUnits` / `voidEvent` to correct mistakes.
2. **Verify consumption** — `getUsageConsumption` (or `getUsageConsumptionPerDay`) and `getEvents` to confirm what was ingested before the bill run.
3. **Preview the invoice** — `previewInvoice` to see charges before finalizing.
4. **Retrieve the invoice** — `getInvoiceById` (or `getInvoiceByAccountAndBillGroup`) after the bill run generates it.
5. **Collect payment** — `payInvoice` (or `invoiceManualPayment` for offline payments; `payAllInvoicesByBillGroup` to sweep a bill group).

## Conventions & error handling
- Payments are processed via Stripe under the hood; use `retrievePaymentMethodList` / `createSetupIntent` to manage stored methods.
- React to `invoice.created` and `invoice.paid` webhooks. See `asyncapi/monetizenow-webhooks.yml`.
- Errors: `401` bad key, `500` contact support. See `errors/monetizenow-problem-types.yml`.
