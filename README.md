# MonetizeNow

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

MonetizeNow is an enterprise monetization platform that unifies quoting, billing, and usage metering into a single quote-to-cash system for B2B SaaS companies. It combines a CPQ/quote builder with guided selling, a billing engine supporting subscriptions, credits, and usage-based pricing, multi-currency payments (via Stripe), dunning, revenue recognition, and real-time usage metering. The platform exposes a REST API (base https://api.monetizeplatform.com) authenticated with an x-api-key header: 156 operations across 124 paths covering accounts, contacts, addresses, bill groups, quotes, opportunities, contracts, subscriptions, invoices, payments, payment methods, credits, credit notes, products, offerings, rates, price uplift, usage events, trials, account documents for e-signature, and a self-service checkout flow, plus a 30-event webhook surface. MonetizeNow publishes OpenAPI 3.0.3 per operation inside its ReadMe reference rather than as one downloadable document, and it operates an OAuth-protected hosted MCP server at https://mcp.monetizeplatform.com/mcp that appears nowhere in its documentation. Pre-built connectors integrate Salesforce, HubSpot, Attio, NetSuite, QuickBooks, Xero, DocuSign, Adobe Sign, Anrok, Avalara, and Taxwire. MonetizeNow is backed by Uncork Capital.

**Areas:** Company · Monetization · Billing · Subscription · Usage-Based Pricing · Quote-to-Cash · CPQ · Payments · Invoicing · Revenue · Software-as-a-Service · Fintech

## MonetizeNow on APIs.io

Everything profiled for MonetizeNow is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/monetizenow/](https://apis.io/providers/monetizenow/)** — or go straight to one of the APIs or properties below.

### APIs (21)

- [MonetizeNow Account API](https://apis.io/apis/monetizenow/monetizenow-account-api/) — Accounts track all billing and selling details for a customer.
- [MonetizeNow Account Overview API](https://apis.io/apis/monetizenow/monetizenow-account-overview-api/) — The Account Overview API from MonetizeNow — 2 operation(s) for account overview.
- [MonetizeNow Account Document API](https://apis.io/apis/monetizenow/monetizenow-accountdocument-api/) — The AccountDocument API from MonetizeNow — 7 operation(s) for accountdocument.
- [MonetizeNow Bill Group API](https://apis.io/apis/monetizenow/monetizenow-billgroup-api/) — Billgroup is an object that allows you to group subscriptions. An account can have multiple bill groups representing different departments, people or groups…
- [MonetizeNow Contact API](https://apis.io/apis/monetizenow/monetizenow-contact-api/) — Contacts represent individual, address, and company deatils for your customers.
- [MonetizeNow Contract API](https://apis.io/apis/monetizenow/monetizenow-contract-api/) — The Contract API from MonetizeNow — 6 operation(s) for contract.
- [MonetizeNow Credit API](https://apis.io/apis/monetizenow/monetizenow-credit-api/) — Credits can be used to adjust account balances.
- [MonetizeNow Invoice API](https://apis.io/apis/monetizenow/monetizenow-invoice-api/) — An invoice is an itemized commercial document that records the products or services delivered to the customer, the total amount due, and the preferred…
- [MonetizeNow Offering API](https://apis.io/apis/monetizenow/monetizenow-offering-api/) — Offerings are collections of products that you can sell to customers, they can be subscriptions, one-time, or minimum commit types.
- [MonetizeNow Opportunity API](https://apis.io/apis/monetizenow/monetizenow-opportunity-api/) — The Opportunity API from MonetizeNow — 5 operation(s) for opportunity.
- [MonetizeNow Payment API](https://apis.io/apis/monetizenow/monetizenow-payment-api/) — Payment is an object that represents an amount paid to an invoice.
- [MonetizeNow Payment Gateway API](https://apis.io/apis/monetizenow/monetizenow-payment-gateway-api/) — Payment gateway is a service that helps customer transfer money to pay for invoices.
- [MonetizeNow Price Uplift Configuration API](https://apis.io/apis/monetizenow/monetizenow-price-uplift-configuration-api/) — The Price Uplift Configuration API from MonetizeNow — 1 operation(s) for price uplift configuration.
- [MonetizeNow Products API](https://apis.io/apis/monetizenow/monetizenow-products-api/) — A product is an item that a business sells to its customers.
- [MonetizeNow Quote API](https://apis.io/apis/monetizenow/monetizenow-quote-api/) — The Quote API from MonetizeNow — 18 operation(s) for quote.
- [MonetizeNow Rate API](https://apis.io/apis/monetizenow/monetizenow-rate-api/) — Rates allow you to add prices, pricing logic, currency details, and billing frequency to an offering
- [MonetizeNow Subscription API](https://apis.io/apis/monetizenow/monetizenow-subscription-api/) — Subscriptions are things your customers have been sold or signed up for that can be billed on a recurring basis.
- [MonetizeNow Trial API](https://apis.io/apis/monetizenow/monetizenow-trial-api/) — The Trial API from MonetizeNow — 4 operation(s) for trial.
- [MonetizeNow Usage API](https://apis.io/apis/monetizenow/monetizenow-usage-api/) — APIs to record, update and query usage events
- [MonetizeNow Credit Note API](https://apis.io/apis/monetizenow/monetizenow-credit-note-api/) — The Credit Note API from MonetizeNow — 6 operation(s) for credit note.
- [MonetizeNow Payment Method API](https://apis.io/apis/monetizenow/monetizenow-payment-method-api/) — Payment methods are entities representing the instrument used to collect payments for invoices on a bill group. This can be Credit Cards, Direct Debit, ACH…

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### AsyncAPI (1)

Event-driven and webhook contracts.

- [Monetizenow Webhooks](https://apis.io/asyncapis/monetizenow/monetizenow-webhooks/)

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [monetizenow](https://apis.io/servers/monetizenow/monetizenow/)

#### Overlays (1)

OpenAPI overlays, including conversational phrasing for each operation.

- [Monetizenow Openapi Overlay](https://apis.io/overlays/monetizenow/monetizenow-openapi-overlay/)

#### Security (4)

Authentication, trust centre, and vulnerability disclosure.

- [Monetizenow Authentication](https://apis.io/security/monetizenow/monetizenow-authentication/)
- [Monetizenow Domain Security](https://apis.io/security/monetizenow/monetizenow-domain-security/)
- [Monetizenow Trust Center](https://apis.io/security/monetizenow/monetizenow-trust-center/)
- [Monetizenow Vulnerability Disclosure](https://apis.io/security/monetizenow/monetizenow-vulnerability-disclosure/)

#### OAuth scopes (1)

The permissions the API asks for.

- [Monetizenow Scopes](https://apis.io/scopes/monetizenow/monetizenow-scopes/)

#### Plans and pricing (1)

Published plans, tiers and prices.

- [Monetizenow Plans Pricing](https://apis.io/plans/monetizenow/monetizenow-plans-pricing/)

#### Rate limits (1)

Published request limits.

- [Monetizenow Rate Limits](https://apis.io/rate-limits/monetizenow/monetizenow-rate-limits/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://www.monetizenow.ai/)
- [Documentation](https://docs.monetizenow.io/docs/welcome)
- [Getting started](https://docs.monetizenow.io/reference/getting-started-with-your-api)
- [API reference](https://docs.monetizenow.io/reference)
- [Support](https://www.monetizenow.ai/join-our-slack-community)
- [Blog](https://www.monetizenow.ai/blog)
- [Security](https://www.monetizenow.ai/information-security-policy)
- [Compliance](https://www.monetizenow.ai/information-security-policy)
- [Terms of service](https://www.monetizenow.ai/terms-of-use)
- [Privacy policy](https://www.monetizenow.ai/privacy-policy)
- [Status](https://status.monetizeplatform.com)

## API Evangelist rating

**Kin Score 51.8** — developing · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 73.2 |
| Contract quality | 53.4 |
| Contract governance | 18.2 |
| Operational transparency | 75.0 |
| Developer ergonomics | 39.9 |
| Access clarity | 43.4 |

**Agent readiness 54.9** — agent-native

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | — |
| Reversibility Documented | documented (partial credit) |
| MCP Server | — |
| Auth Clarity | served (partial credit) |
| Idempotency | documented (partial credit) |
| Error Semantics | verified |
| OpenAPI Examples | verified |
| Rate Limit Signal | documented (partial credit) |
| Event Surface Described | yes |
| Agent Skills | derived (partial credit) |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | — |
| Delegated Identity | served (partial credit) |
| Protected Resource Metadata | verified |
| Dynamic Client Registration | yes |
| Agentic Commerce | — |
| Pagination Ratio | partial |
| Operation Distinctiveness | mostly |

**Regulatory alignment 41.1** — Payments

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/monetizenow/](https://apis.io/providers/monetizenow/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for MonetizeNow: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/monetizenow/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
