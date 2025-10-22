# Value Stream-Aligned Systems

## Context and Problem Statement

How should we organize the larger systems architecture? Should we split the system across different techincal layers, keep it simple as a monolith or look into some other architecture aligned by value streams? Each user group has different needs, frequency of change, and business priorities. How should we organize our systems to optimize for independent value delivery and team autonomy?

## Considered Options

* Option 1: Maintain a single monolithic system serving all use cases
* Option 2: Split into value stream-aligned systems organized by user type and business capability
* Option 3: Split into technical layer-based systems (frontend, backend, data)

## Decision Outcome

Chosen option: "Option 2: Split into value stream-aligned systems", because it enables independent delivery of value to distinct user groups, allows teams to optimize for their specific users' needs, and reduces coupling between systems serving different business purposes.

The system will be split into three value stream-aligned systems:

### 1. Operations System
**Purpose**: Enable internal staff to manage and operate the business, also focus on delivering features tailored to maintain and redistribute our fleet based on demand.
- **Components**: UI, backend, databases, agents
- **Primary Users**: Internal operations staff, administrators, fleet redistributors and maintainers
- **Value Stream**: Operational efficiency and business management

### 2. Customer Reservation System
**Purpose**: Enable customers to discover, book, and manage reservations
- **Components**: Customer-facing UIs, reservations backend, databases, and customer facing agents
- **Primary Users**: Customers
- **Value Stream**: Customer acquisition, booking conversion, customer reliance on services

### 3. Data Intelligence Platform System
**Purpose**: Enable data scientists and analysts to experiment with ML models and derive insights
- **Components**: Data pipelines, ML experimentation environment, Feature stores
- **Primary Users**: Data scientists, ML engineers, analysts
- **Value Stream**: Data-driven insights and ML capabilities

### 4. Engineering Platform Systems
**Purpose**: Enable engineers via a series a platform capabilities that are shared across the infrastructure, and separate complex subsystems
- **Components**: DevOps, accounts and auth, notifications, payment processing
- **Primary Users**: Stream aligned engineering teams
- **Value Stream**: Platforms, enablement, and complex subsystems

## Consequences

### Positive

* Each system can evolve independently at its own pace based on user needs
* Teams can be organized around value streams with clear ownership and accountability
* Functionality can be encapsulated in different bounded contexts with strong contracts based on user scenarios
* Technology choices can be optimized per system (e.g., different databases, frameworks)
* Easier to scale systems independently based on their specific load patterns

### Negative

* Requires establishing contracts/APIs between systems for any cross-system functionality
* Increases operational complexity with multiple deployments and infrastructure
* Potential for data duplication across systems
* Need for cross-system observability and monitoring strategy
* May require shared services or platform capabilities (authentication, logging, etc.)

## Links

* [Team Topologies - Stream-Aligned Teams](https://teamtopologies.com/key-concepts)
* [Domain-Driven Design - Bounded Contexts](https://martinfowler.com/bliki/BoundedContext.html)