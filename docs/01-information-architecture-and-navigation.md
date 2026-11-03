# 01 — Information Architecture & Navigation

## Global shell
- Left navigation rail/sidebar with workspace switcher (only if multiple legal entities/workspaces are later approved).
- Top bar: page title, global search, environment indicator, notifications, current operator, session controls.
- Main content: breadcrumbs, page actions, filter row, primary content, contextual detail panel.
- Persistent warning treatment for staging vs production. Production actions require stronger confirmation.

## Primary navigation
1. **Overview**
   - Command Center
   - KPI & Reports
2. **Customers**
   - Customer Directory
   - Customer 360
   - Support Inbox
3. **Commerce**
   - Catalog
   - Offers & Versions
   - Briefs & Quotes
   - Orders & Projects
   - Customer Payments
   - Digital Products
4. **Production**
   - Work Queue
   - Production Runs
   - Action Runs
   - Review & QA
   - Assets & Delivery
5. **Finance**
   - Customer Payment Reconciliation
   - Admin/Platform Billing (feature-flagged until definition confirmed)
   - Cost Ledger
   - Revenue & Margin Reports
6. **Governance**
   - Team & Roles
   - Audit Log
   - Integrations & Providers
   - Policies & Approvals
7. **System**
   - Settings
   - API/Service Health
   - Feature Flags
   - Environment & Release Status

## Super Admin-only areas
- Global control center
- Admin identity and role governance
- Private perimeter/security posture
- Payment domain configuration (metadata/status only; secrets managed outside UI)
- Audit integrity and incident controls
- Environment and release governance
- High-risk approval queue

## Navigation behavior
- Hide inaccessible navigation items, but enforce authorization again on the server.
- Deep links must not bypass authorization.
- Preserve filters and pagination in URL only when values are non-sensitive.
- Never put customer brief contents, access tokens, payment secrets, or private asset URLs in query strings.
- Empty states must explain the next valid action and must not fabricate records.
