---
status: "accepted"
date: 2025-10-22
decision-makers: [Nimrod Architecture Team]
consulted: [Engineering Team, Product Team]
informed: [Operations, data science, customer facing teams]
---

# Create Platform Services for Shared Capabilities

## Context and Problem Statement

Our value stream aligned systems (operations and customer reservations) both require common capabilities like user authentication and authorization, notification delivery, and payment processing. Each team could build their own solutions but this would lead to duplication, inconsistent user experiences, and higher cognitive load on teams. How should we provide these capabilities to teams to focus on their core value delivery?

## Considered Options

- Option 1: Each stream-aligned team builds and maintains their own authentication, notification, and payment capabilities
- Option 2: One stream-aligned team builds these capabilities and other teams depend on them
- Option 3: Establish a platform team providing these as shared platform services

## Decision Outcome

Chosen option: "Option 3: Establish a platform team providing these as shared platform services", because it reduces cognitive load on stream-aligned teams, ensures consistency across user experiences, enables specialization in complex domains. It also allows us to create an anti-corruption layer around third-party SaaS solutions, which we suggest leveraging for this functionality.

### Decision Outcome

The following platform services will be provided:

### Authentication and Authorization Service

Provides identity management and access control as a platform capability

- User registration, login, and session management
- Multi-factor authentication (MFA)
- Role-based and attribute-based access control
- JWT token issuance and validation

### Notification Service

Provides reliable, multi-channel notification delivery as a platform capability

- Email, SMS, and push notification delivery
- Template management and personalization
- Delivery tracking and retry logic
- Notification preferences and opt-out management

### Payment Processing Service

Provides secure payment handling as a platform capability

- Payment method tokenization and storage
- Transaction processing and reconciliation
- Refund and chargeback handling
- Integration with payment gateways: Stripe, PayPal, etc.

## Pros and Cons of the Options

### Option 1: Each stream-aligned team builds and maintains their own authentication, notification, and payment capabilities

Each team (Operations and Customer Reservations) independently implements auth, notifications, and payments.

- Good, because teams have full autonomy without external dependencies
- Good, because can optimize implementation for specific team needs
- Bad, because significant duplication of effort across teams
- Bad, because inconsistent user experience and security practices across systems
- Bad, because higher cognitive load on teams building commodity capabilities

### Option 2: One stream-aligned team builds these capabilities and other teams depend on them

Either Operations or Customer Reservations team builds shared capabilities that other teams consume.

- Good, because reduces duplication compared to each team building independently
- Good, because faster than establishing new platform team
- Bad, because creates misaligned incentives - provider team focused on their value stream, not platform quality
- Bad, because capability evolution limited by provider team's bandwidth and priorities
- Bad, because coupling between value streams reduces team autonomy

### Option 3: Establish a platform team providing these as shared platform services

Dedicated platform team provides authentication, notification, and payment services to all stream-aligned teams.

- Good, because stream aligned teams can focus on their specific value streams without building commodity capabilities
- Good, because consistent security, compliance, and user experience across all systems
- Good, because specialized expertise in complex domains is centralized
- Good, because we can build it once and use everywhere
- Good, because clear API contracts and versioning enable independent deployment
- Good, because reduces effort for new features in stream aligned systems
- Bad, because platform team becomes a dependency for stream-aligned teams
- Bad, because requires investment in excellent documentation, developer experience, and support
- Bad, because platform services must be highly reliable and need clear service level objectives and support model
- Bad, because risk of platform services becoming a bottleneck if not properly resourced

## Related Documentation

- [Team Topologies - Platform Teams](https://teamtopologies.com/key-concepts)
- [Team Topologies - Reduce Cognitive Load](https://teamtopologies.com/key-concepts)
- [Thinnest Viable Platform (TVP)](https://teamtopologies.com/key-concepts-content/what-is-a-thinnest-viable-platform-tvp)
