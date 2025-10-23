# Features of MobilityCorp Platform

## Operations (Ops) System Features

1. **Ops System Single-Page Application (SPA)**
   - Next.js web application for ops staff to manage vehicle reservations and administrative workflows.
2. **Ops System Cross-Platform Mobile Application**
   - React Native cross-platform mobile app for field technicians performing maintenance and redistributions with GPS navigation.
3. **Ops API Gateway**
   - AWS API Gateway providing VPC-restricted access for internal ops traffic with security and rate limiting.
4. **Admin API**
   - Python FastAPI service for CRUD operations on customer reservations and operational data.
5. **Dispatch Agent Orchestrator**
   - GenAI agentic workflow that provides conversational dispatch recommendations with human-in-the-loop approval.
6. **Dispatch Recommender Agent**
   - LLM agent that evaluates and recommends next dispatch assignments for field operators.
7. **Feedback Agent**
   - LLM agent that enables operators to review, question, and negotiate AI recommendations conversationally.
8. **Dispatch Manager Agent**
   - LLM agent that executes approved dispatch plans and updates operator assignments.
9. **Ops Database**
   - PostgreSQL database storing ops data and demand forecasts.
10. **External Data Providers**
    - Component for historical data download and scheduled ingestion from traffic, weather, and event sources.

## Customer Reservation Features

11. **Customer Reservations SPA**
    - Next.js web application with Tailwind CSS for vehicle reservations via web browsers.
12. **Customer Reservations Cross-Platform Mobile Application**
    - React Native cross-platform mobile app with Expo for iOS and Android providing NFC unlock, GPS tracking, and photo uploads.
13. **Customer Reservations API Gateway**
    - AWS API Gateway providing public access for customer traffic with DDoS protection, rate limiting, and WebSocket support.
14. **Reservation API**
    - Python FastAPI service for CRUD operations on customer vehicle reservations.
15. **Travel Agent Orchestrator**
    - GenAI agentic workflow that assists customers with trip optimization and route planning through conversational interface.
16. **Route Planner Agent**
    - LLM agent that creates optimal route plans based on customer context and preferences.
17. **Route Optimizer Agent**
    - LLM agent that optimizes routes using real-time traffic, weather, and incident data.
18. **Route Judge Agent**
    - LLM agent that evaluates route recommendations and suggests alternatives for optimization.
19. **Reservation Agent**
    - LLM agent that executes reservation changes on behalf of customers with confirm-before-act validation.
20. **Reservation Database**
    - PostgreSQL database storing customer reservation information.

## Data Intelligence Platform Features

21. **ETL Platform**
    - Databricks Spark-based data engineering system transforming data through medallion architecture.
22. **ML/AI Experimentation Platform**
    - Databricks collaborative notebooks with MLflow for building datasets, training, logging, and registering ML models.
23. **Data Lake**
    - Apache Iceberg medallion architecture with Bronze, Silver, and Gold layers for progressive data refinement.
24. **Model Registry**
    - Databricks MLflow model registry for versioned storage of machine learning models.
25. **Model Inference Service**
    - Databricks Model Serving providing REST API endpoints for real-time ML model inference.
26. **Data Extraction Microservices**
    - Independent microservices for each external data provider with standardized event publishing to data platform.
27. **LightGBM Demand Forecasting Model**
    - Gradient boosting ML model predicting vehicle demand by zone using weather, events, and historical patterns.
28. **Google OR-Tools Vehicle Redistribution Optimizer**
    - Algorithmic solver for capacitated vehicle routing with time windows to optimize fleet redistribution.

## Platform Services

29. **Authentication and Authorization Service**
    - Manages user identity, session management, MFA, and role-based access control for customers and operators.
30. **Notification Service**
    - Multi-channel notification delivery for email, SMS, and push notifications with template management and retry logic.
31. **Payment Processing Service**
    - Secure payment handling with Stripe and PayPal integration for per-minute rental billing and fines.

## AI Agent Framework

32. **Pydantic AI Framework**
    - Type-safe agentic framework with built-in Pydantic Evals for testing, Pydantic Logfire for observability, and model-agnostic LLM support.
