# 14 — Decision Register & Open Questions

## Confirmed
1. Public/customer and Admin/Super Admin are separate GitHub repositories.
2. Admin repository: `Sparkmind-obp-off/Admin-overlune`, default branch `main`.
3. Public repository: `Sparkmind-obp-off/Avorlune`.
4. Both are one AVORLUNE product and must connect through a controlled API contract.
5. Admin is private; customer Clerk identity is not admin identity.
6. Existing preference is no in-app admin login screen; a verified perimeter must protect UI and every privileged API.
7. Customer service payments retain 50% deposit before production and 50% before final delivery.
8. User asked for Admin/Super Admin documentation first; combined implementation master prompt comes later.

## New architecture resolution
Earlier docs in Public repo describe two frontends within one repository. The new owner-provided repository split supersedes only the source-code repository arrangement: the Admin frontend now has its own repo. It does not authorize a second backend or a second operational database. Preserve one authoritative API/data domain unless a later explicit decision changes it.

## Open decisions — do not guess
1. What exactly is the separate Admin payment?
   - A. Admin/operator pays a software/platform subscription.
   - B. AVORLUNE charges third-party Admin users for access.
   - C. AVORLUNE records its own vendor bills/operating expenses.
   - D. A distinct internal payment method/account for owner operations.
2. Who is payer and who is payee for Domain B?
3. Is it one-time, recurring, invoice-based, or expense recording only?
4. Does payment affect Admin access or role eligibility?
5. Which provider, legal merchant entity, currency, and tax treatment apply?
6. What exact custom domain is intended for Admin? Suggested placeholder only: `admin.avorlune.com`; not configured or approved.
7. What perimeter provider/identity source is already configured, if any?
8. Does the owner want a separate Super Admin-only hostname, or one Admin hostname with role-gated sections?

## Decision rule
Until answered, Domain B remains a disabled placeholder. Do not change customer Duitku checkout, 50/50 milestones, or customer order records. Do not implement subscription enforcement or create invoices for Admin access.
