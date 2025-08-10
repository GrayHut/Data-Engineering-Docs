![alt text](media/image.png)

# Core Concepts in Data

#### Within this blog, we are going to define and explore some core concepts within the data field. Such concepts feature in various spheres within the data ecosystem such as Data engineering, data analytics, Big data, cloud computing etc
#### Grasping a fundamental understanding of them, will lay a solid foundation to build upon.

## 1. Batch vs Streaming ingestion

**Data ingestion** involves retrieving data from different sources into a single common destination while keeping it in the original format of the source.


For **batch ingestion** data moves at regular scheduled intervals in clusters for source(s) to destination. Is ideal where the data user doesn’t require immediate/real-time data updates ie financial reporting

For **streaming ingestion** involves retrieval of real-time data by making use of change data capture (CDC) to monitor live transactions and make changes to the destination in real-time. It is recommended in situations where data is time sensitive and changes almost constantly. Streaming ingestion is used in cases such as tracking live financial markets etc.

Tools used for streaming ingestion include *Apache kafka, Google Pub, Amazon Kinesis* etc


## 2. Change Data Capture (CDC)

This is a style of data movement that involves capturing every change, transaction from source and moving it to the destination in real-time. 

CDC can occur in three ways; **log-based, query-based and trigger-based** Change Data Capture.
	
This refers to the process of detecting any data changes in the data source and ensuring the changes reflect in the destination in real-time. This concept is applied in stream ingestion to ensure the data destination has up to date data as it changes.


## 3. Idempotency

This concept ensures that only one outcome is achieved even if an operation is done multiple times 

**OR** 

Performing an operation once has the same effect as performing it multiple times.

An example of this concept is sending a server the same request multiple times due to network unreliability.

## 4. OLTP vs OLAP

**Online Transaction Processing (OLTP)**: data processing system that allows the real-time execution of a large number of database transactions – with rapid responses - by a large number of people. These systems are crucial for he processing of a large number of simple transactions such as database updates, insertions and deletions.

Such systems are responsible for day-to-day transactions such as ATMs, in-store purchases & hotel reservations.

**Online Analytical Processing (OLAP)**: data processing system that conducts data a analysis from a multidimensional perspective at very high speeds giving the data user key insights into the said data. This data is sourced from a centralized platform ie data warehouse.

## 5. Columnar vs Row-based storage

**Columnar storage** simply alludes to data storage in columns. Here values of a particular column are stored in the same storage unit/block. This storage type is good for data analysis as data of the same column is stored in the same area thus easier querying. Columnar storage is popular for OLAP systems.

**Row-based storage** involves storage of all attributes of a single record (row) on the same disk. This storage method is popular in OLTP systems since it is less resource intensive to conduct update, insert and delete operations.

## 6. Partitioning

**Data partitioning** is the process of splitting large datasets into smaller chunks that can be easily accessed and managed. This helps in easing scalability, performance and improving efficiency.

## 7. ETL vs ELT

**ETL** data pipeline involves data extraction, Transformation and finally Loading. This process also involves temporary storage of extracted data before transformation known as staging. ETL is optimal for structured data with smaller workloads.

**ELT** data pipeline loads into the data warehouse/lake before transformation. This method is good for big data and cloud computing because transformation happens a bit later.

## 8. CAP Theorem
*The theorem outlines that within a distributed system, one can only achieve 2 out of three of Consistency, Availability & Partition tolerance.*

- **Consistency:** all the nodes see/view the same data at the same time
- **Availability**: all requests get a response – successful or unsuccessful
- **Partition tolerance**: system works despite failures between nodes

## 9. Windowing in streaming

**Windowing** is a fundamental concept in stream processing that involves dividing continuous data streams into batches called windows.

By specifying a window size, events are accumulated within each window & processed collectively when the window closes.

## 10. DAGs & Workflow orchestration

> DAG → Direct Acyclic Graph

DAG is an airflow concept that collects tasks & organizes them with dependencies and linkages specifying how they should run.

DAG properties:

- DAGs are defined in python files in the “DAG” folder
- Transitive closure & transitive reduction are defined differently in DAGs.
- Each node receives a string of ids that it uses as labels for storing calculated values.
- dag_id is the unique value that identifies each DAG.
- start_date defines when the DAG should start.
- dag_args are a dictionary of variables to be used as constructor keyword parameters when  initializing parameters.

Workflow orchestration: refers to the process of coordinating and automating complex workflows consisting of multiple interconnected tasks.

Workflow orchestration involves;

- designing and defining the workflows
- scheduling & executing the tasks
- monitoring progress & outcomes
- handling any errors or exceptions that may arise

Examples of workflow orchestration tools;

1. **Apache Airflow**: a platform for developing, scheduling & monitoring batch-oriented workflows defined as DAGs in python.
2. **Dagster**: this tool focuses on data-aware pipelines with a strong emphasis on data engineering practices.
3. **Temporal**: this tool is designed for fault tolerant execution of long running business processes.
4. **Argo Workflows**: is a high performance, container-native engine for orchestrating parallel jobs on Kubernetes.

## 11. Retry Logic & Dead Letter Queues
**Retry logic** is a technique that automatically retries failed operations in case of failure. This is used to enhance reliability especially in network and distributed systems in the event of network interruptions or temporary service unavailability.

**Dead letter queue (DLQ)** is a special message queue that stores messages that cannot be processed (by a software system) due to errors temporarily.

Message queues are software components that support asynchronous communication in distributed systems and allow sending of messages between software services in any volume without requiring the receiver to be always available.

Dead letter queue specifically stores erroneous messages with no destination or can’t be processed by the receiver.

DLQ reduces the cost of communication and improves troubleshooting by allowing developers investigate causes of errors of messages stored in the DLQ.

## 12. Back-filling & Reprocessing
**Data back-filling** refers to the process of filling in missing data into a dataset or system. This process is essential in maintaining data integrity and consistency.

**Reprocessing** involves recalculation of historical data in cases where there is a change in business logic or data quality issues are discovered. The aim of reprocessing is to ensure the data reflects the most accurate and up-to-date state.
 
*Reprocessing is a broader term that also encompasses back-filling*

## 13. Data Governance
This is a framework that defines how data within an organization is protected, managed and value is derived from the said data.

Core objectives of the said framework are;

- Regulatory compliance
- Data security & privacy
- Data stewardship
- Data quality management

## 14. Time Travel & Data Versioning
**Time travel** allows users to query a historical version of data at a particular point in time.

**Data versioning** means creating a unique reference to a collection of data. This unique reference may take the form of unique id, query of timestamp.

## 15. Distributed Processing Concepts

We can begin by defining a **distributed system**; It is a collection of nodes (can be software or hardware components) that are connected via a network and work together coherently by communicating through message parsing or events to achieve a single objective.

*A distributed system gives the end user an illusion that that the process is being carried out by a single machine/computer hiding the complex network of devices working in sync to execute the process.*

**Distributed processing** (especially in data) alludes to a model where different parts of a data processing task is carried out by a number of different resources/nodes that operate within a network.

Distributed processing features the following concepts;
- **Parallel processing framework (parallelism)**: parallelism is a processing structure that allows many tasks/calculations/processes to be carried out across various nodes simultaneously. Distributed data processing utilizes parallel processing frameworks such as Apache Hadoop & Apache Spark to provide infrastructure for this type of processing.
- **Scalability & resource management**: distributed computing involves making the system adaptable to various processing capacities through balacing computation, storage and network resources across the various nodes. Resource management techniques including load balancing and dynamic resource allocation are key in determining system performance.
- **Partitioning & data distribution**: partitioning involves the division of one dataset into several smaller chunks which are then distributed across various nodes allowing for parallel processing. This allows for better resource utilization during processing.
- **Fault tolerance & reliability**: distributed systems should me able to maneouver errors/faults during processing to avoid downtimes. Techniques such as redundancy and fault detection algorithms are used to increase system reliabilty.
- **Synchronization & data consistency**: since many nodes are working simultaniously on various chunks of the same processes, it is important that they maintain coherence and have accurate data results. Techniques such as locking mecahnisms and data replication play a vital role in achieving this.
- **Data agregation and result integration**: this involves coming up with the final outcome of the different inividual partitions through integration and agregattion techniques.

Distributed processing is utilized by big organizations like *Amazon, Google, Meta* etc to carry out their huge data processing requirements more efficiently, reliably and with high speeds.