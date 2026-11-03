# 31 — Unified Architecture Decision & Lean External Stack Policy

Status: Owner-approved direction for the next implementation phase. This document is the current tie-breaker wherever earlier documents disagree. It supersedes conflicting assumptions in docs 00–30 but does not silently erase their useful requirements.

## 1. Product outcome
AVORLUNE is one AI-assisted creative production business with two connected operating surfaces:
- Public AVORLUNE: customer discovery, service catalogue, brief intake, quote/order, payment milestones, project workspace, customer chat/status, previews, revisions and delivery.
- Admin/Super Admin AVORLUNE: private owner/operator console and agentic control plane for portfolio operations, customer/order/production oversight, integrations, capability configuration, policy, approvals, audit and analytics.

The two surfaces must feel like one product operationally, while remaining separate trust zones.

## 2. Repository and runtime boundary
Canonical repositories:
- Customer/public application and current backend baseline: https://github.com/Sparkmind-obp-off/Avorlune
- Private Admin/Super Admin application and agent control plane: https://github.com/Sparkmind-obp-off/Admin-overlune

Canonical runtime rule:
- Exactly two frontend applications/deployments: Public and Admin.
- Exactly one authoritative business API and one authoritative operational data source for AVORLUNE.
- The Public repository currently contains the production backend baseline. Preserve and evolve it after a code audit; do not create a second database or competing API in the Admin repository.
- Admin is a separate frontend repository and calls the authoritative API over authenticated HTTPS.
- Backend/API may later be extracted into a dedicated Cloudflare Worker/API deployment only when the migration is justified, tested and backward-compatible. Extraction is not a prerequisite to integration.
- Both frontends must never access D1, R2, provider credentials or internal queues directly.
- Admin frontend may have its own static deployment and private perimeter; this is not a second business backend.

Conflict resolution: older Public documentation may describe an Admin frontend living inside the Public repository. The separate Admin-overlune repository is now the designated Admin frontend source of truth. Existing /admin paths in Public must be treated as legacy/migration surface; inspect and preserve safe operational functionality until migration is tested. Do not run two competing Admin implementations in production.

## 3. Shared control plane
The authoritative backend owns:
- Customer, project, quote, order, payment, production and delivery records.
- Capability registry and versioned customer-safe published catalogue.
- Provider registry and server-side secret references.
- Agent tasks, tool execution records, approval requests and audit events.
- Durable generation jobs and private asset metadata.
- Brand, policy, budget, quota and rollout configuration.

Admin drafts and approves configuration through privileged API routes. Public receives only a sanitized, versioned published capability projection. Customer requests are revalidated server-side against the current version before any work or spend occurs.

## 4. Agentic operating model
The Super Admin agent is an operator, not a decorative chat bot. It can observe authorized business data, explain anomalies, answer operational questions, plan and prepare changes, execute only typed registered policy-checked tools, verify results and record evidence, monitor asynchronous work and escalate decisions.

Default mode is read → analyze → propose → prepare. Low-risk reversible actions may be enabled by explicit policy. Money, customer-visible commitments, provider activation, paid model usage, external publishing/messages, security changes, destructive actions and production releases require fresh scoped human approval. No agent can grant itself permissions or approve its own consequential action.

## 5. Lean stack principle
Build only the durable core. Prefer the current Cloudflare-first stack already in the Public repository (TypeScript, React/Vite, Hono/Pages Functions, D1, private R2 when approved). Reuse existing components and dependencies where sound.

External services are optional adapters, not architectural foundations:
- LLM/model providers: choose by task, quality, latency, data policy, availability and total cost.
- Agent orchestration frameworks (e.g. CrewAI or alternatives): evaluate only if they materially simplify durable multi-agent workflows; do not add a framework just for branding.
- Research/search, code intelligence, observability, email, chat, media/video/image generation and scheduling providers: add only for a concrete approved use case.
- Provider/model routing must be provider-neutral and replaceable. Keep policy, identity, business logic, state and audit inside AVORLUNE's backend.
- Avoid multiple overlapping agent frameworks, redundant databases, unnecessary vector stores, duplicated queues, premature microservices and paid services without a measured need.

Before recommending a provider, compare native implementation, existing connected tools and at least one viable alternative. State the exact capability gap, official API/docs, auth/scope, pricing/billing unit, data retention/training terms, commercial rights, limits, region, failure mode, lock-in and exit path. Verify with current official documentation. Report recommendation and ask owner approval before connecting accounts, storing credentials or incurring cost.

## 6. Chat and agent UX
Public chat is customer support/project conversation scoped to the customer's own project. It must not expose internal agent tools or provider routing. Agentic chat belongs in Admin, with explicit context (brand, project, task), cited records, proposed actions, approval previews and execution receipts. Chat is an interface to workflows, not the workflow state store. Persist durable tasks and messages server-side; do not rely on browser memory.

## 7. Video and creative production
Image/video/audio are capability modules, not mandatory dependencies. Keep them hidden/request-only until a provider route is verified and owner-approved. Start with human-assisted production if that creates customer value sooner. For automation, use a normalized async job contract, idempotency, bounded retries, budget caps, provider status normalization, private storage, QA and customer-safe delivery.

## 8. Security and commercial invariants
- Admin identity and customer identity are separate. Customer Clerk JWT is never Admin authorization.
- Private Admin perimeter must protect both UI and every privileged API request.
- Secrets are stored only in approved server-side secret storage; database stores opaque references only.
- Tenant/brand/customer authorization is enforced server-side on every request.
- No arbitrary SQL, shell, unrestricted network, credential export or self-modifying permissions through agent tools.
- Customer service payment remains 50% deposit before production and 50% balance before final delivery.
- No Admin/platform billing, subscription or payment domain.
- Duitku customer checkout remains disabled pending LIVE auth verification and explicit owner approval.
- Private R2 activation and paid external provider usage require owner approval.
- No production deploy, destructive migration or high-risk action without approval.

## 9. Implementation sequence
1. Read-only audit of both repositories, Cloudflare resources, current API, D1 schema, secrets bindings (names only), routes, auth, tests and deployment status.
2. Produce an implementation gap matrix; reconcile code against docs and this decision.
3. Stabilize shared API contract and Admin perimeter.
4. Build Admin frontend and API integration against existing backend.
5. Add agent runtime, policy engine, typed Tool Gateway, durable tasks, approvals and audit.
6. Add provider registry and one low-risk read-only provider integration only if justified.
7. Add customer-facing chat/production workflows where validated.
8. Add one video adapter only after cost, rights, API and owner approval.
9. Test cross-surface authorization, tenant isolation, failure recovery, idempotency and cost controls.
10. Release in stages; no automatic production deploy.

## 10. Definition of done
A customer can use Public and see only their own projects. An authorized operator can use Admin to inspect the same authoritative records. The agent can propose and safely execute authorized tasks; consequential actions require approval; every action is auditable. Public capability availability changes only through an approved backend publication. External providers can be swapped without changing core business records. No duplicate backend/database or uncontrolled spend exists.
