---
status: "accepted"
date: 2025-10-23
decision-makers: [Nimrod Architecture Team]
consulted: [Operations Team, Platform Team, Data Science Team, Security Team]
informed: [Engineering Teams, Product Teams]
---

# Python FastAPI for Operations Backend and API Gateway

## Context and Problem Statement

The Operations System (ADR-001) requires backend services and an API gateway to handle fleet management, dispatch optimization, and operational workflows. The system serves internal operations applications (ADR-013), integrating with Reservation System for admin operations, Data Intelligence Platform for forecasting, and Operations Database for operational data persistence while maintaining security separation from public customer traffic.

We need to determine a backend and gateway architecture that aligns with AI/ML infrastructure, supports operational integrations, and provides enhanced security for internal traffic.

## Decision Drivers

- Stream-aligned team ownership of operations value stream (ADR-001)
- Alignment with AI/ML infrastructure (Pydantic AI chosen in ADR-008)
- Security boundary separation from public customer traffic
- Real-time dispatch optimization and operational analytics
- Admin CRUD operations for reservations and operational data
- Deployment independence from Customer Reservation system
- Architectural consistency with customer backend (ADR-012)

## Considered Options

- Python FastAPI with AWS API Gateway (potentially VPC-restricted)
- Node.js/Express with AWS API Gateway
- Python FastAPI with custom-built gateway framework (future state)

## Decision Outcome

Chosen option: "Python FastAPI with AWS API Gateway", because it aligns with our value stream-aligned architecture (ADR-001) enabling the Operations Team to own their backend stack independently, while maintaining architectural consistency with customer reservation systems (ADR-012). The architecture consists of AWS API Gateway routing traffic to two FastAPI services:

1. Admin API for CRUD operations on reservations via the Reservation System and operational data
2. Dispatch Agent Orchestrator implementing agentic workflows with our Data Intelligence Platform integration for forecasting

Python provides seamless integration with our AI/ML infrastructure, while AWS Gateway provides security and potential VPC/IP restrictions for internal-only traffic.

## Pros and Cons of the Options

### Python FastAPI + AWS API Gateway

Python FastAPI for backend services behind AWS API Gateway, serving operations applications from the operations SPA/cross-platform mobile app with enhanced security for internal traffic.

- Good, because Python dominates AI/ML ecosystem ensuring seamless integration with Dispatch Agent workflows (ADR-009)
- Good, because stream-aligned team owns complete operations backend stack independently (ADR-001)
- Good, because architectural consistency with customer backend reduces operational complexity (ADR-012)
- Good, because security boundary separation allows VPC-only or IP-restricted access for internal staff
- Good, because deployment independence ensures operations can function when customer systems are down
- Bad, because maintaining separate gateway increases infrastructure overhead
- Bad, because managed gateway configuration constraints limit customization

### Node.js/Express + AWS API Gateway

Node.js with Express framework for backend services behind AWS API Gateway for operations.

- Good, because JavaScript/TypeScript consistency with operations frontend
- Good, because Node.js async performance and NPM ecosystem
- Bad, because misaligned with AI/ML ecosystem requiring separate Python services for Dispatch Agent (ADR-009)
- Bad, because technology fragmentation from customer backend increases complexity
- Bad, because Pydantic AI frameworks are Python-first with limited Node.js support

### Python FastAPI + Custom Gateway (Future State)

Custom API gateway framework designed to handle higher traffic volumes for operations traffic, potentially shared infrastructure with customer gateway evolution.

- Good, because complete control over routing and internal security policies
- Good, because cost optimization at scale
- Good, because custom middleware for operations-specific features like audit logging and compliance
- Bad, because requires platform engineering team and upfront investment
- Bad, because operational complexity for security and monitoring
- Bad, because must justify engineering costs for internal-only traffic

## Related Documentation

- [ADR-001: Value Stream-Aligned Systems](./001-value-stream-aligned-systems.md)
- [ADR-008: Pydantic AI for Agentic Framework](./008-agentic-framework.md)
- [ADR-009: Agentic Dispatch Workflow](./009-agentic-dispatch-workflow.md)
- [ADR-012: Customer API Gateway](./012-customer-api-gateway.md)
- [ADR-013: Operations Applications](./013-operations-applications.md)
- [Architecture Diagram](../diagrams/c2-ops.png)
