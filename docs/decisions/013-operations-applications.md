---
status: "accepted"
date: 2025-10-23
decision-makers: [Nimrod Architecture Team]
consulted: [Operations Team, Platform Team, Data Science Team]
informed: [Engineering Teams, Product Teams]
---

# Next.js + React Native with Monorepo for Operations Applications

## Context and Problem Statement

MobilityCorp needs internal applications for operations staff to manage fleet maintenance, vehicle distribution, and operational workflows. The system must support desktop workflows via web browser and mobile field operations for technicians performing battery swaps, inspections, and on-site maintenance. The applications integrate with agentic AI workflows, real-time data visualization, and admin interfaces across multiple EU markets.

We need to determine an application architecture that supports operations workflows and field mobility while maintaining consistency with customer-facing systems.

## Decision Drivers

- Stream-aligned team ownership of full operations value stream (ADR-001)
- Deployment independence from customer-facing systems
- Real-time operational data visualization and dashboards
- Mobile support for field technicians and fleet managers
- Integration with agentic dispatch workflows
- Code reuse and development efficiency with customer systems
- Complex data-heavy UI components (tables, charts, maps)

## Considered Options

- React Native (Expo) for mobile + Next.js/React for web with monorepo
- Native development (Swift/Kotlin) for mobile + Next.js/React for web
- Flutter with web support

## Decision Outcome

Chosen option: "React Native (Expo) for mobile + Next.js/React for web with monorepo", because it aligns with our value stream-aligned architecture (ADR-001), enabling the Operations Team to own their complete frontend stack independently while maintaining architectural consistency with customer systems (ADR-011). This approach provides deployment independence and security boundary separation between internal and public traffic, while the shared monorepo enables code reuse through common packages across value streams.

## Pros and Cons of the Options

### React Native (Expo) + Next.js/React with Monorepo

Next.js for operations web app with advanced data visualization and React Native with Expo for field operations mobile app, managed in a monorepo shared with customer applications.

- Good, because stream-aligned team owns full frontend stack independently with deployment autonomy (ADR-001)
- Good, because security boundary separates public customer traffic from internal operations traffic
- Good, because architectural consistency with customer systems reduces operational complexity (ADR-011)
- Good, because monorepo enables code sharing while maintaining deployment independence
- Bad, because separate applications increase infrastructure overhead
- Bad, because monorepo complexity increases with multiple teams

### Native Development (Swift/Kotlin) + Next.js/React for Web

Native Swift/Kotlin for field operations mobile with separate Next.js web for desktop workflows.

- Good, because maximum native performance for mobile field operations
- Good, because independent evolution paths from customer systems
- Bad, because technology fragmentation with customer systems increases complexity
- Bad, because minimal code sharing increases duplicate effort

### Flutter with Web Support (WebAssembly)

Flutter with Dart for iOS, Android, and web via [WebAssembly](https://docs.flutter.dev/platform-integration/web) in single codebase.

- Good, because single codebase maximizes code reuse across platforms
- Good, because SEO irrelevant for internal tools, eliminating Flutter's primary limitation
- Good, because consistent UI rendering across all operations platforms
- Bad, because technology fragmentation with customer systems (ADR-011)
- Bad, because smaller ecosystem for data visualization compared to React

## Related Documentation

- [ADR-001: Value Stream-Aligned Systems](./001-value-stream-aligned-systems.md)
- [ADR-009: Agentic Dispatch Workflow](./009-agentic-dispatch-workflow.md)
- [ADR-011: Customer Reservations Applications](./011-customer-reservations-applications.md)
- [ADR-014: Operations API Gateway](./014-operations-api-gateway.md)
- [Architecture Diagram](../diagrams/c2-ops.png)
- [System Requirements](../requirements.md)
