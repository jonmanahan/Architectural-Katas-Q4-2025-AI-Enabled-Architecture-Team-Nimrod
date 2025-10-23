# Establish Platform Services for Cross-Cutting Capabilities

## Context and Problem Statement

Our value stream-aligned systems (operations and customer reservations) both require common capabilities: user authentication and authorization, notification delivery, and payment processing. Each stream-aligned team could build these independently, but this would lead to duplication, inconsistent user experiences, and cognitive load on teams. How should we provide these capabilities to enable stream-aligned teams to focus on their core value delivery?

## Considered Options

* Option 1: Each stream-aligned team builds and maintains their own authentication, notification, and payment capabilities
* Option 2: One stream-aligned team builds these capabilities and other teams depend on them
* Option 3: Establish a platform team providing these as shared platform services
* Option 4: Use exclusively third-party SaaS solutions for all capabilities

## Decision Outcome

Chosen option: "Option 3: Establish a platform team providing these as shared platform services", because it reduces cognitive load on stream-aligned teams, ensures consistency across user experiences, enables specialization in complex domains (security, payments). It also allows us to create an anti-corruption layer around third-party SaaS solutions, which we suggest leveraging for this functionality.

The following platform services will be provided:

### 1. Authentication and Authorization Service
**Purpose**: Provide identity management and access control as a platform capability
- User registration, login, and session management
- Multi-factor authentication (MFA)
- Role-based and attribute-based access control
- JWT token issuance and validation

### 2. Notification Service
**Purpose**: Provide reliable, multi-channel notification delivery as a platform capability
- Email, SMS, and push notification delivery
- Template management and personalization
- Delivery tracking and retry logic
- Notification preferences and opt-out management

### 3. Payment Processing Service
**Purpose**: Provide secure payment handling and PCI compliance as a platform capability
- Payment method tokenization and storage
- Transaction processing and reconciliation
- Refund and chargeback handling
- PCI DSS compliance boundary management
- Integration with payment gateways (Stripe, PayPal, etc.)

## Consequences

### Positive

* Stream-aligned teams can focus on their specific value streams without building commodity capabilities
* Consistent security, compliance, and user experience across all systems
* Specialized expertise in complex domains (security, payments, compliance)
* Build once, use everywhere
* Easier to maintain compliance and audit requirements in centralized services
* Clear API contracts and versioning enable independent deployment
* Reduces time-to-market for new features in stream-aligned systems

### Negative

* Platform team becomes a dependency for stream-aligned teams
* Requires investment in excellent documentation, developer experience, and support
* Platform services must be highly reliable and need clear service level objectives and support model
* Risk of platform services becoming a bottleneck if not properly resourced

## Links
* [Team Topologies - Platform Teams](https://teamtopologies.com/key-concepts)
* [Team Topologies - Reduce Cognitive Load](https://teamtopologies.com/key-concepts)
* [Thinnest Viable Platform (TVP)](https://teamtopologies.com/key-concepts-content/what-is-a-thinnest-viable-platform-tvp)