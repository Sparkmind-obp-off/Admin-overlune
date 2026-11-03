# 26 — Agentic Super Admin API & Data Contract

## Contract rules
All endpoints are versioned, authenticated, server-authorized, request-ID traced, schema-validated and documented in OpenAPI. Standard response: data plus requestId, or sanitized error plus requestId.

## Candidate API groups
- /api/v1/admin/session — principal and session context.
- /api/v1/admin/brands — authorized brand list and active scope metadata.
- /api/v1/admin/overview — operational aggregates.
- /api/v1/admin/agent/tasks — create/list/get/cancel.
- /api/v1/admin/agent/tasks/:id/plan — plan and dry-run.
- /api/v1/admin/agent/tasks/:id/steps — timeline and evidence.
- /api/v1/admin/agent/approvals — list/approve/deny exact scoped requests.
- /api/v1/admin/agent/tools — visible tool catalog.
- /api/v1/admin/agent/policies — read policy and propose changes.
- /api/v1/admin/audit — bounded audit query/export.
- /api/v1/admin/integrations — status, scopes and health.
These are proposals only. Inspect existing routes before creating anything.

## Candidate entities
brand, brand_domain, brand_policy_set, principal, role_grant, agent_profile, agent_policy, tool_definition, integration, integration_scope, agent_task, agent_step, approval_request, audit_event, scheduled_task, knowledge_source, evaluation_run and incident.

## Invariants
Brand-owned entities carry brand_id or provable parent relationship. Task/step/approval/audit retain actor and scope. Approval decisions are immutable. Tool schemas and policy versions are versioned. Task outputs store references, not duplicate sensitive files. Audit is append-only.

## Compatibility
Inspect current migrations first. Existing customer, project, quote, payment, payment_orders, asset and event models remain authoritative. No second operational database and no duplicate Admin payment model. Migrations are additive, tested on synthetic data and approved before production.
