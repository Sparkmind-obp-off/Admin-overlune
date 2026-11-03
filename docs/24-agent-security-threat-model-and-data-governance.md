# 24 — Agent Security Threat Model & Data Governance

## Threats
Prompt injection; cross-brand leakage; privilege escalation; compromised tools; replayed approvals; duplicate side effects; hallucination; secret exfiltration; unsafe memory; compromised integrations; PII leakage in logs; dependency compromise.

## Controls
Server-side RBAC/ABAC and brand/environment scope; untrusted-data isolation; typed allowlisted tools; no arbitrary SQL/shell/code execution; minimum-data retrieval; secret redaction; approvals bound to exact action and expiry; idempotency and postcondition verification; rate limits, quotas, timeouts, circuit breakers and kill switch; signed webhook/replay protection; append-only audit; dependency pinning and restore drills.

## Classification
Public; internal; confidential customer/business; restricted credentials/security/payment. Models receive only the minimum necessary data. Restricted values never enter prompts, tool output, analytics or logs.

## Audit
Record principal, actor type, brand, environment, task/run, tool/version, policy decision, approval, resource IDs, timestamp, outcome and evidence pointer. Do not store hidden chain-of-thought; store concise rationale and observable evidence.

## Privacy
Retention and deletion rules are defined per data class. Customer consent remains authoritative. Cross-brand aggregation is minimized. No customer data is used for model training unless separately and lawfully authorized.

## Validation
Test injection resistance, tenant isolation, role boundaries, invalid/replayed/expired approvals, schema bypass, malformed output, secret redaction, audit integrity, emergency pause, environment isolation and unauthorized direct API calls.
