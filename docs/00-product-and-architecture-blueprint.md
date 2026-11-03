# 00 — Product & Architecture Blueprint

## 1. Product definition
AVORLUNE Admin is the private control plane for operating the AVORLUNE AI Product, Creative & Action Marketplace. It is not a customer storefront and must never expose private operational records publicly.

The first operating model remains curated/single-provider: AVORLUNE owns the offers and fulfils the work. Admin manages customers, briefs, quotes, orders, payment milestones, production, deliverables, products, action runs, support, and business configuration.

## 2. Two-repository topology
- `Avorlune`: public/customer application and the existing backend/API implementation baseline.
- `Admin-overlune`: separate admin frontend repository and deployment.
- One authoritative backend/API and operational data model. The API may later be extracted to a dedicated Worker/service, but that is a backend deployment decision—not a third frontend and not permission to fork business logic.
- Admin UI calls the API over HTTPS. No direct D1, R2, provider, or payment-gateway access from the browser.
- Shared contracts are versioned and tested across both repos. Until a dedicated shared package exists, publish OpenAPI/JSON schema and generated types from a controlled contract directory or release artifact.

## 3. Domains
1. Identity and access.
2. Customer and CRM.
3. Catalog, offers, and versioning.
4. Briefs, quotes, orders, and change requests.
5. Customer payments (Duitku order payments).
6. Admin/platform billing (separate domain; meaning awaits owner decision).
7. Production jobs and action runs.
8. Assets, licensing, and delivery.
9. Support and notifications.
10. Reporting, audit, and system settings.

## 4. Environment surfaces
- Local development: synthetic data and local credentials.
- Preview/staging: isolated non-production data and credentials.
- Production: protected admin deployment and production API.
Never attach production D1/R2 or live payment credentials to public previews.

## 5. Non-negotiable invariants
- Customer Clerk identity is never an admin role.
- No public admin registration.
- Private perimeter must protect both admin frontend and admin API.
- Server-side authorization on every privileged request.
- Customer order payments retain 50% deposit before production and 50% balance before final unwatermarked delivery.
- Separate payment domains have separate identifiers, merchant credentials, callbacks, ledgers, permissions, and reports.
- Every mutation is validated, authorized, idempotent where applicable, and audited.
- Human review remains required before external delivery or consequential action.
- No secret or private asset in client bundle, URL, logs, or Git.

## 6. Scope boundary
Initial Admin includes operations, CRM, catalog/offer management, finance visibility, production queue, deliverables, and platform governance. Defer multi-vendor settlement, freelancer payouts, public staff onboarding, complex accounting/tax filing, and unrestricted autonomous external actions.

## 7. Source of truth
The existing Public repository and its current API/data implementation are the baseline to inspect. This blueprint does not authorize rewriting or duplicating that backend. Record every mismatch in a contract gap register before changing either repo.
