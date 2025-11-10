---
status: "accepted"
date: 2025-10-23
decision-makers: [Nimrod Architecture Team]
consulted: [Operations Team, Platform Team, Data Science Team]
informed: [Engineering Teams, Product Teams]
---

# Next.js + React Native with Monorepo for Operations Applications

## Context and Problem Statement

MobilityCorp needs internal applications for operations staff to manage fleet maintenance, vehicle distribution, and operational workflows. The system must support admin workflows via web browser and mobile field operations for technicians performing battery swaps, inspections, and on-site maintenance.

We need to determine an application architecture that supports operations workflows and field mobility while maintaining consistency with customer reservations systems.

## Decision Drivers

- Stream-aligned team ownership of full operations value stream (ADR-001)
- Mobile support for field technicians and fleet managers
- Integration with agentic dispatch workflows
- Deployment independence from customer reservation systems
- Code reuse and development efficiency with customer reservation systems

## Considered Options

- React Native (Expo) for mobile + Next.js/React for web with monorepo
- Native development (Swift/Kotlin) for mobile + Next.js/React for web
- Flutter with web support

## Decision Outcome

Chosen option: "React Native (Expo) for mobile + Next.js/React for web with monorepo", because it aligns with our value stream-aligned architecture (ADR-001), enabling the Operations Team to own their frontend stack while maintaining architectural consistency with customer reservation systems (ADR-011). This approach provides deployment independence and security boundary separation between internal and public traffic, while the shared monorepo enables code reuse through common packages across value streams.

## Pros and Cons of the Options

### React Native (Expo) + Next.js/React with Monorepo

Next.js for operations web app React Native with Expo for field operations mobile app, managed in a monorepo shared with customer applications.

- Good, because stream-aligned team owns full frontend stack independently with deployment autonomy (ADR-001)
- Good, because security boundary separates public customer traffic from internal operations traffic
- Good, because architectural consistency with customer systems reduces operational complexity (ADR-011)
- Good, because monorepo enables code sharing while maintaining deployment independence
- Good, because web platform optimized for data-heavy operational interfaces and real-time fleet visualization
- Bad, because separate UI implementations increase surface area for cross-platform inconsistencies
- Bad, because separate applications increase infrastructure overhead
- Bad, because monorepo complexity increases with multiple teams

### Native Development (Swift/Kotlin) + Next.js/React for Web

Native Swift/Kotlin for field operations mobile with separate Next.js SPA for desktop workflows.

- Good, because best possible native performance for mobile field operations
- Good, because independent evolution paths from customer systems
- Bad, because technology fragmentation with customer systems increases complexity
- Bad, because minimal code sharing increases duplicate effort

### Flutter with Web Support (WebAssembly)

Flutter with Dart for iOS, Android, and web via WebAssembly in single codebase.

- Good, because single codebase maximizes code reuse across platforms
- Good, because consistent UI rendering across all operations platforms
- Neutral, because SEO irrelevant for internal tools
- Bad, because technology fragmentation with customer systems (ADR-011)
- Bad, because smaller ecosystem for data visualization compared to React

## Related Documentation

- [ADR-001: Value Stream-Aligned Systems](./001-value-stream-aligned-systems.md)
- [ADR-005: Dispatch Agent Orchestrator](./005-dispatch-agent-orchestrator.md)
- [ADR-006: Customer Reservations Applications](./006-customer-reservations-frontend.md)
- [ADR-003: Operations API Gateway](./003-operations-system-backend.md)
- [Architecture Diagram](../diagrams/c2-ops.png)
- [System Requirements](../requirements.md)
