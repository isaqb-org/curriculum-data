# Motivation and architectural challenges

## Learning goals

* Give an introduction to the field.
* Know motifs to handle data as "first class citizen".
* Delimitation to other iSAQB-Modules.
* Know types of data analyses
    * Descriptive
    * Diagnostic
    * Predictive
    * Prescriptive
* exploratory vs confirmatory (Mode)

[TODO(RJ): BigData Buzzword]

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
* Understand how data can be held consistent in different environments (distributed, centralized)
    * ACID (Atomicity, Consistency, Isolation, Durability)
    * BASE (BasicallyAvailable, SoftState, Eventually Consistent)
    * [optional: Strong eventual consistency]

[TODO(RJ): Understand impact of essential complexity of source data. Understand higher relevance of architectural decisions, if essential complexity of source data is lower.]

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
    * Micro batch processing
    * Stream processing
    * Event driven architecture
* Understand what data lineage is, when it is needed and how to implement it.
* Know ways how to detect and handle data errors during the ingestion.

# Storage [HOLGER]

## Terms and concepts

Retention time, latency, cloud storage, data lake, data mesh, data warehouse, on premise storage, distributed file systems.

## Learning goals

* Storage system as an ingestion endpoint.
* Schema on write vs schema on read.
* Memory hierarchy: trade-off between data volumen, access time and power consumption.
* Data representations: algorithms require specific data structures. The choice of structure has impact on the storage layout (=> griffiger
  formulieren)
    * structured, semi structured, unstructured
    * normalized vs denormalized
    * multidimensional (star, snowflake)
    * time series
    * text, binary
    * File system, Database
    * graph
* Understand that there exists a strong interdependency between storage and processing.
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
        * Landing Zone - raw, unstructured data
        * Staging Zone - data-integration (semi-structured and processed data) from landing zone or external data-sources
        * Curated Zone - similarities to a big-data-warehouse
        * Analytic Zone - processing, analysis (ML, etc.)
    * Meta-data-mangemant (data-catalog) [if not available, data-mud]
        * conceptual model for locating, generation of indices, versioning and description
        * generation of links and relations between data
    * Data-mangement-process between data-producers and domain-experts to collect information about the data-integration
    * Lake-security: enormous amount of data from lots of sources (encryption, authorization, authentication)
    * Technical storage formats: Parquet, Avro, ORC
    * Distributed file system: HDFS, Hadoop, Ceph, Lustre
    * Cloud storage: S3, Azure Blob, Google ?, IBM ?

* Understand that different types of workload require different adopted storage structures.
* Know that multiple representations of data can be stored.
* Data lineage helps to trace the origins of the transformed representations.

# Query and processing

## Terms and concepts

## Learning goals

* Know different types of query and processing languages and their characteristics:
    * Relational query languages
    * Graph query languages
    * Other (embedded) domain specific languages like R, matlab.
* Know examples of query languages, e.g.
    * SQL
    * MDX
    * R, Julia
    * Spark
    * Query generation
* Know the impact of different data representations on the performance of algorithms and ease of implementation ("impedance mismatch").
* Processing
    * Batch
    * Micro-Batch
    * Stream
* Data oriented programming principles:
    * Separate code from data
    * Represent data entities with generic data structures
    * Data is immutable
* As-is vs As-was (Abbildung der Historie: SCD)
* Indexing, Aggregation, Grouping, Filtering, Pivoting, Windowing, Sorting, Map-Reduce
* Interactive vs implemented
* drill down, up, across, slice and dice
* Roles
* Scalability
* Participants should know the different intents of data analysis:
    * Data analysis as means to understand the past.
    * Data analysis as tool to create and test hypothesis.
    * Data analysis for model based prediction.
    * Data analysis as a tool to assess the quality of data.
* Participants should understand the specific quality requirements relevant for different data analysis uses cases.
* They should know the typical architectures that support the different analytical style.
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
* Possible ways to transfer research model into production.

# Data consumer

## Terms and concepts

Predictive and descriptive data analysis, Data science, BI, Dashboards.

## Learning goals

* Executing queries and data models against stored data.
* Data based prediction and planning
    * Models of real world systems can be used to predict future behaviour.
    * Based on the predicted behaviour organizations can implement actions.
    * Integration patterns of predictive models and automated decisions systems in control loops.
* Know the different categories of data analysis tools:
    * Query engines
    * Statistical analysis
    * Machine learning
* Know typical uses cases for ML and statistical analysis. .
* Search-enginges (special indices)

# DataOps [LARYSA]

## Terms and concepts

DataOps definition. DataOps Components: Catalog/Registry - Metadata Store, Movement/ETL - Data Pipelines, Alignment/Unification - Creating Consistency
in Data, Data Integration, Publishing Data - (DaaS), Data Feedback, Data Governance.

## Learning goals

* Understand the need for automation of data ingestion and processing.
    * Reproducible results
    * Understandability
    * Less errors
    * Cost reduction
* Know the DataOps Practices.
    * Agile process application - short time-to-delivery and responsiveness to change
    * Implementint everything in code (e.g. host configuration, network configuration, automation, gathering and publishing test results, service
      installation * and startup, error handling)
    * Applying software engineering best practices - using version control with branching and merging, automated regression testing of everything,
      clean code design and factoring, clear comments
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
  [TODO(RJ): DWH appliances , high end data processing systems]

# Crosscutting concerns

## Terms and concepts

Metadata Management, Data Quality Assurance, Security, Data and Systems Governance, Data and Systems Oberservability

## Learning goals

* Understand metadata and why it is important.
    * Understand data profiling as a process of gathering metadata.
    * Know the representation form of metadata
* Know the metadata categories for data management:
    * Basic - size, format, aliases, last modified time, access control lists
    * Content-based - schema, number of records, single-column and inter-column metadata, data fingerprint, key field, frequent tokens, similar
      datasets
    * Provenance - reading jobs, writing jobs, downstream datasets, upstream datasets
    * User-supplied - description, annotations
    * Team and project - project description, owner team name
    * Temporal - change history
* Know existing metadata systems and frameworks.

* Understand data quality requirements, assessment and monitoring:
    * Quantitative dimensionen of data quality as foundation for metrics:
        * Intrinsic dimensions: Accuracy, Lineage, Structural/Syntactic Consistency, Semantic Consistency, Outliers. Contextual (Inter-Column)
          Dimensions: Completeness, Consistency, Timeliness.
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



# Decentralized Data Architectures: Data Mesh
Teaching: 90 min  
Exercises: 60 min

This part provides a motivation and introduction to Data Mesh. 
The participants will learn when a decentralised data architecture is appropriate.
Further, they will learn about the four foundational principles of Data Mesh:
Domain Ownership, Data as a Product, Self-serve Data Platform, and Federated Computational Governance.


## Terms and concepts
Data Mesh, Domain-driven Design, Bounded Context, Context Mapping, Data as a Product, Product Thinking, Self-serve Data Platform, Federated Computational Governance, Team Topologies


## Learning goals

LG X-1: Address the Issues of Centralised Data Architectures

* The participants know and understand the distinction between analytical and operational data models.
* The participants understand the scalability issues of central data teams.
* The participants understand the mismatch of a central data team and decentralised domain teams.


LG X-2: Domain Ownership

* The participants know relevant concepts of strategic domain-driven design such as domains, subdomains, bounded contexts, and context mapping patterns.
* The participants understand that the responsibility of the analytical data and its quality is shifted from the central data team to the particular domain teams.
* The participants know that domain teams own their analytical data.
* The participants know that domain teams serve the domain's analytical data to the rest of the organization.
* The participants know the distinction between three Domain Data Archetypes: source-aligned, aggregate, and consumer-aligned data.
* The participants understand the concept of polyseme as a shared concept across different domains.


LG X-3: Data as a Product

* The participants understand that domain teams provide data to other teams as data products.
* The participants understand that data products are first-class citizens in the system architecture, similar to UI and API products.
* The participants know characteristics of data products: data are discoverable, addressable, trustworthy, self-descriptive, secure, understandable, interoperable, natively accessible, and valuable on their own.
* The participants know the different forms of data products, including datasets, reports, dashboards, ML features or entire ML models.


LG X-4: Self-serve Data Platform

* The participants understand the key concepts of the domain-agnostic data infrastructure as a platform.
* The participants know that the platform is managed by a data platform team.
* The participants know typical components of a data platform, i.e. storage, data pipelines, data catalog, access management, monitoring, visualisation.
* The participants have an idea of existing solutions provided by cloud vendors.


LG X-5: Federated Computational Governance

* The participants know that the governance group, typically called a "guild", consists of representatives of the domain teams and the data platform team.
* The participants know that the governance group agrees on global policies of the data eco-systems, including interoperability, security and compliance.
* The participants understand that the self-serve data platform may support, automate, or enforce the global policies.


## References

1. "Data Mesh in Action" by Jacek Majchrzak, Sven Balnojan, and Marian Siwiak. Manning. Publication in Summer 2022
1. "Data Mesh" by Zhamak Dehghani. O'Reilly Media, Inc. April 2022
1. datamesh-architecture.com
1. "Data Management at Scale" by Piethein Strengholt
1. "Software Architecture: The Hard Parts" by Neal Ford, Mark Richards, Pramod Sadalage, Zhamak Dehghani



# Examples of data processing pipelines

## Learning goals

* Know example requirements that are a good fit for database types (FORMULIERUNG!)
* Know examples of (big) data architectures and possible fields of application
    * Lambda
        * Speed Layer
        * Serving Layer
        * Batch Layer
    * Kappa
    * Data vault
* Views on data [how to model them and which diagram-types are recommended]
