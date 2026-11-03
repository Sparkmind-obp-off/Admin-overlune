# 03 — Dashboard & Analytics

## Command Center metrics
- Active projects by lifecycle stage.
- New briefs awaiting qualification.
- Quotes sent / awaiting customer decision.
- Deposits due / received.
- Production workload and deadline risk.
- Internal QA and client review backlog.
- Final balances due.
- Delivered projects and repeat customers.
- Support tickets by priority.
- Payment callback/reconciliation exceptions.

## Financial metrics
Separate:
1. Gross customer order value.
2. Customer deposits received.
3. Customer balances received.
4. Refunds and reversals.
5. Net customer collections.
6. Production/provider costs.
7. Gross contribution and margin.
8. Admin/platform billing revenue or expense (only after its domain is defined).

Never label order value as cash received. Do not include unpaid quotes as revenue. Recognize cash and operational milestones according to explicit accounting policy; dashboard figures are operational, not statutory accounts.

## Filters
Date range, product/service type, order state, customer segment, operator, campaign/source, currency (IDR initially), and environment.

## Data quality
- Every metric has a source query, definition, timezone, and refresh timestamp.
- Use server aggregation and bounded date windows.
- Exclude synthetic/demo records from production metrics.
- Show “data unavailable” rather than substituting zero.
- Do not expose sensitive customer data in chart labels or exports.

## Alerts
Alert on overdue production, failed or duplicated callbacks, payment mismatch, asset delivery failure, suspicious login, repeated authorization denial, and integration degradation. Alerts are actionable and link to authorized detail pages.
