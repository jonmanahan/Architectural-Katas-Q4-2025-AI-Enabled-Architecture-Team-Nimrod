---
status: "accepted"
date: 2025-10-22
decision-makers: [Nimrod Architecture Team]
consulted: [Operations Team, Data Science Team, Reservation Team]
informed: [Engineering Teams, Product Teams]
---

# Create Value Stream-Aligned Systems

## Context and Problem Statement

How should we organize the larger systems architecture? Should we split the system across different techincal layers, keep it simple as a monolith or look into some other architecture aligned by value streams? Each user group has different needs, frequency of change, and business priorities. How should we organize our systems to optimize for independent value delivery and team autonomy?

## Considered Options

* Option 1: Maintain a single monolithic system serving all use cases
* Option 2: Split into value stream-aligned systems organized by user type and business capability
* Option 3: Split into technical layer-based systems (frontend, backend, data)

## Decision Outcome

Chosen option: "Option 2: Split into value stream-aligned systems", because it enables independent delivery of value to distinct user groups, allows teams to optimize for their specific users' needs, and reduces coupling between systems serving different business purposes.

The system will be split into three value stream-aligned and platform services

### Operations System
Enable internal staff to manage and operate the business, also focus on delivering features tailored to maintain and redistribute our fleet based on demand.
- Components include UI, backend, databases, agents
- Users include internal operations staff, administrators, fleet redistributors and maintainers
- Value stream aligned to operational efficiency and business management

### Customer Reservation System
Enable customers to discover, book, and manage reservations
- Components include customer-facing UIs, reservations backend, databases, and customer facing agents
- Users include customers
- Value stream aligned to customer acquisition, booking conversion, customer reliance on services

### Data Intelligence Platform System
Enable data scientists and analysts to experiment with ML models and derive insights
- Components include data pipelines, ML experimentation environment, Feature stores
- Users include Data scientists, ML engineers, analysts
- Value stream aligned to data-driven insights and ML capabilities
- Platform aligned to leveraging off the self platform components

### Platform Services
 Enable engineers via a series a platform capabilities that are shared across the infrastructure, and separate complex subsystems
- Components include devops templates, accounts and auth, notifications, payment processing
- Users include stream aligned engineering teams
- Focus on platform, enablement, and complex subsystem team roles

## Consequences

* Good, because each system can evolve independently at its own pace based on user needs
* Good, because teams can be organized around value streams with clear ownership and accountability
* Good, because functionality can be encapsulated in different bounded contexts with strong contracts based on user scenarios
* Good, because technology choices can be optimized per system
*  Good, because easier to scale systems independently based on their specific load patterns
* Bad, because requires establishing contracts/APIs between systems for any cross-system functionality
* Bad, because increases operational complexity with multiple deployments and infrastructure

## Related Documentation

* [Team Topologies - Stream-Aligned Teams](https://teamtopologies.com/key-concepts)
* [Domain-Driven Design - Bounded Contexts](https://martinfowler.com/bliki/BoundedContext.html)