# 11 — Audit, Observability & Incident Response

## Audit events
Record actor/principal type, role, action, resource type/id, brand, agent task/run/tool version where applicable, policy decision, outcome, reason, request ID, timestamp, safe before/after diff, approval ID, and source environment. Exclude secrets, tokens, raw payment credentials, full brief content, and unnecessary personal data.

## Events that must be audited
Authentication success/failure, session revocation, permission changes, customer export, quote/order changes, payment callback and reconciliation, refunds, asset upload/revoke/delivery, action-run execution, provider configuration, feature flags, release promotion, and incident response.

## Observability
- Structured server logs with request/correlation IDs.
- Metrics for latency, error rate, queue depth, callback failure, D1/R2 errors, and authorization denials.
- Alerts for anomalies and high-risk events.
- Health endpoints expose operational status only, never credentials or private metadata.
- Retention and access policies documented; production logs are not a customer data store.

## Incident playbooks
1. Suspected admin account compromise: revoke sessions/perimeter access, rotate affected credentials, preserve audit evidence.
2. Payment mismatch or duplicate: pause affected settlement, verify provider server-side, reconcile with compensating record.
3. Asset leak: revoke grants, invalidate links, investigate object access, notify according to policy.
4. API compromise: disable affected feature/route, rotate secrets, preserve evidence, assess customer impact.
5. Cross-environment access: immediately disable bindings/credentials and inspect audit trail.

## Incident controls
Super Admin can initiate safe containment (revoke session, disable feature flag, pause an integration) only with explicit confirmation and audit. Destructive database actions are not available in the Admin UI.


## Agent audit evidence
For each agent task and tool invocation, retain the initiating human, agent identity, active brand/environment, tool and schema version, redacted input reference, policy result, approval reference, idempotency key, postcondition verification and evidence pointer. Never log hidden chain-of-thought, secrets or unnecessary customer data.
