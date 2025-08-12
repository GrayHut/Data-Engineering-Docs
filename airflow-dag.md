# Airflow & DAGs

#### Airflow is an open-source data tool used for modeling and running data pipelines. It helps to write workflows as Directed Acyclic Graph (DAG) tasks.

Main components of Airflow architecture are;
1. **Webserver** – provides the web interface and REST API
2. **Scheduler** – brain that decides what and when to run
3. **Executor** – runs tasks. There 3 types of executors;
       
    - ***SequentialExecutor***: runs one task at a time, 
    - ***LocalExecutor***: runs multiple tasks at a time on a single machine 
    - ***CeleryExecutor***: distributed tasks across multiple machines 
    - ***KubernetesExecutor***: runs tasks on kubernetes pods
       
4. **Metadata DB** – stores all airflow information
5. **Worker nodes** – machines that execute tasks

**DAG**: is an Airflow idea that collects tasks and organizes them with *dependencies* and *linkages* that specify how they should run.

**DAGrun**: a *DAG instance* with an execution timestamp

DAG properties
- Defined in python files in airflow DAG folder
- Transitive closure and transitive reduction are defined differently in DAGs.
- Each node receives a string of ids to use as labels for storing calculated values.
- `dag_id `serves as a unique value to identify a DAG.
- `start_date` tells when your DAG should start.
- `default_args` is a dictionary of variables to be used as constructor keyword parameters when initializing operators

Use of DAG
- Determines sub expressions often used.
- Names used within the block and names computed outside the block are determined by DAG.
- Provides the input and output of all arithmetic operations conducted inside the code allowing the compiler to eliminate similar sub expressions.

**Operator**: operator describes a single task in a process and may operate alone without requiring resources from other operators.

Operator properties
- Operator defines the nature of the task and how it should be executed.
- When an operator is created, the task becomes a node in DAG.
- Operator automatically retries in case it fails.

Common operators include:
1. ***BashOperator*** – executes bash command
2. ***EmailOperator*** – sends email
3. ***SqliteOperator, PostegreOperator, MySQlOperator*** – runs SQL commands
4. ***SimpleHttpOperator*** – sends Http requests
5. ***PythonOperator*** - calls an arbitrary python function

Types of Operators:
- ***Action operator*** – performs a certain action ie EmailOperator, BashOperator
- ***Transfer operator*** – moves data from one location to another
- ***Sensor operator*** – waits for data to reach a certain destination