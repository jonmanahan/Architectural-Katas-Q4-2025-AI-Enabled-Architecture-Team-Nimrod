# Team Nimrod's MobilityCorp AI Enabled Architecture

![Tower of Babel](/assets/tower-of-babel.png "tower of babel")


## Table of Contents
- [Overview: Transforming Urban Mobility Through Intelligent Architecture](#overview-transforming-urban-mobility-through-intelligent-architecture)
  - [Solving Vehicle Availability Through Predictive Demand](#solving-vehicle-availability-through-predictive-demand)
  - [Optimizing Fleet Redistribution with Advanced Algorithms](#optimizing-fleet-redistribution-with-advanced-algorithms)
  - [Enhancing Customer Experience Through Intelligent Agents](#enhancing-customer-experience-through-intelligent-agents)
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
- Proposed Future State ADRs
  - [Autonomous-Driving Ride Delivery Agent](/docs/proposals/docs/proposals/001-ride-delivery-agent.md)


## Overview: Transforming Urban Mobility Through Intelligent Architecture
MobilityCorp operates a multi-modal urban mobility service across the European Union, offering short-term rentals of electric scooters, e-bikes, cars, and vans through an on-demand mobile platform. Despite serving a growing market for sustainable "last-mile" transportation, the company faces three critical challenges that directly erode revenue, customer trust, and reliance: 

1. Vehicles are unavailable when customers need them
1. Batteries fail mid-trip with unreliable vehicle charges
1. Customers primarily use the service only for ad-hoc trips rather than as a reliable option for daily commutes

These problems stem from reactive operations rather than intelligent, data-driven decision making. Our proposed architecture addresses these interconnected challenges through a comprehensive AI-enabled system that transforms MobilityCorp from a reactive fleet operator into a predictive mobility platform, fundamentally improving operational efficiency, customer satisfaction, and revenue growth.

### Solving Vehicle Availability Through Predictive Demand

The core problem of vehicle unavailability stems from poor demand forecasting and inefficient fleet positioning. Our architecture implements a machine learning solution using the LightGBM algorithm to predict demand patterns across different locations, times, and conditions. This model ingests historical usage data, weather patterns, local events, and real-time operational metrics through a medallion data architecture built on Apache Iceberg format. By accurately forecasting where and when customers will need vehicles, MobilityCorp can proactively position inventory rather than reactively responding to shortages. The system processes data through bronze, silver, and gold layers using Databricks, ensuring clean, validated information feeds the forecasting model. This predictive capability transforms vehicle availability from a pain point into a competitive advantage, directly increasing booking conversion rates and customer satisfaction.

### Optimizing Fleet Redistribution with Advanced Algorithms

Even with accurate demand predictions, MobilityCorp must physically move vehicles to meet anticipated needs while minimizing operational costs. Our architecture leverages Google OR-Tools, a powerful constraint optimization library, to solve the vehicle routing problem. The system considers multiple variables including vehicle battery levels, current locations, predicted demand hotspots, driver availability, and time windows to generate optimal redistribution routes. This goes beyond simple geographic balancing by incorporating battery charge states, ensuring vehicles arrive at high-demand locations fully charged and ready for use. The optimizer runs continuously, adapting to real-time conditions and generating efficient dispatch instructions for operations teams. By dramatically reducing the time and cost of fleet rebalancing while ensuring vehicles are where customers need them, this component directly improves both operational margins and service reliability.

### Enhancing Customer Experience Through Intelligent Agents

The third dimension of our solution addresses customer engagement through agentic AI workflows built on the Pydantic AI framework. We implement two specialized agents: an agentic dispatch system that intelligently manages vehicle assignments and operations, and a travel copilot that helps customers plan multi-modal journeys integrating MobilityCorp vehicles with other transportation options. The dispatch agent autonomously handles complex decision making around vehicle assignments, maintenance scheduling, and exception handling, reducing manual operations overhead while improving response times. The travel agent provides personalized journey planning, suggesting optimal combinations of scooters, bikes, cars, and public transit based on trip requirements, weather, and real-time availability. These AI agents transform customer interactions from transactional bookings into assisted mobility experiences, building the daily usage habits that drive long-term customer value. Together with the predictive demand and optimization systems, these agents complete an architecture that doesn't just solve today's operational problems but positions MobilityCorp as an intelligent mobility platform capable of competing in tomorrow's urban transportation landscape.

This AI-enabled architecture represents a fundamental shift from reactive operations to predictive intelligence. By combining machine learning forecasting, mathematical optimization, and autonomous agents within a robust data platform, MobilityCorp can systematically address the root causes of customer dissatisfaction while building sustainable competitive advantages in operational efficiency and user experience.


## Meet the Nimrods
We are team Nimrod, named after history's most ambitious architect who looked at the plains of Babylon and decided to build a tower to the heavens. While his Tower of Babel project ended with some unforeseen communication challenges (divine intervention will do that), we embrace his spirit of audacious thinking. Like our namesake, we coordinate complex systems and reach for the sky, fully aware that ambitious architectural projects sometimes end with everyone scattered and confused. Nimrod was humanity's first documented case of "I can totally manage this complex project," and that optimistic overconfidence lives on in every architect tackling seemingly impossible challenges. We're just hoping our tower reaches a bit higher than his did.

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

### Future State Proposed ADRs
1. [Autonomous-Driving Ride Delivery Agent](/docs/proposals/docs/proposals/001-ride-delivery-agent.md)