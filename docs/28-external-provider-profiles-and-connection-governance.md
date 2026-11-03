# 28 — External Provider Profiles & Connection Governance

## Purpose
AVORLUNE may connect external AI, media, storage, analytics and operational providers. An external provider profile represents a verified provider account/workspace and its capabilities; it is not a user profile and not a public social profile.

## Provider profile fields
provider_id, display_name, category, official_site, official_api_docs, account/workspace reference (opaque), connection_state, credential_reference, verified_scopes, available_capabilities, region, data_processing_notes, retention/training policy, commercial-use/license notes, rate limits, pricing source/date, last_verified_at, owner, environment allowlist and status.

Never store API keys, OAuth refresh tokens or secrets in these profile records. Store only a secret-manager reference. Secret values are server-side only and never visible to the browser, agent context, logs or Git.

## Connection lifecycle
discovered → documentation_review → owner_authorized → credentials_configured → read_only_verified → sandbox_or_dry_run_verified → production_approved → active → suspended/rotating/retired.

A search result is not proof of API access. A web-app subscription is not proof that API access or credits are included. Verify account type, developer API availability, terms, data handling, pricing and commercial-use rights before enabling.

## External profile UX
Admin > Integrations > Provider Profiles:
- Provider catalogue and category filters.
- Provider detail with official docs, capabilities, supported operations, limitations and current verification date.
- Connection state, environment and scope.
- Usage, quota and cost visibility when the provider exposes it.
- Credential status as connected/not connected only; never reveal secret.
- Test connection/read-only verification, suspend, rotate and revoke controls.
- Approval and audit history.

Public AVORLUNE must never expose provider keys or require customers to connect a provider account unless that is an explicit product decision. Public users interact with AVORLUNE's own generation workflow.

## Initial provider candidates
- Runway Dev: current official API documents video/image/audio model access, recipes and model routing. API credentials and API billing are distinct from Runway web-app credits. Candidate for a future adapter, not yet connected.
- Luma Agents: current official API documents asynchronous image/video generation jobs and output retrieval. Candidate only; not connected.
- Other providers may be added after official API and commercial terms are verified.

## Policy
Do not scrape private accounts, collect passwords/cookies/OTP, or automate consumer web UIs as a substitute for an unsupported API. If no supported API exists, provide a manual handoff. Provider connection and paid usage require explicit owner approval.
