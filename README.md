# Nimrod Team's MobilityCorp AI Enabled Architecture

![Tower of Babel](/assets/tower-of-babel.png "tower of babel")

## Table of Contents

- [Overview](#overview)
  - [Core Business Challenges](#core-business-challenges)
  - [Meet the Nimrods](#meet-the-nimrods)
- [Requirements](#requirements)
  - [Functional and non-functional requirements](/docs/requirements.md)
- [System Design](#system-design)
  - [MobilityCorp System Context Diagram (C1)](/docs/diagrams/c1-context.png)
  - [Reservation Service Container Diagram (C2)](/docs/diagrams/c2-res.png)
  - [Travel Agent Component Diagram (C3)](/docs/diagrams/c3-travel-agent.png)
  - [Operations Service Container Diagram (C2)](/docs/diagrams/c2-ops.png)
  - [Dispatch Agent Component Diagram (C3)](/docs/diagrams/c3-dispatch-agent.png)
  - [Data Intelligence Platform Container Diagram (C2)](/docs/diagrams/c2-data.png)
- [Architecture Decision Records (ADRs)](#architecture-decision-records-adrs)
  - [Create Value Stream-Aligned Systems](/docs/decisions/001-value-stream-aligned-systems.md)
  - [Create Platform Services for Shared Capabilities](/docs/decisions/002-platform-services.md)
  - [Adopt Medallion Architecture using Iceberg format for Data Lake](/docs/decisions/003-medallion-data-lake.md)
  - [Use Databricks for ETL, ML Experimentation, and Model Serving](/docs/decisions/004-databricks-for-etl-mlflow-inference.md)
  - [Extensible External Data Provider Architecture](/docs/decisions/005-external-data-providers.md)
  - [Demand Forecasting with LightGBM Machine Learning Model](/docs/decisions/006-forecast-model.md)
  - [Google OR-Tools for Vehicle Redistribution Optimization](/docs/decisions/007-redistribution-optimizer-algo.md)
  - [Pydantic AI for our Agentic Framework Foundation](/docs/decisions/008-agentic-framework.md)
  - [Agentic Dispatch Workflow Using GenAI](/docs/decisions/009-agentic-dispatch-workflow.md)
  - [Travel "Agent" Using GenAI](/docs/decisions/010-agentic-travel-copilot.md)
  - [Next.js + React Native with Monorepo for Customer Reservations Applications](/docs/decisions/011-customer-reservations-applications.md)
  - [Python FastAPI for Customer Reservation Backend and API Gateway](/docs/decisions/012-customer-api-gateway.md)
  - [Next.js + React Native with Monorepo for Operations Applications](/docs/decisions/013-operations-applications.md)
  - [Python FastAPI for Operations Backend and API Gateway](/docs/decisions/014-operations-api-gateway.md)

## Overview

MobilityCorp is a multi-modal urban mobility provider offering short-term rentals of electric scooters, eBikes, electric cars, and electric vans across multiple city and suburban locations throughout the European Union. The company operates a "last-mile transport" model where customers can book vehicles on-demand through a mobile app, access them via NFC technology, and return them to designated parking spots.

### Core Business Challenges

MobilityCorp faces three interconnected challenges that directly impact revenue, customer satisfaction, and operational efficiency. Customers can't find vehicles when they need them, vehicles run out of power mid-service, and users treat the service as a occasional convenience rather than a reliable daily transportation option. These issues stem from reactive operations rather than predictive, data-driven decision making.

### Meet the Nimrods

_Architects of big ideas since Babylonia_

- **Eric Olson** [[LinkedIn](https://www.linkedin.com/in/olsoneric/)] [[GitHub](https://github.com/ericjohnolson)] - Principal Software Engineer
- **Kelsey Roy** [[LinkedIn](https://www.linkedin.com/in/kelseytroy/)] [[GitHub](https://github.com/kelseyroy)] - Senior Software Engineer
- **Jonathan Manahan** [[LinkedIn](https://www.linkedin.com/in/jonathan-manahan/)] [[GitHub](https://github.com/jonmanahan)] - Software Engineer

## Requirements

[Functional and non-functional requirements](/docs/requirements.md)

## System Design

### MobilityCorp System Context Diagram (C1)

![System Context Diagram](/docs/diagrams/c1-context.png "System Context Diagram")

### Reservation Service Container Diagram (C2)

![Reservation Service Container Diagram (C2)](/docs/diagrams/c2-res.png "Reservation Service Container Diagram (C2)")

### Travel Agent Component Diagram (C3)

![Travel Agent Component Diagram (C3)](/docs/diagrams/c3-travel-agent.png "Travel Agent Component Diagram (C3))")

### Operations Service Container Diagram (C2)

![Operations Service Container Diagram (C2)](/docs/diagrams/c2-ops.png "Operations Service Container Diagram (C2)")

### Dispatch Agent Component Diagram (C3)

![Dispatch Agent Component Diagram (C3)](/docs/diagrams/c3-dispatch-agent.png "Dispatch Agent Component Diagram (C3))")

### Data Intelligence Platform Container Diagram (C2)

![Data Intelligence Platform Container Diagram (C2)](/docs/diagrams/c2-data.png "Data Intelligence Platform Container Diagram (C2)")

### Experimentation Platform Component Diagram (C3)

![Experimentation Platform Component Diagram (C3)](/docs/diagrams/c3-exp.png "Experimentation Platform Component Diagram (C3)")

## Architecture Decision Records (ADRs)

1. [Create Value Stream-Aligned Systems](/docs/decisions/001-value-stream-aligned-systems.md)
2. [Create Platform Services for Shared Capabilities](/docs/decisions/002-platform-services.md)
3. [Adopt Medallion Architecture using Iceberg format for Data Lake](/docs/decisions/003-medallion-data-lake.md)
4. [Use Databricks for ETL, ML Experimentation, and Model Serving](/docs/decisions/004-databricks-for-etl-mlflow-inference.md)
5. [Extensible External Data Provider Architecture](/docs/decisions/005-external-data-providers.md)
6. [Demand Forecasting with LightGBM Machine Learning Model](/docs/decisions/006-forecast-model.md)
7. [Google OR-Tools for Vehicle Redistribution Optimization](/docs/decisions/007-redistribution-optimizer-algo.md)
8. [Pydantic AI for our Agentic Framework Foundation](/docs/decisions/008-agentic-framework.md)
9. [Agentic Dispatch Workflow Using GenAI](/docs/decisions/009-agentic-dispatch-workflow.md)
10. [Travel "Agent" Using GenAI](/docs/decisions/010-agentic-travel-copilot.md)
11. [Next.js + React Native with Monorepo for Customer Reservations Applications](/docs/decisions/011-customer-reservations-applications.md)
12. [Python FastAPI for Customer Reservation Backend and API Gateway](/docs/decisions/012-customer-api-gateway.md)
13. [Next.js + React Native with Monorepo for Operations Applications](/docs/decisions/013-operations-applications.md)
14. [Python FastAPI for Operations Backend and API Gateway](/docs/decisions/014-operations-api-gateway.md)
