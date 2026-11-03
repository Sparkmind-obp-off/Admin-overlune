# 21 — Agentic Visual Design & Interaction System

## Art direction
Premium editorial control room: warm-neutral workspace, dark ink navigation, restrained accent, crisp typography, fine separators and subtle depth. Calm, precise and trustworthy; avoid neon sci-fi/gamified AI dashboards.

## Tokens
Semantic CSS variables for canvas, surface, elevated surface, text, muted text, border, focus, success, warning, danger and info. Light/dark themes. Status includes text/icon, never color alone. Meet WCAG 2.2 AA contrast and keyboard focus requirements.

## Layout
Desktop-first, tablet capable, mobile monitoring/approval. Sidebar 248px expanded / 72px collapsed; topbar 60–64px; gutters 24–32px; fluid content. Dense tables use readable text and row height.

## Components
App shell, brand selector, environment indicator, command palette, agent dock, task card, plan step, tool badge, risk label, approval card, audit timeline, data table, filter bar, empty/error/stale state, confirmation dialog, diff viewer, schema viewer, chart panel and accessible modal.

## Agent visual language
Clearly distinguish user instruction, concise agent rationale, proposed plan, tool execution, approval required, verified result and warning/error. Show source and freshness. Never present model-generated claims as verified system facts. Do not expose hidden chain-of-thought.

## Interaction
Every side effect is previewable. Risky operations show before/after diff and scoped confirmation. Long tasks show durable progress and cancellation. Errors show sanitized details and request ID. Optimistic UI must not imply success before server confirmation. Respect reduced motion, keyboard, screen readers and Indonesian/English localization readiness.

## Responsive
Desktop: full shell, tables and agent dock. Tablet: collapsible navigation and agent drawer. Mobile: priority alerts, approvals and read-only monitoring; complex bulk changes remain desktop-first.
