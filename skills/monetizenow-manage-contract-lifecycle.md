---
name: Manage the contract lifecycle
description: Retrieve a contract, amend it mid-term, transfer ownership, and renew it at term end.
api: openapi/monetizenow-openapi.json
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
verified: '2026-08-13'
verified_against: openapi/monetizenow-openapi.json
---

# Manage the contract lifecycle

Use this flow to service an existing contract: amendments, ownership changes, and renewals.

## Preconditions
- Tenant API key on the `x-api-key` header; base URL `https://api.monetizeplatform.com`.
- An existing active contract (created from an accepted quote).

## Steps
1. **Find the contract** — `getAllContractsByAccountId` (`GET /api/accounts/{accountId}/contracts`) to list an account's contracts, then `getContractById` (`GET /api/contracts/{contractId}`) for detail.
2. **Amend** — `amendContract` (`POST /api/contracts/{contractId}/amend`) to change quantities, add products, or adjust terms mid-term (proration applies per tenant settings). Review `amendment-errors` in the docs for edge cases.
3. **Reassign** — `changeContractOwner` (`POST /api/contracts/{contractId}/changeOwner/{userId}`) when the account owner changes.
4. **Renew** — `renewContract` (`POST /api/contracts/{contractId}/renew`) at (or ahead of) term end; auto-renewal and early-renewal are also supported via quote settings.

## Conventions & error handling
- Amendments and renewals generate new quotes/subscriptions; subscribe to `contract.updated` and `subscription.updated` webhooks. See `asyncapi/monetizenow-webhooks.yml`.
- Versioning/deprecation: breaking changes are carried in a version header, and there is no `Sunset`/`Deprecation` response header — you cannot detect a pending removal at runtime. See `lifecycle/monetizenow-lifecycle.yml`.
- Errors: `403` "Not authorized to update contract" is a distinct, documented outcome on `changeContractOwner`; `404` not found by id; `500` contact support. `401` = bad key (returned by the gateway, undocumented). See `errors/monetizenow-problem-types.yml`.
- These are non-idempotent POSTs with no `Idempotency-Key`. A retry after a timeout can produce a second amendment or renewal — re-read the contract with `getContractById` before retrying.
