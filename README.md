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
  - [Next.js + React Native with Monorepo for Operations Applications](/docs/decisions/002-operations-system-frontend.md)
  - [Python FastAPI for Operations Backend and API Gateway](/docs/decisions/003-operations-system-backend.md)
  - [Extensible External Data Provider Architecture](/docs/decisions/004-external-data-providers.md)
  - [Agentic Dispatch Workflow Using GenAI](/docs/decisions/005-agentic-dispatch-workflow.md)
  - [Next.js + React Native with Monorepo for Customer Reservations Applications](/docs/decisions/006-customer-reservations-frontend.md)
  - [Python FastAPI for Customer Reservation Backend and API Gateway](/docs/decisions/007-customer-reservations-backend.md)
  - [Travel "Agent" Using GenAI](/docs/decisions/008-agentic-travel-copilot.md)
  - [Adopt Medallion Architecture using Iceberg format for Data Lake](/docs/decisions/009-medallion-data-lake.md)
  - [Use Databricks for ETL, ML Experimentation, and Model Serving](/docs/decisions/010-databricks-for-etl-mlflow-inference.md)
  - [Demand Forecasting with LightGBM Machine Learning Model](/docs/decisions/011-forecast-model.md)
  - [Google OR-Tools for Vehicle Redistribution Optimization](/docs/decisions/012-redistribution-optimizer-algo.md)
  - [Pydantic AI for our Agentic Framework Foundation](/docs/decisions//013-agentic-framework.md)
  - [Create Platform Services for Shared Capabilities](/docs/decisions/014-platform-services.md)

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
2. [Next.js + React Native with Monorepo for Operations Applications](/docs/decisions/002-operations-system-frontend.md)
3. [Python FastAPI for Operations Backend and API Gateway](/docs/decisions/003-operations-system-backend.md)
4. [Extensible External Data Provider Architecture](/docs/decisions/004-external-data-providers.md)
5. [Agentic Dispatch Workflow Using GenAI](/docs/decisions/005-agentic-dispatch-workflow.md)
6. [Next.js + React Native with Monorepo for Customer Reservations Applications](/docs/decisions/006-customer-reservations-frontend.md)
7. [Python FastAPI for Customer Reservation Backend and API Gateway](/docs/decisions/007-customer-reservations-backend.md)
8. [Travel "Agent" Using GenAI](/docs/decisions/008-agentic-travel-copilot.md)
9. [Adopt Medallion Architecture using Iceberg format for Data Lake](/docs/decisions/009-medallion-data-lake.md)
10. [Use Databricks for ETL, ML Experimentation, and Model Serving](/docs/decisions/010-databricks-for-etl-mlflow-inference.md)
11. [Demand Forecasting with LightGBM Machine Learning Model](/docs/decisions/011-forecast-model.md)
12. [Google OR-Tools for Vehicle Redistribution Optimization](/docs/decisions/012-redistribution-optimizer-algo.md)
13. [Pydantic AI for our Agentic Framework Foundation](/docs/decisions//013-agentic-framework.md)
14. [Create Platform Services for Shared Capabilities](/docs/decisions/014-platform-services.md)
