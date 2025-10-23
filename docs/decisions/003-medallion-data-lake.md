---
status: "accepted"
date: 2025-10-22
decision-makers: [Nimrod Architecture Team]
consulted: [Data Science Team, Platform Engineering Team]
informed: [Operations and Customer Reservation Engineering Teams]
---

# Adopt Medallion Architecture using Iceberg format for Data Lake

## Context and Problem Statement

Our Data Intelligence Platform system needs a structured approach to organize and process data from various sources (external data providers, operational systems, customer reservations). Data arrives in different formats and quality levels, and needs to be progressively refined for analytics and ML experimentation. How should we organize our data lake to support this progression while enabling efficient querying and data management?

## Considered Options

* Option 1: Data lake with ad-hoc organization
* Option 2: Medallion architecture with Parquet format
* Option 3: Medallion architecture with Apache Iceberg format
* Option 4: Traditional data warehouse approach

## Decision Outcome

Chosen option: "Option 3: Medallion architecture with Apache Iceberg format", because it provides clear data quality progression through layers, while Iceberg enables ACID transactions, schema evolution, time travel, and efficient updates and deletes that Parquet lacks.

### Medallion Architecture Layers

**Bronze Layer: Raw**
- Raw data ingested from all sources
- Minimal transformation, preserves source format
- Append-only, immutable historical record
- Purpose: Source aligned for reprocessing

**Silver Layer: Cleaned**
- Validated, deduplicated, and standardized data
- Conformed schemas across similar sources
- Data quality rules applied
- Purpose: Reliable source for analytics

**Gold Layer: Curated**
- Aggregated, feature store data
- Optimized for consumption via BI, ML models
- Purpose: Consumer tailored datasets

### Apache Iceberg Benefits

- ACID transactions: Reliable concurrent reads and writes
- Schema evolution: Add, drop, rename columns without rewriting data
- Time travel: Query historical versions of data
- Efficient updates and deletes: Critical for GDPR compliance and data corrections
- Better partitioning: Users don't need to know partition structure and can change paritioning strategy without data rewrite

## Consequences

* Good, because clear data quality progression from raw to consumer ready
* Good, because Iceberg enables reliable data operations and efficient processing for big data systems
* Good, because time travel supports reproducible ML experiments and debugging
* Good, because schema evolution reduces breaking changes for consumers
* Good, because strong ecosystem support including Spark, Flink, Trino
* Good, because partition evolution allows optimization without migration
* Good, because better performance than traditional file formats for analytical queries
* Bad, because learning curve for teams unfamiliar with medallion pattern
* Bad, because additional storage costs for maintaining multiple layers
* Bad, because Iceberg adds complexity compared to simple Parquet files
* Bad, because requires Iceberg-compatible query engines
* Bad, because more infrastructure to manage
