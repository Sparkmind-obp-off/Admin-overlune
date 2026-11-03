# 15 — Agentic Super Admin Product Charter

## Product definition
The Admin application is AVORLUNE's private Agentic Super Admin Control Plane. Its primary operator is an AI agent with scoped tools, durable task state, observability, and human approval gates. It is not merely a CRUD dashboard with a chat box.

The agent operates AVORLUNE and its authorized brand portfolio. It can inspect, explain, plan, prepare, execute permitted reversible operations, monitor outcomes, and escalate decisions. It must never exceed the active human's authority or its policy envelope.

## Mission
1. Maintain a reliable view of authorized brands and shared platform services.
2. Convert natural-language objectives into inspectable, bounded tasks.
3. Operate customer, catalog, creative-production, action-service, CRM and support workflows through typed tools.
4. Detect anomalies, summarize risks and recommend corrections.
5. Coordinate multi-step work with durable state, evidence, retries and audit logs.
6. Keep consequential decisions under human control.

## Brand layering
A brand is a governed operating scope, not merely a visual theme. Each brand has an immutable ID, identity, domains, configuration, capabilities, integrations, policies, data scope and audit boundary. AVORLUNE is the only active production brand in phase 1. The architecture is portfolio-ready but must not invent or provision other brands.

The owner can use a portfolio overview or enter a specific brand workspace. Cross-brand actions must enumerate target brand IDs and pass authorization independently for every target.

## Agent capabilities
Read, analyze, plan, prepare, execute permitted tools, monitor, verify and escalate. Every action is traceable to a task and evidence.

## Autonomy tiers
- T0 Observe: read-only inspection.
- T1 Recommend: analysis and recommendations.
- T2 Prepare: drafts, plans and dry-runs; no external side effects.
- T3 Execute reversible low-risk internal actions only when explicitly enabled.
- T4 Consequential actions only after fresh, scoped human approval.
- T5 Prohibited: credential extraction, security bypass, uncontrolled financial actions, unapproved publishing/messaging, destructive production operations, policy override or self-granted privileges.

Default autonomy is T0–T2. T3 requires explicit owner configuration. T4 always requires human approval.

## Non-goals
No unrestricted autonomous superuser, no self-modifying permissions, no public agent console, no public admin registration, no third-party seller marketplace in phase 1, and no assumption that a provider offers a supported API or commercial rights.

## Success measures
Task completion with evidence; safe-action rate; approval correctness; time-to-detect/resolve; tool error rate; correct policy denials; operator trust; cross-brand isolation pass rate; cost per completed task. Never optimize completion by weakening controls.
