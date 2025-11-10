---
status: "accepted"
date: 2025-10-23
decision-makers: [Nimrod Architecture Team]
consulted:
  [Customer Reservation Team, Platform Team, Data Science Team, Security Team]
informed: [Engineering Teams, Product Teams, Operations Team]
---

# Python FastAPI for Customer Reservation Backend and API Gateway

## Context and Problem Statement

The Customer Reservation System (ADR-001) requires backend services and an API gateway to handle vehicle reservations, AI-powered travel assistance, and platform integrations. The system serves customer-facing applications (ADR-011) with high concurrency requirements for WebSocket connections, strong type safety, and seamless AI/ML integration while scaling to 10x customer growth across EU markets.

We need to determine a backend and gateway architecture that aligns with AI/ML infrastructure while balancing performance, security, and operational complexity.

## Decision Drivers

- Stream-aligned team ownership of customer value stream (ADR-001)
- Alignment with AI/ML infrastructure (Pydantic AI chosen in ADR-008)
- High concurrency for WebSocket connections and API calls
- Type safety end-to-end with frontend TypeScript models
- Security controls: authentication, rate limiting, DDoS protection
- Horizontal scaling for 10x customer growth across EU
- Deployment independence from Operations system

## Considered Options

- Python FastAPI with third-party managed API Gateway (AWS API Gateway or Cloudflare API Gateway)
- Node.js/Express with AWS API Gateway
- Python FastAPI with custom-built gateway framework (future state)

## Decision Outcome

Chosen option: "Python FastAPI with AWS API Gateway", because it aligns with our value stream-aligned architecture (ADR-001) enabling the Customer Reservation Team to own their backend stack, while providing seamless integration with AI/ML infrastructure (Pydantic AI from ADR-008). The architecture consists of AWS API Gateway routing traffic to two FastAPI services:

1. Reservation API for CRUD operations on customer reservations
2. Travel Agent Orchestrator implementing agentic workflows for trip optimization and commute planning

AWS API Gateway handles security and scaling through managed services with a planned evolution toward a custom gateway framework at higher traffic volumes.

## Pros and Cons of the Options

### Python FastAPI + AWS API Gateway

Python FastAPI for backend services behind AWS API Gateway as managed entry point, serving customer reservation applications from ADR-011. AWS chosen over Cloudflare for superior WebSocket support (critical for Travel Agent real-time chat) and deeper integration with AWS infrastructure. Cloudflare remains viable alternative for edge performance and cost optimization at extreme scale.

- Good, because Python dominates AI/ML ecosystem ensuring seamless integration with Pydantic AI and future ML capabilities
- Good, because stream-aligned team owns complete customer backend stack independently (ADR-001)
- Good, because managed AWS Gateway provides security, DDoS protection, and auto-scaling without operational burden
- Good, because FastAPI async performance supports high concurrency with Pydantic type validation
- Bad, because managed gateway configuration constraints limit customization
- Bad, because costs scale linearly with traffic

### Node.js/Express + AWS API Gateway

Node.js with Express framework for backend services behind AWS API Gateway.

- Good, because JavaScript/TypeScript consistency with frontend reduces language context switching
- Good, because Node.js async performance and massive NPM ecosystem
- Good, because no GIL limitations for concurrent operations
- Bad, because misaligned with AI/ML ecosystem requiring separate Python services for agentic features (ADR-008)
- Bad, because Pydantic AI frameworks are Python-first with limited Node.js support

### Python FastAPI + Custom Gateway (Future State)

Custom API gateway framework designed to handle higher traffic volumes.

- Good, because complete control over routing, filtering, and middleware without vendor constraints
- Good, because cost optimization at scale
- Good, because custom middleware enables advanced features like geo-IP routing and session standardization
- Good, because tight integration with service mesh and per-team gateway instances
- Bad, because requires platform engineering team and upfront investment
- Bad, because operational complexity for security, monitoring, and reliability falls on our team
- Bad, because must justify engineering costs vs managed service fees

## Related Documentation

- [ADR-001: Value Stream-Aligned Systems](./001-value-stream-aligned-systems.md)
- [ADR-013: Pydantic AI for Agentic Framework](./013-agentic-framework.md)
- [ADR-008: Travel Agent Orchestrator](./008-travel-agent-orchestrator.md)
- [ADR-006: Customer Reservations Applications](./006-customer-reservations-frontend.md)
- [ADR-003: Operations API Gateway](./003-operations-system-backend.md)
- [Architecture Diagram](../diagrams/c2-res.png)
- [System Requirements](../requirements.md)
