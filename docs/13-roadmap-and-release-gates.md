# 13 — Roadmap & Release Gates

## Phase 0 — Repository and contract audit
Inspect Public repo current routes, schemas, auth, migrations, payment, R2, tests, Cloudflare configuration and current deployment. Inspect Admin repo (this repo) and establish frontend stack only after choosing based on maintainability. Produce route-to-contract map and gap register. No production writes.

## Phase 1 — Secure shell
Build responsive shell, design tokens, routing, error/loading states, environment banner, and private perimeter integration. Keep all real data unavailable until perimeter is verified.

## Phase 2 — Operational MVP
Customer directory, Customer 360, briefs, quotes, orders/projects, production queue, assets/delivery metadata, support timeline. Integrate existing backend endpoints first; add API endpoints in Public repo only where approved.

## Phase 3 — Customer finance
Read customer order payments, payment milestones, callback exceptions, reconciliation, and cost ledger. Preserve 50/50 policy. Checkout remains gated by existing LIVE verification and owner approval.

## Phase 4 — Agent read/analyze/plan
Agent workspace, durable tasks, model gateway adapter, approved knowledge retrieval and read-only/prepare-only tool registry.

## Phase 5 — Approval and controlled execution
Policy engine, scoped approvals, idempotent Tool Gateway, task resume, audit evidence and emergency pause.

## Phase 6 — Brand portfolio readiness and integrations
AVORLUNE-only brand scope first; verified integrations and isolation tests before any additional brand is activated.

## Release gates
- G0: documentation and repository/API audit complete.
- G1: local synthetic-data shell and contract tests.
- G2: staging with isolated data and perimeter allow/deny verified.
- G3: production read-only pilot; no financial mutation.
- G4: approved operational mutations with audited rollback and support.
- G5: payment write actions only after LIVE verification, explicit owner approval, and controlled test plan.

No deployment, live payment, paid resource activation, destructive migration, or real customer communication without required approval.
