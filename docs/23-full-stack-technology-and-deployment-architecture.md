# 23 — Full-Stack Technology & Deployment Architecture

## Guiding decision
Preserve the current Cloudflare-first AVORLUNE baseline. Do not add a second database, backend of record or costly orchestration platform before demonstrated need. Validate all library/runtime choices against current official docs during implementation.

## Admin frontend
React + TypeScript + Vite to match Public. Use the existing router if suitable; otherwise choose a maintained router. TanStack Query for server state, React Hook Form + Zod for forms/schema validation, accessible primitives and project-owned design tokens. Avoid unnecessary framework lock-in.

## Admin BFF and domain API
Hono + TypeScript, reusing authoritative API/domain logic. Admin frontend calls same-origin BFF or versioned API over HTTPS. BFF may adapt responses but cannot become a second business-logic owner. OpenAPI 3.1 and Zod schemas define contracts.

## Agent orchestration
Start as a modular TypeScript service alongside existing backend. Persist tasks in D1. Use Cloudflare Queues/Workers only if runtime/account availability and cost are verified and owner approves. Otherwise use bounded request-driven tasks with durable resume; never pretend background execution exists. Tool Gateway and Policy Engine are server-side allowlisted modules.

## Data and storage
D1 remains authoritative. R2 remains private object storage; activation is owner-approval gated. KV may cache short-lived non-critical state, never critical tasks, approvals or audit. Use additive migrations and tested rollback.

## Identity and security
Keep existing first-party Admin session until private perimeter migration is verified. Cloudflare Access or equivalent may be evaluated; protect UI and privileged API independently and verify signed identity assertions server-side. Clerk is customer-only. No public Admin registration. No secret in VITE variables or browser bundle.

## Observability and tests
Structured logs include request, trace, actor, agent run, tool and brand IDs; redact PII/secrets. OpenTelemetry-compatible tracing where runtime supports it. Vitest and existing test conventions; isolated D1 integration tests; Playwright for critical journeys if feasible. CI policy must respect owner's deployment constraints.

## Deployment
Separate Cloudflare Pages project for Admin. Existing API remains authoritative; extracting it to a dedicated Worker is a deliberate migration only. Local, isolated preview/staging and production must be separate. Preview cannot bind production D1/R2 or live providers. Admin domain is not assumed configured.

## Non-decisions
No Supabase/Firebase/Neon replacement, second D1, paid vector DB, autonomous browser agent, paid queue/model/monitoring product or microservice split without evidence and owner approval.
