# 02 — Visual Design System & Screen Concepts

## Visual direction
Premium editorial operations control room: warm-neutral canvas, high-contrast typography, deep ink navigation, restrained accent, subtle borders, generous spacing and legible operational density. Avoid generic neon AI dashboard styling.

## Core shell
Sidebar 248px expanded / 72px collapsed; topbar 60–64px; fluid content with 24–32px gutters. Active brand and environment are always visible. Agent dock is persistent but collapsible. Right contextual panel provides evidence and selected-record context.

## Key screens
1. Command Center — brand health, open orders, production risk, customer payment exceptions, agent tasks, integration health and alerts.
2. Agent Workspace — conversation/task history, objective, structured plan, execution timeline, tool/evidence panel, risk and approval state.
3. Plan Detail — ordered steps, affected records, active brand/environment, tool versions, side effects, rollback and approval.
4. Approval Inbox — exact action, before/after diff, scope, impact, expiry, evidence and approve/deny.
5. Brand Portfolio — authorized brands and health; phase 1 shows AVORLUNE only.
6. Brand Workspace — identity, catalog, customers, operations, assets, integrations, policies and audit.
7. Customer 360 — verified profile, projects, quotes, customer payments, assets, support and timeline.
8. Order/Production Workspace — scope, milestones, production queue, QA, revisions and deliverables.
9. Finance — customer order payments, exceptions, refunds/adjustments and cost ledger. No Admin billing or subscription tab.
10. Governance — roles, agent policies, tool registry, perimeter, approvals, audit and emergency pause.
11. Integrations — verified capability, scopes, status, health, terms and revoke control.
12. Observability — API, D1/R2, model/tool health, task backlog, errors and incident timeline.

## Agent interaction language
Distinguish user instruction, concise agent rationale, proposed plan, tool execution, approval required, verified result and warning/error. Display source and freshness. Never show hidden chain-of-thought or claim a model statement is a verified fact.

## Interaction principles
Destructive and consequential actions require scoped confirmation. Bulk operations require dry-run. Show exact affected records and rollback. Status uses text + icon, not color alone. Design loading, empty, error, partial and stale states. Keyboard access, reduced motion and WCAG 2.2 AA contrast are required.

## Responsive behavior
Desktop-first operations; tablet supports monitoring and approvals; mobile prioritizes alerts, approval review and task progress. Complex bulk actions remain desktop-first.
