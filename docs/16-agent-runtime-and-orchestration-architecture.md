# 16 — Agent Runtime & Orchestration Architecture

## Logical architecture
Admin Web UI → Admin BFF/API → Agent Orchestrator → Policy Engine → Tool Gateway → authoritative domain APIs and approved provider adapters.

Supporting modules: durable task store, conversation/session store, approval queue, append-only audit log, scheduler/worker, retrieval layer, model gateway, secrets broker, telemetry and evaluation harness.

The Admin frontend never calls model providers, D1, R2 or privileged third-party APIs directly. The agent never receives raw database credentials or unrestricted network access.

## Execution lifecycle
1. Receive intent with actor identity, active brand, environment and request ID.
2. Resolve intent into a typed task; clarify missing critical parameters.
3. Retrieve only relevant authorized context.
4. Build a plan with steps, tools, inputs, impact, dependencies, risk and rollback.
5. Run policy preflight against actor, agent, brand, environment, resource and action.
6. Present plan/dry-run where required.
7. Obtain fresh scoped approval for consequential operations.
8. Execute through schema-validated Tool Gateway with idempotency and bounded timeouts.
9. Persist step outputs, evidence references, errors and state transitions.
10. Verify postconditions independently.
11. Summarize result, residual risk and next step.

## Durable task state
States: received → clarifying → planned → awaiting_approval → queued → running → waiting_external → verifying → completed | partially_completed | failed | cancelled | expired.

Each step records task, sequence, tool/version, schema version, redacted input, output reference, status, timestamps, retry count, error code, idempotency key, approval and evidence. State transitions are server-enforced. Resume must not duplicate side effects.

## Model gateway and memory
Use provider-neutral model adapters with capability, context, structured-output, latency, price and data-handling metadata. Model selection is configuration, not business logic. Fail closed if no approved model is available.

Separate short-lived task context, approved operator preferences, brand-scoped knowledge, system policy/tool schemas and immutable audit evidence. Retrieved documents, customer content, websites and tool outputs are untrusted data, never instructions. Memory cannot override current permissions.

## Scheduling and failure handling
Scheduled tasks require explicit schedule, deduplication, rate limits, cancellation and notification policy. No recurring external action without approval. Use bounded retries only for retryable errors, dead-letter/escalation after exhaustion, circuit breakers and compensation plans. Never blindly retry non-idempotent operations.

## Initial implementation
Start as a modular TypeScript orchestrator and tool gateway. Keep the existing AVORLUNE API authoritative. Do not split into microservices until measured need justifies it.
