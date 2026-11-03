# 07 — Data Ownership & Domain Model

## One authoritative operational data source
Public/customer and Admin views must operate on the same canonical customer, offer, quote, order/project, payment, asset, and event records through the backend API. Do not create a second customer table or duplicate operational ledger in the Admin frontend repository.

## Domain entities
- Customer and customer identity link.
- Catalog item, offer, offer version.
- Brief and brief attachment reference.
- Quote, quote line, scope revision.
- Order/project and lifecycle event.
- Customer payment order, callback, allocation, refund record.
- Production job and action run.
- Asset, version, provenance/license, delivery grant.
- Support ticket and communication event.
- Admin principal, role, permission grant, session.
- Audit event and approval record.
- Platform billing account/invoice/payment only if the owner confirms this separate domain.

## Ownership rules
- Customer owns customer-visible profile and brief data, subject to policy.
- AVORLUNE owns internal operational records, pricing logic, production notes, cost data, staff notes, and audit logs.
- Customer-facing timeline is a filtered projection; never expose internal notes.
- Asset metadata and delivery rights are authoritative on backend; R2 object keys are never exposed.
- Payment records are immutable financial facts; corrections are compensating records, not silent edits.
- Audit log is append-only by application policy; privileged deletion is prohibited.

## Data separation
Use explicit tenant/workspace scope only if multi-tenant product operation is introduced. Do not invent multi-tenant complexity for a single-provider initial marketplace. Enforce customer object ownership on every customer API and staff permission on every admin API.

## Migration
All schema changes are additive where possible. Back up and verify production D1 before migrations. Never drop, truncate, reset, or recreate production D1 to simplify development. Use synthetic local/staging fixtures and tested rollback/forward recovery.
