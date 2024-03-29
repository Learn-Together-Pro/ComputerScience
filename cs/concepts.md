# Key concepts of Computer Science

Key concepts of Computer Science.

<!-- [:arrow_down: Tags legend](#tags-legend) at the end of the page. -->

<!-- - []() by []() ( _:movie_camera:_ ) -->

## Architecture

SOA ~ Service-oriented architecture
: An architectural style that focuses on discrete services instead of a monolithic design. Loosely coupled service-oriented architecture with bounded context.

MVC
: ...

DDD
: ...

BDD
: ...

## Cloud

Horizontal / Vertical scaling
: ...

High-level design / Low-level design
: High-level design : explains the architecture that would be used to develop a system. Low-level design is a component-level design process that follows a step-by-step refinement process, this process can be used for designing data structures, required software architecture, source code and ultimately, performance algorithms.

Distributed consensus
: ...
Types: 2PC, 3PC, SAGA

Replication strategy
: ...

Split brain
: failure when more than single component believes it is a master

Sharding
: a database architecture pattern related to horizontal partitioning — the practice of separating one table’s rows into multiple different tables, known as partitions.

Infrastructure as code
: methodology ...

IaaS
: ...

PaaS
: ...

SaaS
: ...

On-Premises Service
: ...

Fail Over
: ...

Disaster Recovery
: ...

Business Continuity Plan
: ...

Recovery Point Objective
: ...

Recovery Time Objective
: ...

## Database

### Data Lake
: ...

### Data Lakehouse
: ...

### Data Mesh
: method ...

### Data Fabric
: method ...

### Data base / Data Mesh / Data Warehouse / Data Lake
: ...

### Data Warehouse ~ EDW
: ...

### ETL ~ Extract Transform Load
: ...

### BI ~ Business Intelligence
: ...

### PAML ~ Prediction Analytic Machine Learning
: ...

### Column-oriented database / Row-oriented database
: ...

### Column-wide database ~ Big Table database

A column-based database, also known as a columnar database, is a type of database management system that stores data in columns rather than in rows. In a column-based database, each column of a table is stored separately on disk, rather than storing each row as a separate record. This makes columnar databases well-suited for analytics workloads that require complex queries across large volumes of data, as it allows for much faster querying and analysis of data. Column-based databases are often used for data warehousing and business intelligence applications, as well as for storing large amounts of structured and semi-structured data. They are known for their high performance, scalability, and ability to handle large volumes of data with low latency. Some popular examples of column-based databases include Apache Cassandra, Apache HBase, and Google Bigtable.

Data Model: Wide column databases use a non-relational or NoSQL data model, while relational databases use a relational data model.

High Availability: Wide column databases can achieve high availability and fault tolerance through data replication across multiple nodes or servers. Relational databases typically rely on backup and recovery methods.

Query Language: Wide column databases use a variety of query languages, including CQL (Cassandra Query Language) and SQL-like query languages. Relational databases use SQL.

Use Cases: Wide column databases are often used for big data applications, such as IoT, real-time analytics, and high-traffic websites. Relational databases are commonly used for transactional systems, such as e-commerce and financial applications.

Schema flexibility: In a wide column database, the schema can be more flexible, allowing for the addition or removal of columns without affecting the rest of the schema. This is because the data is stored in columns rather than rows, which allows for a more dynamic schema.

Distributed architecture: Wide column databases are often designed to be distributed across multiple nodes, allowing for horizontal scalability and fault tolerance. This is in contrast to relational databases, which are often designed to run on a single node or a small cluster of nodes.

High write performance: Because wide column databases are optimized for write-heavy workloads, they often have very high write performance compared to relational databases. This is because they use a log-structured merge tree (LSM tree) data structure, which allows for efficient writes and compaction of data.

Query performance: Wide column databases may have slower query performance than relational databases, especially for complex queries that require joins or aggregation. However, they are often optimized for specific types of queries, such as range queries or key-value lookups.

Strong consistency: Some wide column databases, such as Apache Cassandra, offer strong consistency guarantees through features like tunable consistency levels and lightweight transactions. However, achieving strong consistency in a distributed system can be challenging, and it may come at the cost of performance or availability.

NoSQL paradigm: Wide column databases are part of the NoSQL movement, which emphasizes flexibility, scalability, and performance over strict adherence to the relational data model. This means that wide column databases may have different trade-offs and design principles than relational databases.

Column-oriented storage: Wide column databases store data in column families, which are groups of columns that are often accessed together. This allows for efficient storage and retrieval of data, especially when only a subset of columns is needed for a particular query. Relational databases, on the other hand, store data in rows, which can make it harder to optimize queries for specific subsets of columns.

##### Example

HBase, Google Big Table, Cassandra, ScyllaDB

### Graph DB
...

##### Example

Neo4J, FlockDB

### Consistency in reads : Strict Consistence / Eventual Consistency / Causal consistency

**Strict consistency** is a guarantee that any read operation on the data will always return the latest version of the data. In other words, if a data is updated, any subsequent read of that data will always return the latest version. Strict consistency is often achieved by locking data during updates, which can cause delays and potentially slow down the system.

**Causal consistency** ensures that causally related operations are seen in a specific order by all nodes in the system, but does not necessarily require that all nodes see all operations in the same order. This means that there may be some operations that are seen in a different order by different nodes, as long as there is a causal relationship between them.

**Eventual consistency** is a weaker form of consistency that allows for temporary inconsistencies to exist between replicas of the data, but guarantees that the replicas will eventually converge to the same value. This means that if a data is updated, there may be a delay before all replicas of the data are updated with the latest version. However, given enough time and no new updates, all replicas will eventually be updated and converge to the same value.

In summary, strict consistency guarantees immediate consistency at the expense of performance, while eventual consistency allows for temporary inconsistencies in exchange for higher performance and availability. Causal consistency strikes a balance between strong consistency and weak consistency, and is often used in distributed systems where strict consistency is not feasible due to performance or network limitations. Causal consistency provides strong ordering guarantees while eventual consistency provides weaker ordering guarantees but allows for more flexibility and scalability.

### Consistency in data

Consistency in data refers to the property of data being accurate and valid over time. It means that the data remains consistent in all copies of the database, even when it is updated or modified. In a consistent database, all data is correctly synchronized, and there are no conflicting or contradictory copies of the same data. Consistency ensures that data is reliable and can be trusted by users and applications. It is a fundamental aspect of database design and is achieved through various mechanisms such as transactions, locking, and replication.

### Durability of data storage

In the context of data storage and database systems, durability refers to the ability of a transaction to survive permanently in the event of a system failure. In other words, once a transaction has been committed, its changes must be stored and protected in a way that ensures they will not be lost or undone due to hardware or software failure.

There are typically two types of durability guarantees:

**Volatile Durability**: In this level of durability, changes are written to volatile memory (such as RAM) before they are stored on disk. As a result, if the system fails before the changes are written to disk, they may be lost.

**Non-Volatile Durability**: In this level of durability, changes are written directly to disk or other non-volatile storage before a transaction is considered to be complete. This guarantees that the changes will be retained even in the event of a system failure.

Most modern database systems provide some form of non-volatile durability, as it is considered to be a critical component of transaction processing.

### Atomicity : All-or-nothing atomicity / Atomicity with partial failure

**All-or-nothing atomicity**: In this type of atomicity, a transaction is either completed in its entirety or not at all. If any part of the transaction fails, the entire transaction is rolled back and the database is left in the state it was in before the transaction began.

**Atomicity with partial failure**: In this type of atomicity, a transaction can be partially completed even if some part of it fails. The completed part of the transaction is still committed to the database, while the failed part is rolled back.

### Isolation : Read uncommitted / Read committed / Repeatable read / Serializable

**Read uncommitted**: In this level of isolation, transactions are not isolated from each other, and a transaction can read uncommitted data from another transaction. This level provides no protection against dirty reads, non-repeatable reads, or phantom reads.

**Read committed**: In this level of isolation, a transaction can only read committed data from other transactions. This level provides protection against dirty reads, but still allows non-repeatable and phantom reads.

**Repeatable read**: In this level of isolation, a transaction can read data that has been committed by other transactions, but cannot read data that has been modified but not yet committed. This level provides protection against dirty reads and non-repeatable reads, but still allows phantom reads.

**Serializable**: This is the highest level of isolation, where transactions are completely isolated from each other. A transaction can only read data that has been committed by other transactions, and no other transaction can modify the data until the transaction is complete. This level provides complete protection against dirty reads, non-repeatable reads, and phantom reads, but can result in slower performance due to locking.

In summary, the differences between these levels of isolation are based on the degree of protection against different types of read inconsistencies and the level of concurrency that is allowed between transactions.

### Document-based database
...

### OLTP DB / OLAP DB
: ...

### Relational database / Document-based database
: ...

## Characteristics

[Resilience](https://www.youtube.com/watch?v=NIy9HMRlpjQ)
: ability to handle and recovery from failure gracefully.

Idempotent
: in computer science, the term is used more comprehensively to describe an operation that will produce the same results if executed once or multiple times.

CAP Theorem
: in theoretical computer science, the CAP theorem, states that any distributed data store can provide only two of the following three guarantees.

## Communication

APM ~ application performance monitoring
: ...

Pub-Sub ~ Publish-Subscribe ~ Broker
: Implementation of publish-subscribe as a service. Conceptually it is message queue + namespace ~ channels ~ types of events.

Message queue
: Implementation of publish-subscribe with a single channel as a service. Conceptually it is pub-sub with a single channel ~ type of event.

CQRS ~ Command and Query Responsibility Segregation
: Pattern that separates read and update operations for a data store. Implementing CQRS in your application can maximize its performance, scalability, and security. The flexibility created by migrating to CQRS allows a system to better evolve over time and prevents update commands from causing merge conflicts at the domain level.

Event Sourcing
: Pattern that defines an approach to handling operations on data that's driven by a sequence of events, each of which is recorded in an append-only store.

Consistent hashing
: ...

Proxy / Reverse Proxy
: ...

Load Balancing
: ...

<!-- ## Tags legend -->
<!-- - ( _:movie_camera:_ ) - video material -->
<!-- - ( _short_ ) - short overview -->
