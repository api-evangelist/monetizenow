---
name: Manage the contract lifecycle
description: Retrieve a contract, amend it mid-term, transfer ownership, and renew it at term end.
api: MonetizeNow API
base_url: https://api.monetizeplatform.com
auth: x-api-key header
operations:
- getContractById
- amendContract
- changeContractOwner
- renewContract
- getAllContractsByAccountId
source: https://docs.monetizenow.io/reference
method: generated
---

# Manage the contract lifecycle

Use this flow to service an existing contract: amendments, ownership changes, and renewals.

## Preconditions
- Tenant API key on the `x-api-key` header; base URL `https://api.monetizeplatform.com`.
- An existing active contract (created from an accepted quote).

## Steps
1. **Find the contract** — `getAllContractsByAccountId` to list an account's contracts, then `getContractById` for detail.
2. **Amend** — `amendContract` to change quantities, add products, or adjust terms mid-term (proration applies per tenant settings). Review `amendment-errors` in the docs for edge cases.
3. **Reassign** — `changeContractOwner` when the account owner changes.
4. **Renew** — `renewContract` at (or ahead of) term end; auto-renewal and early-renewal are also supported via quote settings.

## Conventions & error handling
- Amendments and renewals generate new quotes/subscriptions; subscribe to `contract.updated` and `subscription.updated` webhooks. See `asyncapi/monetizenow-webhooks.yml`.
- Versioning/deprecation: breaking changes are carried in a version header. See `lifecycle/monetizenow-lifecycle.yml`.
- Errors: `401` bad key, `500` contact support. See `errors/monetizenow-problem-types.yml`.
