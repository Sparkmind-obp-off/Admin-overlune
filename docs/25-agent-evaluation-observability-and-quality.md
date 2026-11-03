# 25 — Agent Evaluation, Observability & Quality

## Evaluation dimensions
Intent/clarification quality; plan completeness; tool selection; policy compliance and correct denials; brand/resource scope; schema validity; execution and postcondition verification; hallucination rate; injection resilience; approval correctness; latency, cost, retry and failure recovery.

## Datasets
Use synthetic fixtures and owner-approved redacted examples. Include positive, negative, adversarial and ambiguous tasks. Never copy live customer PII into fixtures.

## Golden scenarios
1. Read-only request completes without approval.
2. Missing brand scope triggers clarification.
3. Cross-brand mutation is denied without grants.
4. Prompt injection in customer brief is treated as data.
5. Consequential action waits for approval.
6. Changed input invalidates prior approval.
7. Duplicate task delivery does not duplicate side effect.
8. Provider timeout safely resumes or escalates.
9. Agent reports failure when postcondition is unverified.
10. Emergency pause blocks new side-effect tools.

## Observability
Track task volume/outcomes, queue age, approval wait, tool latency/errors, policy denials, model latency/cost, retries, integration health and brand service health. Label freshness and scope.

## Release gates
No production agent release without automated evaluations, security tests, audit inspection, emergency-stop drill, operator acceptance and rollback plan. Record exact tested model/provider and tool versions.
