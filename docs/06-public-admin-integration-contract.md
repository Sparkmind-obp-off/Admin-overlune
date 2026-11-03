# 06 — Public/Admin Integration Contract

## Contract boundary
Public and Admin are separate frontend applications. They integrate through a versioned HTTPS API contract. Admin is a privileged API client, not a second backend.

## Required contract groups
- `/health` and service capability metadata.
- `/admin/session` or equivalent trusted-principal introspection.
- `/admin/dashboard/summary`.
- `/admin/customers`, `/admin/customers/:id`.
- `/admin/catalog`, `/admin/offers`, `/admin/offer-versions`.
- `/admin/briefs`, `/admin/quotes`, `/admin/orders`, `/admin/projects`.
- `/admin/production/jobs`, `/admin/action-runs`.
- `/admin/assets`, `/admin/deliveries`.
- `/admin/customer-payments`.
- `/admin/agent/tasks`, `/admin/agent/approvals`, `/admin/agent/tools`, `/admin/agent/policies` (proposed; only after runtime design and contract review).
- `/admin/support`, `/admin/audit`, `/admin/settings`.

These are logical resource groups, not a claim that routes currently exist. First inventory the actual API in Avorlune and map each screen to existing routes. Add routes only after contract review.

## API standards
- JSON response envelope: `{ data, requestId }` or `{ error: { code, message, details? }, requestId }`.
- Stable opaque IDs; no database IDs exposed as authorization.
- Cursor pagination for large lists; bounded page size.
- Explicit sort/filter allowlists.
- Idempotency keys for money, callback processing, and consequential mutations.
- Optimistic concurrency/version fields for edits to quotes, offers, and order state.
- UTC timestamps; display in configured local timezone.
- Money integer IDR minor units with explicit currency.
- Consistent error codes; no stack traces or secret-bearing details.

## Contract versioning
Use additive, backward-compatible changes where possible. Breaking changes require versioned schema, migration notes, compatibility window, and coordinated release across both repositories. Generate typed clients from OpenAPI or equivalent schema; do not hand-maintain divergent interfaces.

## Cross-repo release
1. Change API contract and tests in the authoritative backend.
2. Publish/update schema artifact.
3. Update Admin typed client and integration tests.
4. Deploy backend backward-compatible change.
5. Deploy Admin.
6. Remove deprecated contract only after usage is verified absent.

## Security
Admin API must independently authenticate trusted admin principal and authorize each action. CORS is not authentication. Hiding routes in UI is not authorization.


## Agent boundary
Agent orchestration, policy and tool execution are privileged server-side capabilities. The Admin frontend submits user intent and displays plans/results; it does not invoke providers or domain mutations directly. All agent operations must call the authoritative API/Tool Gateway with scoped identity and audit context.
