# 08 — Payment Scope (Admin Payment Removed)

## Owner clarification
There is **no separate Admin payment**. The earlier reference to an Admin/platform payment was a typo. Do not implement or display Admin subscriptions, Admin access fees, Admin billing, a second payment provider, or a separate Admin payment ledger.

## Customer order payments only
- Customer pays AVORLUNE for a quoted creative service/order.
- Current business policy: 50% deposit after quote acceptance and before production; 50% balance after preview/revisions and before final unwatermarked delivery.
- Duitku POP is the existing/planned customer gateway baseline in the Public repository. Production checkout remains OFF pending LIVE authentication verification and explicit owner approval.
- Payment ties to order/project, quote version, milestone, amount, currency and verified gateway transaction.
- Signed callback plus server-to-server verification; idempotent settlement; browser redirect is not proof of payment.

## Admin UI treatment
Finance screens show customer order payments, customer payment exceptions, approved refund/adjustment workflows and operating cost visibility where supported by the existing data model. Do not show an Admin/platform billing tab or placeholder.

## Safety
Do not change customer checkout, payment milestones, merchant credentials, callback handling or existing payment records as part of this documentation update. Do not initiate invoices, charges, refunds or live tests without explicit approval. Preserve all existing LIVE-only constraints and checkout-off status until its verification gate passes.
