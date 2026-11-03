# AVORLUNE Admin & Super Admin

Dokumen produk, UX, keamanan, integrasi, pembayaran, data, operasional, dan release untuk aplikasi Admin AVORLUNE.

> Repo ini adalah aplikasi frontend Admin/Super Admin yang terpisah dari repo Public `Sparkmind-obp-off/Avorlune`. Keduanya tetap satu produk dan harus terhubung melalui kontrak API resmi. Repo ini belum berisi implementasi aplikasi; dokumen ini adalah blueprint sebelum fase implementasi.

## Repositories

- Public/customer: https://github.com/Sparkmind-obp-off/Avorlune
- Admin/Super Admin: https://github.com/Sparkmind-obp-off/Admin-overlune

## Prinsip arsitektur

- Dua repo, dua frontend/deployment surface, satu backend domain/API dan satu sumber data operasional bersama.
- Admin frontend tidak boleh membaca D1 secara langsung. Semua akses melalui backend API dengan otorisasi server-side.
- Customer Clerk authentication tidak memberi akses Admin. Admin identity, session, roles, and perimeter are separate.
- Tidak ada public admin registration. Admin app hanya dapat diakses melalui private perimeter yang melindungi UI dan seluruh API admin.
- Customer payment dan admin/platform payment adalah dua domain finansial terpisah. Jangan berbagi invoice, merchant config, webhook, ledger, atau status.
- Existing customer order payment policy tetap 50% DP sebelum produksi dan 50% pelunasan sebelum final delivery.
- Semua fitur sensitif wajib audit trail, least privilege, explicit confirmation, dan idempotency.
- Production secrets, customer data, provider keys, private assets, and payment credentials must never enter the browser bundle or Git.

## Document index

| Doc | Subject |
|---|---|
| 00 | Product and architecture blueprint |
| 01 | Information architecture and navigation |
| 02 | Visual design system and screen concepts |
| 03 | Dashboard and analytics |
| 04 | Roles, permissions and governance |
| 05 | Authentication, perimeter and security |
| 06 | Public/Admin integration contract |
| 07 | Data ownership and domain model |
| 08 | Separate payment domains |
| 09 | Finance, reconciliation and reporting |
| 10 | CRM, order and production operations |
| 11 | Audit, observability and incident response |
| 12 | Acceptance criteria and test matrix |
| 13 | Roadmap and release gates |
| 14 | Decision register and open questions |

## Status

- Repository metadata verified: public repository, default branch `main`, currently empty at document creation.
- This documentation set is a design specification only. No UI, API, auth, database, payment integration, Cloudflare project, or production deployment is claimed as implemented.
- The Admin frontend must first integrate with the existing Public repository's real API contract; it must not invent a parallel source of truth.
- The exact meaning of “separate Admin payment” is intentionally isolated as an explicit decision in doc 08/14; customer checkout behavior must not be changed by assumption.

