# 04 — Roles, Permissions & Governance

## Role model
- **Super Admin / Owner:** global governance, role assignment, environment/security controls, agent policy/tool governance, emergency access revocation.
- **Admin / Operations Lead:** customer/order/quote/production operations; limited finance visibility.
- **Creative Operator:** assigned production jobs, assets, QA submissions; no customer payment mutation.
- **Finance Operator:** customer payment reconciliation and approved finance records; no provider secret access.
- **Support Operator:** customer/support timeline and permitted communications; no finance or production destructive actions.
- **Read-only Auditor:** approved read-only operational and audit access.

Initial deployment may be single-owner, but design permissions as capability-based from day one. Do not assume multi-staff is already enabled.

## Permission naming
Examples: `customers.read`, `customers.update`, `quotes.create`, `orders.transition`, `production.assign`, `assets.upload`, `assets.revoke`, `customer_payments.reconcile`, `agent.tasks.read`, `agent.tasks.plan`, `agent.tools.invoke`, `agent.approvals.review`, `agent.policies.propose`, `brands.read`, `team.roles.manage`, `security.sessions.revoke`, `audit.read`, `settings.integrations.manage`.

## Governance rules
- Deny by default; least privilege.
- Server-side checks on every route and object.
- High-risk permissions require step-up authentication and reason.
- Super Admin actions affecting another administrator require dual control where feasible.
- No role escalation through customer profile fields or Clerk metadata.
- Never allow an operator to approve their own high-risk change where a second approver is configured.
- Record actor, target, action, reason, request ID, before/after safe diff, timestamp, and approval references.
- Permission changes take effect promptly; sessions/tokens are revoked when role or account is disabled.

## Sensitive actions
Require explicit confirmation and audit: role changes, account disablement, credential rotation, payment reconciliation override, refund initiation, webhook configuration, secret reference changes, asset revocation, data export, environment promotion, and feature flag changes affecting production.


## AI agent principal
The agent has a distinct non-human principal and never inherits the owner's full permissions. Every tool call is checked against human grant, agent policy, brand, environment, resource and autonomy tier. The agent cannot approve its own request, grant itself permissions, edit its policy or disable audit/emergency controls. Default authority is read/recommend/prepare; consequential actions require fresh human approval.
