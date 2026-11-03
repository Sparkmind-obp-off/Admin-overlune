# 27 — Agentic Super Admin Roadmap & Acceptance

## Phase 0 — Discovery
Inspect both repositories, branches, routes, schema, migrations, bindings, identity, secret names, integrations and tests. Create evidence-based gap register. No production writes.

## Phase 1 — Secure Admin shell
Separate frontend, verified private perimeter/session, role context, AVORLUNE scope, navigation, design tokens, API client and honest states. Keep existing protection until replacement passes tests.

Acceptance: public user denied UI and privileged API; authorized owner allowed; Clerk customer token cannot grant Admin access; preview cannot reach production data.

## Phase 2 — Operational control plane
Command Center, customer 360, catalog/quotes/orders, production queue, customer payment visibility, support, audit and system health through authoritative API.

Acceptance: all data comes from source of truth; pagination, filters, scope and audit tests pass; no duplicate store.

## Phase 3 — Agent read/analyze/plan
Agent workspace, model gateway adapter, tool registry, approved-doc retrieval, durable tasks and structured plans. Read-only/prepare-only tools.

Acceptance: golden scenarios 1–4 pass; claims have evidence; no direct DB or arbitrary tool access.

## Phase 4 — Approval and controlled execution
Policy engine, approval inbox, idempotent tool gateway, task resume, kill switch and reversible internal actions.

Acceptance: exact approval, expiry, replay and mutation tests pass; emergency stop blocks side effects; results independently verified.

## Phase 5 — Brand readiness
Brand scope groundwork and AVORLUNE migration plan. No second brand activation without owner approval.

Acceptance: all brand-owned queries scoped; cross-brand access denied by default; active brand always visible.

## Phase 6 — Integrations and monitoring
Enable verified integrations one at a time with scopes, terms and owner approval. Scheduled health checks and proactive alerts only; no autonomous consequential action.

## Phase 7 — Production readiness
Threat model, privacy/legal review, restore drill, performance, accessibility, agent evaluations, operator training, release and rollback evidence.

## Release rules
No production deploy, paid provider, R2 activation, live payment, migration, external message/publish, refund, destructive operation or legal acceptance without explicit approval. A push to main is not deployment approval.

## Completion report
Exact files, commit SHA, tests/results, evidence, gaps, production impact, approvals and deployment status. Distinguish docs from implementation.
