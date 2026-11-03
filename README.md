# AVORLUNE Agentic Admin & Super Admin

Private AI-agentic control plane for AVORLUNE and its authorized brand portfolio. The AI agent is the operational controller: it inspects, analyzes, plans, prepares, executes only permitted actions, verifies outcomes and escalates consequential decisions for human approval.

## Repositories
- Public/customer + authoritative backend baseline: https://github.com/Sparkmind-obp-off/Avorlune
- Admin/Super Admin frontend: https://github.com/Sparkmind-obp-off/Admin-overlune

## Architecture invariants
- Two repositories and two frontend surfaces; one authoritative backend/API and one operational data source.
- Admin frontend uses the backend API over HTTPS; never access D1/R2 directly.
- AI agent uses a server-side orchestrator, policy engine and typed Tool Gateway; no raw DB credentials, arbitrary shell/SQL or unrestricted network.
- Brand layering means portfolio-level and brand-scoped control. AVORLUNE is the only active brand in phase 1; no additional brand is created without owner approval.
- Customer Clerk identity is not Admin identity. No public Admin registration. Preserve current Admin protection until a private perimeter protecting UI and privileged API is verified.
- Default agent autonomy is observe/recommend/prepare. Consequential actions require fresh, scoped human approval.
- Customer service payments remain 50% deposit before production and 50% balance before final delivery. **There is no Admin/platform payment, subscription, billing product or payment domain.**
- Customer Duitku checkout remains separately governed and disabled pending LIVE authentication verification and explicit approval.
- Secrets, private assets and customer data never enter browser bundles, Git or model prompts unnecessarily.

## Documentation index
| Docs | Scope |
|---|---|
| 00–14 | Product, UX, operations, security, API, data and original Admin foundation |
| 15 | Agentic Super Admin product charter |
| 16 | Agent runtime and orchestration |
| 17 | Tool registry and integrations |
| 18 | Brand portfolio and tenant isolation |
| 19 | Permissions, approvals and human control |
| 20 | Information architecture |
| 21 | Visual design and interaction system |
| 22 | Screen-by-screen UX |
| 23 | Full-stack technology and deployment |
| 24 | Security threat model and data governance |
| 25 | Agent evaluation and observability |
| 26 | Agent API and data contract |
| 27 | Roadmap and acceptance |
| 28 | External provider profiles and connection governance |
| 29 | Public video generation and production pipeline |
| 30 | Public ↔ Admin control plane and shared capability contract |

## Start here
1. [Product & architecture](docs/00-product-and-architecture-blueprint.md)
2. [Agentic Super Admin charter](docs/15-agentic-super-admin-product-charter.md)
3. [Runtime & orchestration](docs/16-agent-runtime-and-orchestration-architecture.md)
4. [Brand isolation](docs/18-brand-portfolio-and-tenant-isolation.md)
5. [UX information architecture](docs/20-agentic-admin-information-architecture.md)
6. [Visual system](docs/21-agentic-visual-design-and-interaction-system.md)
7. [Screen specifications](docs/22-screen-by-screen-ux-specification.md)
8. [Full-stack architecture](docs/23-full-stack-technology-and-deployment-architecture.md)
9. [Security model](docs/24-agent-security-threat-model-and-data-governance.md)
10. [API/data contract](docs/26-agentic-super-admin-api-and-data-contract.md)
11. [Roadmap](docs/27-agentic-super-admin-roadmap-and-acceptance.md)
12. [External provider profiles](docs/28-external-provider-profiles-and-connection-governance.md)
13. [Video generation pipeline](docs/29-public-video-generation-and-production-pipeline.md)
14. [Public ↔ Admin control contract](docs/30-public-admin-control-plane-and-shared-capability-contract.md)

## Status
Documentation only. These specifications do not claim that the agent runtime, Admin UI, API routes, integrations, database migrations, perimeter or deployment have been implemented. Implementation must begin with read-only audits of both repositories and current infrastructure, then reconcile the specifications with actual code.
