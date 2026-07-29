# Anthony — building Optqo

I am the founder and sole human engineer behind **Optqo**, a production platform for UK trade services.

The source repository is private because the value is in the operational logic, not in making that logic easy to copy. This page is the deliberately high-level technical view: what I build, the engineering surface I cover, and the standards I apply—without publishing the system's playbook.

![JavaScript](https://img.shields.io/badge/JavaScript-ES_modules-F7DF1E?logo=javascript&logoColor=111)
![Cloudflare Workers](https://img.shields.io/badge/Cloudflare-Workers-F38020?logo=cloudflare&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-source_of_truth-4169E1?logo=postgresql&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-CI%2FCD-2088FF?logo=githubactions&logoColor=white)

## What I work on

- Event-driven backend systems and distributed edge services
- Real-time telephony, routing, transcription, and communications
- Payment lifecycles, reconciliation, and failure recovery
- Identity, verification, compliance, and evidence-handling workflows
- AI-assisted classification and decision support with deterministic safeguards
- Internal control planes, operational tooling, observability, and automated recovery
- Secure third-party integrations across communications, payments, advertising, and identity

## Optqo, technically

Optqo is not a monolith. It is a fleet of small, independently deployable services built around an event-driven architecture.

| Area | High-level implementation |
|---|---|
| Runtime | 50+ Cloudflare Workers using modern vanilla JavaScript ES modules |
| System of record | Supabase PostgreSQL with database events, scheduled work, and realtime consumers |
| Edge state | Durable Objects, Workers KV, private object storage, and durable queues |
| Integration style | Signed webhooks, internal service bindings, background jobs, and provider APIs |
| Interfaces | Public web flows, authenticated operator dashboards, and messaging surfaces |
| Reliability | Idempotent operations, explicit failure modes, recovery jobs, health monitoring, and kill switches |
| Security | Server-side secrets, signature verification, constant-time credential checks, and private evidence storage |
| Delivery | GitHub Actions, automated deployment, semantic releases, and 150+ dependency-light self-checks |

```mermaid
flowchart LR
    A["Calls · messages · web events"] --> B["Edge service fleet"]
    B <--> C["PostgreSQL source of truth"]
    B <--> D["Durable edge state"]
    B <--> E["External provider APIs"]
    F["Operator control plane"] --> B
    G["CI · self-checks · releases"] --> B
```

The private repository also contains the supporting architecture documentation, database and service inventories, design notes, verification records, operational runbooks, and deployment automation required to keep a production system understandable.

## Engineering principles

- Keep services small and ownership boundaries clear.
- Prefer platform primitives and simple code over unnecessary frameworks.
- Treat retries, duplicate events, partial failure, and stale state as normal operating conditions.
- Fail closed at security and compliance boundaries.
- Put irreversible financial or account actions behind idempotency and reconciliation.
- Keep documentation and runnable checks beside the behaviour they protect.
- Automate routine operations while preserving a human decision point where judgement matters.

## What is intentionally not public

The private codebase includes proprietary decision logic, prompts, thresholds, routing rules, data models, operational controls, provider configuration, and abuse-prevention measures. Those details are omitted here on purpose.

This repository is a window into the engineering scope—not a blueprint of the product.

## Credits

I am currently the only human contributing to Optqo. I design, build, operate, and take responsibility for the system.

AI coding agents help me implement, test, review, investigate, and document the work. They are capable collaborators and very fast typists; the product direction and final decisions remain mine. :)
