# 33 — External Stack & Provider Requirements Register

Status: Living implementation register. This is a decision and procurement handoff, not a declaration that any provider is connected or approved.

## Purpose
During implementation, the engineering agent must identify external software, APIs, models, accounts, credentials, permissions, plans or owner actions that are genuinely required. It must report the exact dependency and wait for the owner when access, payment, data sharing or account authorization is needed.

The owner has explicitly authorized the team to recommend suitable external stacks, including LLMs, AI consoles, agent frameworks, coding agents, search/research, chat, media generation and operational software. This is authorization to **identify and request** them, not blanket authorization to create accounts, connect credentials, incur charges, expose data or activate production services.

## Decision rules
1. Audit the current code and connected tools before recommending a new provider.
2. First ask: can the requirement be met by the existing AVORLUNE stack, existing authorized connector, or a small native implementation?
3. Add an external provider only when it closes a concrete capability gap or materially improves quality, reliability, safety, time-to-delivery or total cost.
4. Prefer one provider per capability at first. Add fallback only when a measured availability or quality need justifies the added complexity.
5. Keep provider integrations behind replaceable server-side adapters. Never bind core business records or workflows to a vendor-specific schema.
6. Verify current official API documentation, availability, authentication scopes, rate limits, pricing/billing unit, region, data retention/training policy, commercial rights, support and exit path.
7. Distinguish API access from web-app subscriptions/credits. Never assume that buying a consumer plan includes API quota.
8. Never put secrets in Git, browser code, chat logs, prompts, ordinary database fields or customer-visible responses. Store only approved secret references in application data.
9. Do not connect, subscribe, pay, activate, provision, publish or send customer data until owner approval is recorded.
10. If the external dependency is optional, provide a no-provider/manual fallback and keep the feature disabled or request-only until ready.

## Provider request format — mandatory
Whenever an external dependency is needed, create/update a register entry and tell the owner using this exact structure:

- **Request ID / status:** unique ID; proposed / needs owner / approved / configured / verified / rejected / deferred.
- **Capability:** what feature is blocked or improved.
- **Provider/software:** exact product and vendor.
- **Why needed now:** evidence from code audit or acceptance requirement.
- **What it will do:** bounded role; what it will not do.
- **Integration surface:** API/SDK/MCP/OAuth/webhook/CLI; where adapter runs.
- **Required owner action:** create account, enable API, select plan, grant named scopes, provide credential through approved secret manager, approve budget, or none.
- **Estimated cost:** pricing unit, known rate and likely usage estimate; mark unknown if not verifiable. Never invent a price.
- **Data exposure:** exact categories sent, retention/training concerns and minimization plan.
- **Security/permissions:** scopes, environment, secret storage, access boundaries and revocation plan.
- **Alternatives:** existing stack/native route and at least one viable external alternative when practical.
- **Fallback:** what happens if unavailable or rejected.
- **Acceptance test:** how we prove it works.
- **Approval needed:** precise yes/no decision; no implied consent.

Do not ask for passwords, OTPs, session cookies or raw secrets in chat. Provide secure setup steps for the approved secret manager instead.

## Initial capability map (candidates, not selections)

| Capability | Candidate category/examples | Selection gate |
|---|---|---|
| LLM inference and routing | OpenAI API, xAI/Grok API, Anthropic API, Google Gemini API, OpenRouter | Compare task quality, tool calling, structured output, privacy, price and availability; select only the minimum viable route |
| Agent orchestration | Native Hono/TypeScript orchestrator first; CrewAI or LangGraph only if durable multi-agent workflows justify them | Must demonstrate measurable complexity reduction; no framework by default |
| Coding/repository assistance | Existing GitHub tools, approved coding agent or IDE agent | Repository permissions, reviewability, branch/commit controls and test evidence |
| Search/research | Existing web/search capability or a verified search API | Need freshness, citation quality, licensing and predictable cost |
| Chat/support | Native project messaging first; optional chat/support provider if realtime, inbox or SLA needs justify it | Customer data controls, exportability, identity and channel permissions |
| Image/video/audio generation | One approved provider adapter per initial capability; examples may include Runway, Luma or other verified API providers | API availability, commercial rights, output quality, pricing, moderation, async job support and private storage |
| Workflow/automation | Native durable jobs first; Make or another workflow service only for external SaaS orchestration | Idempotency, retries, observability, data access and vendor lock-in |
| Observability/error tracking | Existing platform telemetry first; optional Sentry or equivalent | PII redaction, retention, alert usefulness and cost |
| Storage/CDN | Existing Cloudflare D1/R2 architecture | Private R2 provisioning requires owner approval; do not duplicate storage without a demonstrated need |

Examples above are discovery candidates only. They are not endorsements, connected integrations, confirmed entitlements or mandatory stack choices.

## Initial requests to investigate during audit
These are questions to resolve from the actual code, not pre-approved purchases:
1. **Primary LLM route:** determine whether an existing authorized model connection is available and sufficient for Admin agent planning/tool use. If not, submit a provider request with model, API scope, budget and data handling.
2. **Agent orchestration:** begin with a small native server-side orchestrator. Evaluate CrewAI/LangGraph only if the audit finds a real need for durable multi-agent delegation, recovery or tracing that native code cannot economically satisfy.
3. **Coding agent:** inspect the current GitHub integration and available repository workflow first. Request a coding-agent product only if implementation throughput or safe test execution is materially blocked.
4. **Research/search:** use existing search tools first. Add a paid search API only if production workflows require a documented search capability unavailable in the current environment.
5. **Customer chat:** inspect existing Public project messaging. Add an external chat provider only if realtime delivery, agent inbox or omnichannel support is a required release criterion.
6. **Video provider:** keep optional/request-only. Select one provider only after the customer offer, commercial rights, API access, unit economics and owner budget are validated.
7. **Monitoring:** start with platform logs and structured audit. Add a third-party observability service only for a defined alerting/tracing gap.

## Lifecycle
discovered → documented → official docs reviewed → owner request submitted → owner approved → credential configured → read-only/test verified → production activation separately approved → active → suspended/rotated/retired.

Approval to investigate is not approval to connect. Approval to connect is not approval to incur unlimited spend. Test verification is not production activation.

## Integration architecture
The backend owns a provider-neutral registry:
- provider identity and category;
- approved capability and environment;
- connection state and verified scopes;
- opaque secret reference;
- pricing metadata with source and checked-at timestamp;
- budget/quota and per-task cap;
- adapter version and health state;
- approval/audit history.

The frontend must never receive provider credentials or private routing configuration. The Admin agent may inspect provider status and prepare configuration changes, but cannot reveal secret values, grant new scopes to itself, or activate a provider without approval.

## Implementation reporting
At every milestone, report:
- new provider requirements discovered;
- requests waiting for owner action;
- existing connections reused;
- providers configured and actually verified;
- disabled/request-only capabilities;
- spend limits and remaining risks.

A provider must never be described as integrated merely because its name appears in this register.
