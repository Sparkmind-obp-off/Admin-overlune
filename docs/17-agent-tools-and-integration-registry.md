# 17 — Agent Tools & Integration Registry

## Tool contract
Each tool declares stable ID/version, description, category, permitted roles, autonomy tier, brand/environment scope, JSON input/output schema, side-effect class, idempotency, timeout, rate limit, data classification, approval requirement, evidence requirements and owner.

## Tool classes
- Read-only: search, list, get, health, metrics, audit query.
- Prepare-only: draft quote, compose reply, preview configuration, generate change proposal.
- Reversible internal mutation: assign owner, add internal tag, update permitted metadata.
- Consequential: change offer visibility, move production state, revoke access, publish, notify, refund, change security settings.
- Prohibited: extract credentials/cookies/OTP, bypass access, delete audit history, alter own permissions, unapproved money movement, arbitrary SQL/shell/code execution or unrestricted network access.

## Initial tool domains
Platform health; brand portfolio; customer/CRM; catalog/quotes/orders; production; asset metadata/license/provenance; customer order payment status; support drafting; governance; observability; documentation search; verified external providers.

Finance tools are read-only initially and concern customer order payments and operating cost records only. There is no Admin/platform payment product or billing workflow.

## Tool Gateway
Enforce server-side authorization, schema validation, size limits, resource ownership, trusted brand context, environment allowlist, autonomy tier, approval token, idempotency and rate limits. Redact sensitive fields before model-visible output. Record actor, run, policy decision, tool version, outcome and evidence.

Never expose generic SQL, arbitrary code execution, unrestricted HTTP fetch, browser profile or shell as agent tools.

## Integration onboarding
Status: proposed → documentation_review → owner_authorized → credentials_configured → read_only_verified → production_approved → active → suspended/retired.

Record scopes, expiry, account owner, allowed operations, API availability, pricing, data policy, commercial-use rights and revocation procedure. Credentials remain in server-side secret storage and are never returned to the model.

## Initial integrations
Inspect the existing AVORLUNE API first. Cloudflare and GitHub may begin read-only. Model provider selection requires current pricing/data-policy review and owner approval. Genspark remains a human-operated handoff until supported API and current terms are verified. A connected account does not automatically mean an integration is approved or active.
