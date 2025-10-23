---
status: "accepted"
date: 2025-10-23
decision-makers: [Nimrod Architecture Team]
consulted: [Customer Team, Mobile Team, UX Team]
informed: [Engineering Teams, Product Teams]
---

# Next.js + React Native with Monorepo for Customer-Facing Applications

## Context and Problem Statement

MobilityCorp needs to provide vehicle reservation functionality to customers
through both web browsers and mobile devices (iOS and Android). The system must
support critical mobile features including NFC vehicle unlocking, real-time GPS
tracking, photo uploads, and WebSocket notifications. Additionally, the application
must support multiple languages across EU markets as we scale to 10x our customer
base across multiple cities and countries.

We need to determine an application architecture that maximizes code reuse and native performance while maintaining cross-platform consistency.

## Decision Drivers

MobilityCorp's priorities for the system include:

- Stream-aligned team ownership of full customer value stream (ADR-001)
- Code reuse and development efficiency
- Native performance for critical features (NFC, GPS, camera)
- Consistent cross-platform user experience
- Multi-language support for EU expansion
- Real-time communication and notifications
- Offline capability for reservations

## Considered Options

- React Native (Expo) for mobile + Next.js/React for web with monorepo
- Native development (Swift/Kotlin) for mobile + Next.js/React for web
- Flutter with web support

## Decision Outcome

Chosen option: "React Native (Expo) for mobile + Next.js/React for web with monorepo", because it provides platform-optimized solutions while aligning with our value stream-aligned architecture (ADR-001), enabling the Customer Reservation Team to own their complete frontend stack independently. The monorepo approach allows substantial code sharing through TypeScript types, API clients, and business logic while maintaining deployment independence from Operations systems.

## Pros and Cons of the Options

### React Native (Expo) + Next.js/React with Monorepo

Use Next.js (or Vite + React) with Tailwind CSS for the web app and React Native with Expo for the iOS and Android apps, all managed within a monorepo (such as Turborepo or Nx). Shared packages handle TypeScript types, an auto-generated API client (from OpenAPI), business logic, and a WebSocket client, allowing each platform to share core functionality while still using the tools best suited to it. The mobile apps are distributed through the app stores with Expo OTA updates, and the web app is served via CDN (CloudFront or Cloudflare) with PWA support for fast, installable experiences.

- Good, because platform-native architecture delivers optimal web SEO and mobile performance without cross-platform compromises
- Good, because separate customer applications enable stream-aligned team to own full frontend stack independently (ADR-001)
- Good, because monorepo enables type-safe code sharing through shared API clients, business logic, and TypeScript types
- Good, because OTA updates allow rapid iteration and bug fixes without waiting for app store approvals
- Good, because React Native's bridge provides direct access to native device capabilities such as NFC, GPS, and camera
- Bad, because separate UI implementations increase surface area for cross-platform inconsistencies
- Bad, because monorepo tooling complexity requires dedicated build infrastructure and expertise

### Native Development (Swift/Kotlin) + Next.js/React for Web

Build fully native mobile applications using Swift for iOS and Kotlin for Android, with a separate Next.js/React-based Single-Page Application for web browsers. This traditional approach provides maximum platform optimization and control at the cost of maintaining three independent codebases with minimal shared code (only TypeScript types if using type generation).

- Good, because best possible native performance and direct access to all platform APIs without abstraction
- Good, because each platform can evolve independently without cross-platform constraints
- Bad, because requires three separate codebases with minimal code sharing between mobile platforms
- Bad, because 3x development time and requires teams skilled in Swift, Kotlin, and React/TypeScript
- Bad, because significantly higher maintenance costs and difficulty maintaining feature parity across platforms

### Flutter with Web Support (WebAssembly)

Use Google's Flutter framework with the Dart programming language for iOS, Android, and web applications compiled to [WebAssembly](https://docs.flutter.dev/platform-integration/web). This provides a true single codebase approach where the same Flutter widgets and business logic run across all platforms.

- Good, because using a single codebase across mobile and web reduces development effort
- Good, because compiled Dart to WebAssembly provides consistent UI/UX across all platforms
- Good, because mature tooling with hot reload and growing enterprise adoption
- Bad, because [Flutter web lacks SEO support](https://docs.flutter.dev/platform-integration/web/faq#search-engine-optimization-seo)
- Bad, because web experience suffers from larger bundle sizes, accessibility gaps, and limited web-native feature integration

## Related Documentation

- [ADR-001: Value Stream-Aligned Systems](./001-value-stream-aligned-systems.md)
- [ADR-010: Travel Agent Using GenAI](./010-agentic-travel-copilot.md)
- [ADR-012: Customer API Gateway](./012-customer-api-gateway.md)
- [ADR-013: Operations Applications](./013-operations-applications.md)
- [Architecture Diagram](../diagrams/c2-res.png)
- [System Requirements](../requirements.md)
