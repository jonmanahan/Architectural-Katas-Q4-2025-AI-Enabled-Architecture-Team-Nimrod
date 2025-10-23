---
status: "accepted"
date: 2025-10-22
decision-makers: [Nimrod Architecture Team]
consulted: [Operations Team, Data Platform Team, Platform Engineering Team]
informed: [Engineering and Product Teams]
---

# Extensible External Data Provider Architecture

## Context and Problem Statement

Our systems need to integrate data from various external sources including traffic APIs, weather services, and other third-party data providers to trigger forecasts and build training data sets. Each data source has different protocols, rate limits, authentication mechanisms, and update frequencies. Some sources support push, while others require polling. How should we architect data ingestion to support multiple external providers while maintaining reliability, observability, and ease of adding new sources?

## Considered Options

* Option 1: Build monolithic data ingestion service handling all external sources
* Option 2: Each consuming system integrates directly with external data providers
* Option 3: Create extensible architecture with specialized data extraction microservices
* Option 4: Use only third-party ETL/integration platforms (e.g., Fivetran, Airbyte)

## Decision Outcome

Chosen option: "Option 3: Create extensible architecture with specialized data extraction microservices", because it provides flexibility to handle diverse integration patterns, allows independent scaling and deployment of data extractors, enables specialization per data source, and supports both polling and push architectures while maintaining a consistent internal interface.

### Core Components

**Data Extraction Microservices**
- Independent microservices, one per external data provider or provider category
- Examples: Traffic Data Extractor, Weather Data Extractor
 - Each service encapsulates provider-specific logic (authentication, rate limiting, data transformation)
- Publishes standardized events/messages to internal data bus

**Scheduling Infrastructure**
- Leverage off-the-shelf infrastructure components for scheduling (e.g., AWS EventBridge scheduled rules, Kubernetes CronJobs)
- Configurable intervals per data source (e.g., traffic every 5 minutes, weather hourly)
- Triggers extraction microservices via events or API calls
- Built-in reliability, monitoring, and managed infrastructure

**Push Notification Gateway**
- Receives push notifications from external providers that support webhooks, websockets, gPRC, etc.
- Authenticates and validates incoming requests
- Routes to appropriate data extraction microservice
- Provides consistent endpoints for external systems

**Event Streaming Platform**
- Central message broker (e.g., Kafka, AWS EventBridge)
- Standardized event schemas for extracted data
- Decouples data extraction from consumption
- Enables multiple consumers and data replay

**Configuration Service**
- Centralized configuration for all data extractors
- API credentials, endpoints, schedules, and feature flags
- Enables runtime configuration changes without redeployment
- Leverage configuration stores in chosen platform (AWS microservices or K8s)

## Consequences

### Positive

* Good, because easy to add new data sources and create new microservice without affecting existing ones
* Good, because leverage managed infrastructure for scheduling reduces operational burden and development time
* Good, because independent scaling based on data volume and extraction frequency per source
* Good, because isolation of failures, issues with one provider don't affect others
* Good, because flexibility to use different tech stacks optimized for specific providers
* Good, because clear ownership and specialization per data source
* Good, because supports both polling and push patterns within unified architecture
* Good, because centralized observability and monitoring of all external integrations
* Good, because rate limiting and retry logic encapsulated per provider
* Good, because easier testing and mocking of external dependencies
* Bad, because increased operational complexity with multiple services to deploy and monitor
* Bad, because need for service discovery and configuration management
* Bad, because potential for inconsistent implementation patterns across extractors
* Bad, because requires standardized event schemas and versioning strategy
* Bad, because additional infrastructure costs for multiple services
* Bad, because need for comprehensive observability across all services
* Bad, because risk of schema evolution challenges as extractors are added