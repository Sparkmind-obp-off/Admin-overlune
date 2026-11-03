# 20 — Agentic Admin Information Architecture

## Global shell
Navigation: Command Center, Agent Workspace, Brands, Customers, Commerce, Production, Assets, Finance, Support, Integrations, Governance, Observability, Documentation.

Top bar: active brand, environment badge, global search/command palette, notifications, task activity and operator profile. Persistent agent dock supports ask, inspect scope, create task and view plan/approval. Context panel shows selected record, evidence and related tasks.

## Agent Workspace
Tabs: Conversation, Plan, Runs, Approvals, Scheduled Tasks, Knowledge. Chat is a task interface, not a privileged shell. Every action creates a durable task. Plan view shows step graph, tools, risk, status, evidence and approval. Runs show timeline, logs and safe retry/cancel controls.

## Command Center
Brand health, orders/projects requiring attention, production SLA risk, customer/support queue, customer payment exceptions, integration/API health, agent runs and security/approval alerts.

## Brand workspace
Overview, identity, domains, catalog, customer operations, assets, integrations, policy and audit. Phase 1 contains AVORLUNE only.

## Governance
Human principals, role grants, agent policies, tool registry, approval history, perimeter health, secret metadata (never values), retention, audit export and emergency pause.

## Navigation rules
Active brand remains visible. Portfolio context is read-only for aggregates unless an explicit cross-brand action is authorized. Deep links re-check access and scope. Unavailable capabilities show honest disabled states, never fake data.
