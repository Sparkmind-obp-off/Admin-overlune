# 08 — Separate Payment Domains

## Purpose
The phrase “payment Admin terpisah” requires its own explicit domain. It must not be interpreted as a change to customer checkout.

## Domain A — Customer order payments (already defined)
- Customer pays AVORLUNE for a quoted creative service/order.
- Current policy: 50% deposit after quote acceptance and before production; 50% balance after preview/revisions and before final unwatermarked delivery.
- Duitku POP is the planned/implemented gateway baseline in the Public repository; production checkout remains disabled pending LIVE authentication verification and explicit approval.
- Payment is tied to an order/project, quote version, milestone, amount, currency, and verified gateway transaction.
- Signed callback plus server-to-server verification; idempotent settlement; browser redirect is not proof of payment.
- This domain is not an admin subscription or admin-access fee.

## Domain B — Admin/platform payments (separate, not yet defined)
Potential meanings are materially different and must not be merged:
1. Admin pays a platform/vendor subscription or infrastructure invoice.
2. Admin users pay AVORLUNE for access to an Admin/Super Admin product.
3. AVORLUNE records operating expenses, vendor bills, or reimbursements.
4. A separate internal finance/payment method is intended for owner/admin transactions.

No option is selected by this document. Do not implement a checkout, recurring billing, subscription gate, or payment provider for Domain B until owner confirms the payer, payee, purpose, pricing model, currency, provider, and legal entity.

## Hard separation requirements
If Domain B is activated:
- Separate tables/entities and ID namespace.
- Separate merchant/provider account and credentials where the business relationship requires it.
- Separate callback URL, signature verification, idempotency namespace, and reconciliation process.
- Separate ledger, reports, access permissions, refunds, tax/accounting treatment, and retention.
- No reusing customer order invoice IDs, payment status, quote IDs, or webhook handler.
- Explicit environment separation; never test with live funds without approval.
- No customer order may become paid because an Admin/platform payment succeeded, and vice versa.

## Admin UI treatment
Show two clearly separated tabs:
- Customer Order Payments — operational collection for customer orders.
- Admin / Platform Billing — disabled/“Not configured” until Domain B is defined and implemented.

Never show fake payment rows or imply a gateway is connected when it is not.

## Approval checklist before implementation
Confirm payer, payee, purpose, payment direction, one-time vs recurring, amount/pricing, currency, provider, merchant entity, invoice ownership, refunds/cancellations, tax/legal handling, who can initiate/approve/reconcile, and whether this payment changes Admin access.
