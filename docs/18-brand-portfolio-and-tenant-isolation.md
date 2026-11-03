# 18 — Brand Portfolio & Tenant Isolation

## Scope model
Portfolio → Brand → Environment → Resource → Record. Principals and agents receive explicit grants at each level. AVORLUNE is the only active brand in initial release; additional brands are not created automatically.

## Brand entity
Minimum fields: brand_id, slug, display_name, status, domains, theme_config, locale, timezone, currency, policy_set_id, integration_set_id, data_partition_key, timestamps. Legal identity documents and secrets do not belong in ordinary brand configuration.

## Isolation rules
- Every brand-owned record has brand_id or an enforceable relationship to a brand-owned parent.
- Every query and mutation is scoped server-side.
- Portfolio analytics require explicit permission and minimum-data aggregation.
- Cross-brand actions enumerate targets and pass authorization per brand.
- Brand switching clears stale client caches and revalidates grants.
- Settings, credentials, assets, customers and logs cannot leak across brands.
- Shared platform services are explicitly global and separately permissioned.

## UX
Portfolio overview is read-only for aggregates by default. Brand workspace is one selected brand. Global control covers shared infrastructure, security and model/tool policy. Active scope remains visible; mutations cannot run in ambiguous "all brands" context.

## Phased strategy
Phase 1: AVORLUNE only with brand_id groundwork.
Phase 2: add another brand only after owner approval, isolation tests, domain mapping and policy setup.
Phase 3: portfolio automation and cross-brand analytics with explicit grants.

## Migration
Do not retrofit brand_id into production blindly. Inspect schema, propose additive migration, backfill AVORLUNE in an isolated copy, verify relationships and query scope, then seek approval for production migration. Preserve legacy IDs.
