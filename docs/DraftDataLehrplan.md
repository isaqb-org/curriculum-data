# TIMELINE: 1.02.2021 final version

# Motivation and architectural challenges

## Learning goals

* Give an introduction to the field.
* Know motifs to handle data as "first class citizen".
* Delimitation to other iSAQB-Modules.

# Data sources

## Terms and concepts

Data, information, master data, operational data

## Learning goals

* Know the different qualities that characterize data:
  * Correctness
  * Completeness
  * Timeliness
  * Data volume
  * Change rate, stability of information
  * Structured vs unstructured data
  * Data formats
* Know different types of technical data sources and their chacteristics:
  * Data base systems
  * Document management systems
  * File system
  * Logs
  * External APIs (e.g. stock market)
  * SCADA, IoT systems
* Understand the need to gather data from different sources.
* Be aware that different sources may provide conflicting data about same entity.
* Know trade-off and implications of unified data model for all sources vs. one model per source.
* Know means to assess the data quality of different sources.
* Understand how organizational and legal frameworks influence availability and quality of data.
* Be aware that data quality may change over time and needs to be monitored.
* Understand what metadata is and how it helps to retrieve information from data.
* Know different solutions to manage metadata.
* Understand the impact of legal and organizational constraints on data accessibility.
* Understand that the nature of data the system has to deal with is a major driver for architectural decisions.

# Ingestion and transformation

## Terms and concepts

ETL, ELT, batch processing, stream processing, event driven architecture, data lineage

## Learning goals

* Understand the typical requirements that determine architectural decisions.
  * Data volume
  * Data latency, response time
  * Data format/model
  * Stability of data model
  * Number of sources
  * Availability of sources
* Understand the difference between ETL and ELT as well as their impications and respective pros and cons.
* Know about possibilities and implications of data transformation in the ingestion pipeline.
* Know typical architectures and technologies for data ingestion and make informed choices.
  * Batch systems, ETL, ELT
  * Stream processing
  * Event driven architecture
* Understand what data lineage is, when it is needed and how to implement it.
* Know ways how to detect and handle data errors during the ingestion.

# Storage

## Terms and concepts

Retention time, latency, cloud storage, data lake, data mesh, data warehouse, on premise storage, distributed file systems.

## Learning goals

* Storage system as an ingestion endpoint
* Schema on write vs schema on read.
* Memory hierarchy: trade-off between data volumen, access time and power consumption.
* Characteristics of classical database systems.
  * Combination of storage and query processing.
  * Focus on one query and processing model.
* Different data base types:
  * Relational DB
  * Graph DB,
  * Column oriented DB,
  * Document DB
* Database as a (cloud) service
* Data lake storage
  * Separation of storage and processing engine
  * Technical storage formats: Parquet, Avro, ORC
  * Distributed file system: HDFS, Ceph, Lustre
  * Cloud storage: S3, Azure Blob, Google ?, IBM ?
* Data Mesh
  * When Centralization is an issue: DWH and Data Lake
  * Data Mesh Paradigm Shift Principles:
    * Decentralization (Decentralized Ownership)
      * Domain-driven data decomposition
      * Domain data is a first-class concern
      * Data pipelines are second class
    * Product Thinking (Success Criteria: Decreased Lead time to discover and consume data product)
      * Domain data as a product (data is consumed by Data Scientists)
      * Characteristics: Data is discoverable, addressable, trustworthy (SLO), self-described, secure
      * Publishing output data points (instead of getting data trough centralized data pipelines)
      * Role: Domain Data Product Owner
    * Self-service Infrastructure as a Platform (Success Criteria: Reduced lead time to create new secure and discoverable data products)
      * Distributed
      * Data Pipelines are domain-agnostic (like cloud platforms)
      * DataOps (Data Product CI/CD)
      * Metadata
    * Federated Ecosystem Governance
      * Encryption
      * ACLs
      * Regulations



* Understand that different types of workload require different adopted storage structures.
* Know that multiple representations of data can be stored.
* Data lineage helps to trace the origins of the transformed representations.

<<<<<<< HEAD
# Query and Processing
=======
# Data analysis
>>>>>>> a0984112f3688ff895d2c98de660fa795dafcd8e

## Terms and concepts

Model, hypothesis, test, prediction, descriptive statistics

## Learning goals

<<<<<<< HEAD
* Types of data analysises (-> Motivation and architectural challenges)
  * Descriptive
  * Diagnostic
  * Predictive
  * Prescriptive
* exploratory vs confirmatory (Mode) (-> Motivation and architectural challenges)
* Suitable data representations (references to storage)
  * structured, semi structured, unstructured
  * normalized vs denormalized
  * multidimensional (star, snowflake)
  * time series
  * text, binary
  * File system, Database
  * graph
* Processing
  * Batch
  * Micro-Batch
  * Stream
* As-is vs As-was (Abbildung der Historie: SCD)
* Indexing, Aggregation, Grouping, Filtering, Pivoting, Windowing, Sorting, Map-Reduce
* Query languages
  * SQL
  * MDX
  * R, Julia
  * Spark
  * Query generation
* Interactive vs implemented
* drill down, up, across, slice and dice

* Roles
* Scalability
* Data analysis as a tool to assess the quality of data.
* Use the data pipeline to build models of real world systems from data analysis.
=======
* Participants should know the different intents of data analysis:
  * Data analysis as means to understand the past.
  * Data analysis as tool to create and test hypothesis.
  * Data analysis for model based prediction.
  * Data analysis as a tool to assess the quality of data.
* Participants should understand the specific quality requirements relevant for different data analysis uses cases.
* They should know  the typical architectures that support the different analytical style.
>>>>>>> a0984112f3688ff895d2c98de660fa795dafcd8e
* Understand that work with data can be explorative or repetitive.
  * Building new models, derive meaningful characteristic values.
  * Regular measurement of characteristic model parameters, KPIs.
* Systems for exploratory data analysis:
  * interactive environments
  * working on smaller subsets of data
  * results in research prototype of algortithm and modes
* Systems for regular analysis
  * Reporting systems
  * KPIs
  * Dashboards
<<<<<<< HEAD
* Possible ways to transfer research model into production.

# Query engines 
=======
* Possible ways to to transfer research models into production.
>>>>>>> a0984112f3688ff895d2c98de660fa795dafcd8e

# Query and processing engines

## Terms and concepts

## Learning goals

* Know different types of query and processing languages and their characteristics:
  * Relational query languages
  * Graph query languages
  * Other (embedded) domain specific languages like R, matlab.

#  Data consumer

## Terms and concepts

Predictive and descriptive data analysis, Data science, BI, Dashboards.

## Learning goals

* Executing queries and data models against stored data.
* Data based prediction and planning
    * Models of real world systems can be used to predict future behaviour.
    * Based on the predicted behaviour organizations can implement actions.
    * Integration patterns of predictive models and automated decisions systems in control loops.

# Systems for data analytics and model creation

## Terms and concepts

## Learning goals

* Know the different categories of data analysis tools:
  * Query engines
  * Statistical analysis
  * Machine learning
* Know typical uses cases for ML and statistical analysis.
* Understand that tools
.

# Data ops

## Terms and concepts

DataOps definition. DataOps Components: Catalog/Registry - Metadata Store, Movement/ETL - Data Pipelines, Alignment/Unification - Creating Consistency in Data, Data Integration, Publishing Data - (DaaS), Data Feedback, Data Governance.

## Learning goals

* Understand the need for automation of data ingestion and processing.
  * Reproducible results
  * Understandability
  * Less errors
  * Cost reduction
* Know the DataOps Practices.
  * Agile process application - short time-to-delivery and responsiveness to change
  * Implementint everything in code (e.g. host configuration, network configuration, automation, gathering and publishing test results, service installation * and startup, error handling)
  * Applying software engineering best practices - using version control with branching and merging, automated regression testing of everything, clean code design and factoring, clear comments
  * Maintaining multiple environments (keep development, acceptance testing, and production environments separate)
  * Integrating the toolchains - everything needs to work together.
  * Testing - automated testing to make changes quickly and find problems early.

* Know tools for definition and execution of data transformation.


# Infrastructure

## Terms and concepts

## Learning goals

* Understand the specific requirements on infrastructure:
  * Storage capacity
  * Processing
  * Network
* Cloud vs on premise infrastructure
* Processor options: CPU, GPU, TPU
* Parallelization middleware like MPI

# Crosscutting concerns

## Terms and concepts
Metadata Management, Data Quality Assurance, Security, Data and Systems Governance, Data and Systems Oberservability

## Learning goals

* Understand metadata and why it is important.
  * Understand data profiling as a process of gathering metadata.
  * Know the representation form of metadata
* Know the metadata categories for data management:
  * Basic - size, format, aliases, last modified time, access control lists
  * Content-based - schema, number of records, single-column and inter-column metadata, data fingerprint, key field, frequent tokens, similar datasets
  * Provenance - reading jobs, writing jobs, downstream datasets, upstream datasets
  * User-supplied - description, annotations
  * Team and project -  project description, owner team name
  * Temporal - change history
* Know existing metadata systems and frameworks.

* Understand data quality requirements, assessment and monitoring:
  * Quantitative dimensionen of data quality as foundation for metrics:
      * Intrinsic dimensions: Accuracy, Lineage, Structural/Syntactic Consistency, Semantic Consistency, Outliers.
      Contextual (Inter-Column) Dimensions: Completeness, Consistency, Timeliness.
  * Qualitative dimensions: Authoritative (trusted) sources, Trust, Anonymity/Privacy/Governance compliance, Standards and Policies.

* Understand data cleaning approaches: Rule-based, Missing values imputation, Duplicate detection and consolidation.
* Understand the security and data governance aspects of data management:
  * Archivierung
  * Einschlägige Gesetze und Verordnungen (DSGVO, Anonymisierung, Pseudonymisierung)
  * Geo-Fencing
  * Schutzklassen und Sicherheitsstufen

* Understand the data observability, monitoring, traceability, logging:
  * Dashboards
  * Logging



# Examples of data processing pipelines

## Learning goals

* Know example requirements that are a good fit for database types (FORMULIERUNG!)
* Know examples of (big) data architectures and possible fields of application
    * Lambda
    * Kappa
    * Data vault
