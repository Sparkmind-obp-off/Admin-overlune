# 02 — Visual Design System & Screen Concepts

## Visual direction
Premium editorial operations console: clean, restrained, modern, sophisticated. Use warm-neutral canvas, high-contrast typography, deep ink navigation, subtle borders, restrained accent color, generous spacing, and compact but legible data density. Avoid a generic neon AI dashboard look.

## Layout rules
- Desktop-first operational workspace; responsive tablet/mobile for monitoring and approvals.
- Sidebar 248px expanded / 76px collapsed; topbar 64px; content max width fluid with 24–32px gutters.
- Cards use quiet surfaces, 12–16px radius, thin borders, minimal shadow.
- Typography hierarchy: page title 24–28px, section 16–18px, body 14–15px, metadata 12px.
- Status uses text + icon, not color alone. Color must meet contrast standards.
- Tables support sticky headers, server pagination, sorting, saved filters, column visibility, bulk actions only when safe.

## Screen concept A — Command Center
```text
┌────────────────────────────────────────────────────────────────────┐
│ AVORLUNE / ADMIN      Search...       PROD ●       Alerts   Profile │
├──────────────┬─────────────────────────────────────────────────────┤
│ Overview     │ Good afternoon                                     │
│ Customers    │ Operations at a glance                              │
│ Commerce     │ [Open Orders] [Awaiting Deposit] [In Production]    │
│ Production   │ [Awaiting Review] [Balance Due] [Overdue]           │
│ Finance      │                                                     │
│ Governance   │ Order flow              Revenue / Margin             │
│ System       │ [weekly trend chart]    [period summary]             │
│              │                                                     │
│              │ Needs attention                                      │
│              │ • Quote waiting approval • Failed callback          │
│              │ • Production deadline • QA review pending            │
│              │                                                     │
│              │ Recent activity                                      │
└──────────────┴─────────────────────────────────────────────────────┘
```

## Screen concept B — Customer 360
```text
Customers / AVL-XXXX-XXXX
[Customer identity + verified contact] [Tags] [Risk/consent flags]
Tabs: Overview | Projects | Quotes | Payments | Assets | Support | Timeline
Left: profile, source, consent, owner, internal notes
Right: active project, lifetime value, outstanding balance, last contact
Timeline separates customer-visible events from internal notes.
```

## Screen concept C — Order workspace
```text
Order AVL-...   Status: Production   [Actions]
Customer / Brief / Scope / Quote / Payment milestones
Production board: Queue → In progress → Internal QA → Client review
Right rail: activity log, deadlines, owner, cost/margin summary
Deliverables: versioned assets, license/provenance, approval state
```

## Screen concept D — Payment domains
```text
Finance
Tabs: Customer Order Payments | Admin/Platform Billing | Cost Ledger
Each tab has its own identifiers, filters, reconciliation state and exports.
Never combine the two payment domains into a single settlement queue.
```

## Screen concept E — Super Admin control center
```text
SUPER ADMIN / CONTROL
Security posture      Service health       Approval queue
[Perimeter status]    [API + D1 + R2]       [High-risk changes]
Identity & Roles      Payment domains      Environments
[operators + roles]   [isolated configs]    [preview/staging/prod]
Audit integrity       Release controls      Incident actions
[immutable events]    [feature gates]       [contain / revoke]
```

## Interaction principles
- Destructive and financial actions use a confirmation dialog with entity, amount, reason, and consequence.
- Show a dry-run/preview for bulk operations.
- Require reason codes for refunds, overrides, access changes, and manual reconciliation.
- Display exact timestamps in local timezone with UTC available in detail.
- Loading, empty, error, partial, and stale states are designed—not improvised.
- Charts always expose period, currency, filters, and data freshness.
