# 22 — Screen-by-Screen UX Specification

## Command Center
KPI row: open orders, production in progress, reviews due, customer payment exceptions, SLA risk and agent tasks needing attention. Panels: workflow funnel, attention queue, activity feed and integration health. Every metric links to filtered records and displays freshness.

## Agent Workspace
Task history on left; objective, plan and step timeline in center; scope, tools, evidence, risk and approval on right. Composer shows active brand/environment. Plan-only is default. Execution is enabled only after policy preflight and approval.

## Plan detail
Goal, assumptions, target records, brand scope, environment, ordered steps, tool versions, side effects, risk, known/unknown duration or cost, rollback and approvals.

## Approval Inbox
Group by risk and expiry. Detail shows exact action, diff, resources, evidence, actor, brand, environment, side effects and rollback. Approval may require re-authentication.

## Brand Portfolio
Authorized brand cards with health, open work, agent state and domains. Phase 1 shows AVORLUNE only. Add-brand remains unavailable until explicit owner authorization and setup.

## Brand Workspace
Identity, domains, catalog, customers, operations, assets, integrations, policies and audit.

## Customer 360
Verified identity attributes, consent, projects/orders, quotes, customer order payments, assets, support and timeline. Internal notes are visually separate from customer-visible communication.

## Commerce & Production
Catalog/offer versioning, brief/quote/order lifecycle, production board, QA, revisions and delivery readiness. Enforce existing 50% deposit before production and 50% balance before final delivery through the authoritative backend.

## Finance
Customer Order Payments, customer exceptions, refund/adjustment workflow and cost ledger. There is no Admin/platform payment product, billing tab or subscription placeholder.

## Integrations
Connection state, capability, permission scopes, last verification, health, terms review, owner and revoke control. Never show secret values.

## Governance & Security
Human identities, grants, agent policy, tool registry, perimeter, approvals, audit, retention and emergency stop.

## Observability
API latency/errors, database/storage health, model/tool health, task backlog, failures, usage/cost where available and incident timeline.

## Documentation & Knowledge
Search approved specs/runbooks, show source/version, mark stale docs and let agent cite evidence.

## Global states
Every screen defines loading, empty, denied, stale, partial, error, offline and success states. Tables paginate and bound filters. Destructive actions require confirmation.
