# 14 — Decision Register & Open Questions

## Confirmed
1. Public/customer and Admin/Super Admin are separate repositories.
2. Admin repository: Sparkmind-obp-off/Admin-overlune, branch main.
3. Public repository: Sparkmind-obp-off/Avorlune.
4. Both are one AVORLUNE product connected through a controlled API contract.
5. Admin is private; customer Clerk identity is not Admin identity.
6. No public Admin registration. No in-app Admin login preference remains subject to verified private perimeter protecting UI and every privileged API.
7. Customer service payments retain 50% deposit before production and 50% before final delivery.
8. There is **no Admin/platform payment**; earlier mention was a typo. Remove Admin billing/subscription concepts.
9. AI Agent is the core Super Admin controller, with scoped tools, durable tasks, policy enforcement, evidence and human approval gates.
10. Brand layering means portfolio-level and brand-scoped operations. AVORLUNE is the only active brand in phase 1.
11. User wants all product, UX/UI, architecture, full-stack, security and agent specifications completed before the combined implementation master system prompt.

## Architecture resolution
Earlier Public docs describe two frontends within one repository. Owner's newer direction creates a separate Admin frontend repository. This changes source-code organization only; it does not authorize a second backend or operational database.

## Open decisions for implementation phase
1. Exact Admin hostname and Cloudflare Pages project.
2. Private perimeter provider/configuration and identity assertions.
3. Model provider/model and approved data handling/cost limits.
4. Whether background tasks require Cloudflare Queues based on verified account/runtime capability and cost.
5. Which external integrations the owner authorizes first, with exact scopes.
6. Whether/when to activate a second brand; none is assumed.
7. Exact T3 reversible actions, if any, to enable beyond read/prepare.

## Decision rule
Do not invent brands, integrations, paid services, permissions or autonomous side effects. Start implementation with read-only audits and evidence-based gap register. Customer Duitku checkout and 50/50 milestones remain independent and unchanged.
