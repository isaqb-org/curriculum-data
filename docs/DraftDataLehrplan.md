

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

Retention time, cloud storage, data lake, data warehouse, on premise storage, distributed file systems.

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
* Understand that different types of workload require different adopted storage structures.
* Know that multiple representations of data can be stored.
* Data lineage helps to trace the origins of the transformed representations.

# Data analysis 

## Terms and concepts

## Learning goals

* Data analysis as means to understand the past.
* Data analysis as a tool to assess the quality of data.
* Use the data pipeline to build models of real world systems from data analysis.
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
* Possible ways to to transfer research model into production.

# Query engines 

## Terms and concepts 

## Learning goals 

* Know different types of query languages and the 


#  Data consumer

## Terms and concepts

## Learning goals

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

## Learning goals

* Understand the need for automation of data ingestion and processing.
  * Reproducible results
  * Understandability 
  * Less errors
  * Cost reduction
* Know tools for definition and execution of data transformation.


# Infrastructure
  
## Terms and concepts

## Learning goals

* Understand the specific requirements on infrastructure:
  * Storage capacity
  * Processing 
  * Network
* Cloud vs on premise infrastructure 

# Crosscutting concerns 

## Terms and concepts

## Learning goals

# Examples of data processing pipelines 

## Learning goals 

* Know example requirements that are a good fit for database types (FORMULIERUNG!)
* Know examples of (big) data architectures and possible fields of application
    * Lambda
    * Kappa 
    * Data vault
