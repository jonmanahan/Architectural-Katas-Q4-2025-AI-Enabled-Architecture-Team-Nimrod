---
status: "accepted"
date: 2025-10-22
decision-makers: [Nimrod Architecture Team]
consulted: [Data Science Team, Platform Engineering Team]
informed: [Operations and Customer Reservation Engineering Teams]
---

# Use Databricks for ETL, ML Experimentation, and Model Serving

## Context and Problem Statement

Our Data Platform system requires integrated capabilities for data processing with ETL pipelines, ML experimentation tracking for data scientists, and model registry with serving infrastructure for production deployment. We need to decide whether to adopt a unified managed platform or build a custom solution using open source tools. How should we architect our data intelligence platform to support our medallion architecture data lake, collaborative ML experimentation, and production-grade model deployment?

## Considered Options

- Option 1: Databricks Data Intelligence Platform
- Option 2: AWS SageMaker and AWS Glue
- Option 3: Custom solution using open source tools like self-hosted Flink, Spark, MLflow, and custom model serving

## Decision Outcome

Chosen option: "Option 1: Databricks Data Intelligence Platform", because it provides comprehensive integration across data engineering and ML workflows, native support for our medallion architecture and Iceberg format, industry-standard MLflow for experimentation, and multi-cloud portability to avoid vendor lock-in. While it has higher costs than a custom solution, the reduced operational overhead and faster time-to-value justify the investment.

## Pros and Cons of the Options

### Option 1: Databricks Data Intelligence Platform

- Good, because single platform reduces operational complexity and tool sprawl across data and ML teams
- Good, because native MLflow 3.0 integration offers industry-standard experiment tracking with open source foundation
- Good, because supports for Apache Iceberg and Delta Lake table formats
- Good, because includes data catalog for governance, lineage, and data quality
- Good, because doesn't lock you into a cloud vendor
- Good, because collaborative notebooks enable teamwork between data engineers and data scientists
- Good, because framework agnostic supporting TensorFlow, PyTorch, Scikit-learn, LightGBM, and all major LLMs.
- Good, because large open source community and extensive third-party integrations
- Good, because managed infrastructure with auto-scaling reduces operational burden
- Bad, because higher cost compared to custom open source solution or cloud-native alternatives and can become expensive at scale without careful optimization
- Bad, because learning curve for teams unfamiliar with Databricks platform and Spark ecosystem
- Bad, because Databricks-specific create vendor lock-in despite open source foundation
- Bad, because additional vendor relationship to manage beyond cloud provider
- Bad, because of configuration complexity with cluster sizing and job orchestration

### Option 2: AWS SageMaker

- Good, because seamless integration with AWS services
- Good, because advanced model serving with low latency endpoints and autoscaling
- Good, because mature DevOps practices including canary deployments, A/B testing, and rollback capabilities
- Good, beause fully managed infrastructure abstracts complexity from data science teams
- Good, because managed MLflow tracking server available for experiment compatibility
- Good, because great documentation and large enterprise customer base
- Good, because serverless inference options reduce costs for variable workloads
- Good, because AWS Glue also leverages Spark
- Bad, AWS vendor lock-in with proprietary infrastructure and deployment formats
- Bad, because need to piece together a myriad of AWS services to get ETL and data engineering capabilities as comprehensive than Databricks
- Bad, because requires separate EMR clusters for distributed processing
- Bad, because complex pricing model can be difficult to predict and optimize
- Bad, because only Iceberg support through Athena rather than native integration
- Bad, because weaker collaboration features for data science teams
- Bad, because model registry approval workflow limitations
- Bad, because learning curve for teams not experienced with AWS ecosystem
- Bad, because less suitable for medallion architecture data lake pattern

### Option 3: Custom Solution using Open Source Stack

- Good, because maximum cost optimization with no platform licensing fees
- Good, because complete control over infrastructure and technology choices
- Good, because zero vendor lock-in, can run anywhere including on-premises
- Good, because flexibility to use exactly the tools and versions needed
- Good, because can leverage open source innovation directly without waiting for platform adoption
- Good, because team builds deep expertise in underlying technologies
- Good, because can customize every aspect of the stack for specific requirements
- Good, because open source MLflow provides industry-standard experiment tracking
- Good, because freedom to choose best-of-breed model serving solutions
- Bad, because significant engineering effort required to build, integrate, and maintain all components
- Bad, because need dedicated platform engineering team to manage infrastructure and operations
- Bad, because responsibility for security patches, upgrades, and disaster recovery
- Bad, because no unified support, must rely on community or multiple vendor relationships
- Bad, because integration complexity between Flink, Spark, MLflow, storage, and serving layers
- Bad, because operational overhead for monitoring, logging, and observability across stack
- Bad, because longer time-to-value as team builds out infrastructure and tooling
- Bad, because requires specialized skills in infra maintanence
- Bad, because potential reliability issues without mature automation and testing
- Bad, because may ultimately cost more when factoring in engineering time and opportunity cost
