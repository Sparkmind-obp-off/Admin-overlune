# 00 — Product & Architecture Blueprint

## 1. Product definition
AVORLUNE Admin is the private Agentic Super Admin Control Plane. The AI agent is the core operational controller, not a decorative chatbot. It inspects, analyzes, plans, prepares, executes authorized tools, monitors and verifies outcomes, and escalates consequential decisions to the owner.

It controls AVORLUNE operations and, when explicitly configured, an authorized brand portfolio. This is not an unrestricted autonomous superuser.

## 2. Two-repository topology
- Avorlune: public/customer application and authoritative backend/API baseline.
- Admin-overlune: separate Admin/Super Admin frontend repository and deployment.
- One authoritative backend/API and one operational data model.
- Admin frontend calls API over HTTPS. No direct D1/R2, provider or payment gateway access from browser.
- Shared contracts are versioned and tested across repos. OpenAPI/JSON schemas and generated types are preferred.

## 3. Brand layering
Portfolio → Brand → Environment → Resource. AVORLUNE is the only active brand in phase 1. Brand scope includes identity, domains, configuration, policies, integrations, permissions and data boundary. Cross-brand reads/actions require explicit grants and per-brand authorization. No additional brand may be provisioned without owner approval.

## 4. Agent architecture
Admin UI → Admin BFF/API → Agent Orchestrator → Policy Engine → Tool Gateway → authoritative domain APIs and approved provider adapters. Durable tasks, approvals, audit, retrieval, model gateway, secrets broker and evaluation support the runtime. Agent tools are typed and allowlisted; no arbitrary SQL/shell/network access.

## 5. Autonomy and control
Default T0–T2: observe, recommend, prepare. T3 reversible internal actions only when owner explicitly enables them. T4 consequential actions always require fresh, scoped human approval. T5 prohibited operations include credential extraction, bypass, uncontrolled money movement, unapproved publishing/messaging and destructive production actions. The agent cannot modify its own policy or permissions.

## 6. Domains
Identity/access; brand portfolio; customer/CRM; catalog/offers; briefs/quotes/orders; customer order payments; production/action runs; assets/licensing/delivery; support/notifications; governance/audit; observability; agent tasks/approvals/integrations. **There is no Admin/platform payment or subscription domain.**

## 7. Environment surfaces
Local, isolated preview/staging and production. Preview cannot bind production D1/R2 or live providers. Never use production customer data as test data.

## 8. Non-negotiable invariants
- Customer Clerk identity is never an Admin role.
- No public Admin registration.
- Existing Admin protection remains until a verified perimeter protects UI and every privileged API endpoint.
- Server-side authorization on every privileged request and tool.
- Customer order payment policy remains 50% deposit before production and 50% before final unwatermarked delivery.
- Customer checkout remains disabled pending LIVE authentication verification and explicit owner approval.
- Every mutation is validated, authorized, idempotent where applicable and audited.
- Human review remains required before external delivery or consequential action.
- No secret/private asset in client bundle, URL, logs or Git.

## 9. Source of truth
Inspect current Public repository and API/data implementation before implementation. Do not duplicate backend or operational records. Record mismatches in a contract gap register.
