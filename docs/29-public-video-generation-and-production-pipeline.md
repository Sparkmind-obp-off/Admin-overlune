# 29 — Public Video Generation & Production Pipeline

## Product intent
Video is an optional capability within AVORLUNE's public AI Creative Production experience. Customers submit a brief and receive a managed generation workflow. The public UI does not talk directly to Runway/Luma or any provider.

## Customer journey
1. Select Video Creation in the public service/product catalogue (only when enabled).
2. Choose a use case: product promo, social vertical short, cinematic brand clip, multi-shot story or image-to-video.
3. Provide brief, script/prompt, aspect ratio, duration, reference assets and intended platform.
4. Validate rights, consent, content safety, asset format and scope.
5. Show transparent estimate, provider/model class and delivery expectations where known.
6. Customer confirms brief and any required payment milestone according to existing quote/order rules.
7. Backend creates an order-linked generation job.
8. Agent or orchestration service prepares storyboard/prompt and chooses an enabled provider/model within budget and policy.
9. Human review may be required for high-risk content or external publishing.
10. Provider job runs asynchronously; backend tracks status and retries safely.
11. Output is copied into private R2 after validating ownership, MIME, size and checksum; create expiring signed delivery access only when authorized.
12. QA, revisions and final delivery follow the existing customer order workflow.

## Public UI
Catalogue card, brief builder, reference asset uploader, script/storyboard preview, quote/estimate, generation status timeline, preview player, revision request and final deliverable area. Show honest pending/failed/partial states. Do not expose provider API keys, raw provider job credentials or private bucket paths.

## Job lifecycle
draft → validated → quoted → awaiting_customer_confirmation → queued → submitting → processing → retrieving → asset_validation → internal_review → revision_requested | ready_for_customer_preview → approved → final_delivery_ready → delivered; terminal failed/cancelled/expired states are explicit.

Persist provider task ID, provider profile/version, model, normalized request hash, cost estimate/actual cost if available, retry count, idempotency key, timestamps, error category, asset references and audit evidence. Do not duplicate customer order lifecycle; generation job is a child workflow linked to order/project.

## Provider adapter
Provider-neutral interface: capabilities(), validateInput(), estimateCost() when supported, submit(), getStatus(), retrieveOutput(), cancel() when supported. Normalize provider-specific states and errors. Use webhook where supported with signature verification and replay protection; otherwise bounded polling with backoff. Never assume cancellation or refund is supported.

## Safety and quality
Validate customer asset rights, likeness/voice consent, trademarks, music rights, prohibited content and provider policy. Do not promise output ownership or commercial usage rights without verifying provider terms. Add provenance metadata and record model/provider version. Human QA before final customer delivery.

## Costs and quotas
Generation is not free by default. Display estimate/price before customer commitment. Enforce per-customer, per-brand and per-provider budgets, concurrency caps and kill switch. No generation job can incur paid provider cost until owner-approved provider, budget and customer pricing are configured.

## Initial launch strategy
Keep Video Creation disabled or marked request-only until one provider is connected, tested, commercially reviewed, priced and approved. First release may be a human-assisted production workflow with no automatic generation. Add one adapter at a time.
