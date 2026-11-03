# 10 — CRM, Order & Production Operations

## Customer 360
Profile, verified contact attributes, source/acquisition, consent, tags, owner, customer-visible projects, quotes, payment milestones, deliverables, support tickets, and chronological timeline. Internal notes are visually and technically separated from customer-visible activity.

## Order lifecycle
Brief submitted → qualification → quote drafting → quote sent → accepted/rejected/expired → deposit due/paid → production queued → in production → internal QA → client review → revision (if scoped) → balance due/paid → final delivery → completed/archived.

A state transition must validate prerequisites server-side. No manual status edit may bypass required payment, scope, QA, approval, or delivery checks.

## Production board
Views: queue, assigned to me, deadline risk, internal QA, client review, revision, blocked. Cards show reference, offer type, due date, owner, payment milestone state, and safe status summary.

## Action runs
Action services are bounded, typed jobs with declared inputs, outputs, permissions, checkpoints, logs, and cancellation behavior. Prepare/review/export by default. External publishing, messaging, purchases, ad spend, account changes, and destructive/financial actions require explicit scoped authorization and confirmation.

## Asset and delivery controls
- Upload and download through authenticated backend.
- Private R2 objects; never expose bucket keys.
- Validate MIME/magic bytes, size, file type, and ownership.
- Track versions, license/provenance, QA status, customer approval, and delivery grant.
- Only active approved final asset can be delivered.
- Revocation must invalidate access and create audit event.

## Human review
AI-generated content is not automatically customer-ready. Internal QA and rights/provenance checks precede client review and final delivery.


## Agent orchestration
Agent tasks are separate from customer orders and production jobs. A task has an explicit objective, brand/environment scope, plan, typed steps, approvals, status, evidence and audit references. The agent may read and prepare by default; execution uses the server-side Tool Gateway and must obey the autonomy/approval policy. Do not merge agent task state into order lifecycle state.
