# 30 — Public ↔ Admin Control Plane & Shared Capability Contract

## Separation of concerns
Public AVORLUNE is the customer-facing storefront and workspace. Admin-overlune is the private operator/AI-agent control plane. Both communicate with the same authoritative backend/API. They are separate frontend deployments, not two independent products or databases.

## Shared capability registry
Backend owns a capability registry with capability_id, version, status, customer_visibility, allowed_brands, supported_inputs, output_contract, provider_route, pricing_policy, quota_policy, moderation_policy, availability_window and rollout flags.

Admin can inspect, configure and propose changes to capability availability, provider routing, limits and pricing. Public reads only the customer-safe published capability projection. Never expose internal provider credentials, private notes, cost margin or operational policy.

## Control flow
1. Owner/operator configures a capability in Admin.
2. Agent proposes a change and displays impact/diff.
3. Policy engine checks authority, brand, environment, budget and risk.
4. Consequential configuration changes require human approval.
5. Backend persists approved version and audit event.
6. Public storefront receives the published customer-safe projection.
7. Customer submits a job/order through Public.
8. Backend validates current capability state, customer eligibility, quote and order rules.
9. Orchestrator routes the job to an approved provider adapter.
10. Admin observes status, cost, errors, quality and evidence.
11. Agent recommends improvements; owner approves any consequential rollout.

## Configuration separation
Draft configuration is private to Admin. Published configuration is versioned and safe for Public. Provider credentials and internal costs never cross into public responses. Public requests cannot override provider, model, budget or policy.

## API contract (proposed)
- GET /api/v1/public/capabilities — published customer-safe catalogue.
- GET /api/v1/public/capabilities/:slug — public capability detail.
- POST /api/v1/public/generation-jobs — authenticated customer request tied to order/project.
- GET /api/v1/public/generation-jobs/:id — only the owning customer may view.
- GET /api/v1/admin/capabilities — authorized internal catalogue/configuration.
- PATCH /api/v1/admin/capabilities/:id — draft-only, policy checked, audited.
- POST /api/v1/admin/capabilities/:id/publish — approval-gated version publish.
- GET /api/v1/admin/generation-jobs — scoped operational monitoring.
- POST /api/v1/admin/generation-jobs/:id/retry|cancel — only when provider semantics and policy permit.
These routes are proposals. Inspect actual routes and schema before implementation.

## Consistency and isolation
Use one source of truth and versioned API contracts. Public and Admin never write directly to D1/R2. Customer identity is scoped to owned records; Admin/agent identity is separate. Every record is brand-scoped. Public sees only published customer-safe data; Admin sees authorized internal data.

## Release gates
No provider is active or public-visible until credentials, API access, terms, commercial rights, cost, safety, rate limits, webhook/polling, storage and recovery are verified. Do not deploy or activate a paid integration without explicit owner approval.
