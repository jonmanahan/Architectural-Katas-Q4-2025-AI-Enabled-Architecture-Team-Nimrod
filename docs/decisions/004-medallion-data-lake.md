# Adopt Medallion Architecture with Apache Iceberg for Data Lake

## Context and Problem Statement

Our Data Intelligence Platform system needs a structured approach to organize and process data from various sources (external data providers, operational systems, customer reservations). Data arrives in different formats and quality levels, and needs to be progressively refined for analytics and ML experimentation. How should we organize our data lake to support this progression while enabling efficient querying and data management?

## Considered Options

* Option 1: Data lake with ad-hoc organization
* Option 2: Medallion architecture (Bronze/Silver/Gold) with Parquet format
* Option 3: Medallion architecture (Bronze/Silver/Gold) with Apache Iceberg format
* Option 4: Traditional data warehouse approach

## Decision Outcome

Chosen option: "Option 3: Medallion architecture with Apache Iceberg format", because it provides clear data quality progression through layers, while Iceberg enables ACID transactions, schema evolution, time travel, and efficient updates and deletes that Parquet lacks.

### Medallion Architecture Layers

**Bronze Layer (Raw)**
- Raw data ingested from all sources
- Minimal transformation, preserves source format
- Append-only, immutable historical record
- Purpose: Source aligned for reprocessing

**Silver Layer (Cleaned)**
- Validated, deduplicated, and standardized data
- Conformed schemas across similar sources
- Data quality rules applied
- Purpose: Reliable source for analytics

**Gold Layer (Business-Level)**
- Aggregated, feature store data
- Optimized for consumption via BI, ML models
- Purpose: Consumer tailored datasets

### Apache Iceberg Benefits

- **ACID transactions**: Reliable concurrent reads and writes
- **Schema evolution**: Add, drop, rename columns without rewriting data
- **Time travel**: Query historical versions of data
- **Partition evolution**: Change partitioning strategy without data rewrite
- **Efficient updates/deletes**: Critical for GDPR compliance and data corrections
- **Hidden partitioning**: Users don't need to know partition structure

## Consequences

### Positive

* Clear data quality progression from raw to consumer ready
* Iceberg enables reliable data operations and efficient processing for big data systems
* Time travel supports reproducible ML experiments and debugging
* Schema evolution reduces breaking changes for consumers
* Strong ecosystem support including Spark, Flink, Trino
* Partition evolution allows optimization without migration
* Better performance than traditional file formats for analytical queries

### Negative

* Learning curve for teams unfamiliar with medallion pattern
* Additional storage costs for maintaining multiple layers
* Iceberg adds complexity compared to simple Parquet files
* Requires Iceberg-compatible query engines
* More infrastructure to manage
