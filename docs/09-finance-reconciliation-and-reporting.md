# 09 — Finance, Reconciliation & Reporting

## Finance workspace
- Customer Order Payments: deposit, balance, callback, gateway verification, manual payment evidence, reconciliation, refunds.
- Cost Ledger: AI/provider usage, production labor, stock/licensing, delivery, and other project costs.
- Margin report: collected customer cash and allocated costs, with clear distinction from quoted/projected revenue.
- Platform Billing: separate disabled domain until doc 08 decisions are confirmed.

## Customer payment lifecycle
Pending → gateway initiated → callback received → server verification → settled / failed / expired / mismatch / under review. Use exact provider states mapped to canonical internal states. Never accept browser redirect as authoritative.

## Reconciliation
- Compare local order, amount, currency, merchant reference, provider reference, callback signature, and server-side status.
- Duplicate callbacks are idempotent.
- Mismatch enters manual review; never auto-mark paid.
- Manual confirmation requires evidence reference, reason, operator, timestamp, and approval policy.
- Refunds are separate compensating transactions with reason, amount, approver, and provider result. Do not imply refund automation exists unless verified.

## Reports
Daily/weekly/monthly collections, deposit-to-balance conversion, overdue balances, refunds, payment exceptions, cost by order, margin by offer, and provider spend. Each report defines gross/net, date basis, timezone, currency, and exclusions.

## Exports
Bounded, permission-gated, audited, redacted by default. Export should be generated server-side and expire. Never expose private asset or payment secrets.
