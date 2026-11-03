# 12 — Acceptance Criteria & Test Matrix

## Functional acceptance
- Admin sees only authorized navigation and data.
- Customer, brief, quote, order, payment, production, asset, and support views map to canonical backend records.
- Search, filters, sorting, pagination, empty/error/loading states behave predictably.
- Customer-visible and internal events remain separated.
- Financial summaries distinguish quoted, due, paid, refunded, and cost amounts.
- No Admin/platform billing UI or data model exists.

## Security acceptance
- Direct API call without valid perimeter identity is denied.
- Forged identity headers are denied.
- Customer Clerk token cannot access admin routes.
- Admin identity without required permission is denied.
- Object-level access is checked server-side.
- CSRF/origin protections cover cookie-authenticated writes.
- Secrets never appear in bundles, source maps, logs, responses, or exports.
- Preview cannot reach production D1/R2 or production payment credentials.
- Cross-customer and cross-role isolation tests pass.

## Financial acceptance
- Customer 50/50 milestones cannot be bypassed.
- Duplicate callbacks settle once.
- Wrong amount/currency/merchant/order reference is rejected or held for review.
- Browser redirect cannot mark an order paid.
- Customer payment identifiers, callbacks and ledger remain isolated from Admin/agent task records.
- Refund and manual adjustments require permissions, reasons, and audit.

## Operational acceptance
- Action runs enforce declared scope and human approval gates.
- Asset delivery requires valid final asset, license/provenance, and approval.
- Revoked links no longer work.
- Audit log records privileged changes without sensitive payloads.
- Dashboard freshness and metric definitions are visible.

## Test matrix
Unit tests for permissions, transitions, money arithmetic, schemas, and mapping; API integration tests for every admin route; contract tests against Public API; browser E2E for key journeys; security tests for IDOR/CSRF/header spoofing; payment simulation with signed fixtures only; environment isolation tests; accessibility and responsive tests.

## Release evidence
A release is not accepted based on screenshots alone. Provide test output, contract compatibility, deployed URL, perimeter allow/deny evidence, environment binding evidence, migration status, and rollback plan.


## Agent acceptance
- Agent tasks persist and resume without duplicate side effects.
- Read/prepare actions work with no mutation authority.
- Tool schema, brand scope, environment, autonomy tier and human grants are checked server-side.
- Consequential actions require fresh single-use approval bound to exact inputs.
- Prompt injection in customer content cannot override policy or trigger tools.
- Emergency pause blocks side-effect tools; agent cannot disable it.
- Every agent result includes verifiable evidence and honest failure/partial status.
- Cross-brand access is denied by default; AVORLUNE-only phase 1 passes isolation tests.
