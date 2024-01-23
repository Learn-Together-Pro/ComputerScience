# Key concepts of DBMS

Key concepts of DBMS.

<!-- [:arrow_down: Tags legend](#tags-legend) at the end of the page. -->

### Page

Fundamental unit of data storage and retrieval on disk. A page is a fixed-length block of data that is read from or written to the disk. In a DBMS, the data of tables (rows/tuples) is stored in these pages. A page is the term used within the context of a DBMS and refers to the unit of data that is read from or written to the disk by the database.

Pages are often composed of one or more disk blocks. The DBMS manages data in terms of pages.

In a Database Management System (DBMS), "blocks" and "pages" are often used interchangeably to refer to the fundamental units of data storage and retrieval on disk. While both blocks and pages represent data units on the disk, "block" is a more general term used in computing and storage, while "page" is specific to the context of databases and how the DBMS handles data. The DBMS abstracts the complexities of block-level operations, presenting a more manageable unit, the page, for storing and handling data.

### Blocks

These are units of data storage at the file system level. A block is typically a collection of data stored on the disk, and databases read or write data in blocks.

Pages are often composed of one or more disk blocks. The DBMS manages data in terms of pages.

In a Database Management System (DBMS), "blocks" and "pages" are often used interchangeably to refer to the fundamental units of data storage and retrieval on disk. While both blocks and pages represent data units on the disk, "block" is a more general term used in computing and storage, while "page" is specific to the context of databases and how the DBMS handles data. The DBMS abstracts the complexities of block-level operations, presenting a more manageable unit, the page, for storing and handling data.

### Directory Page / Data Page

A directory page, also known as an index page in some contexts, is used to store metadata about data pages, for indexing and to store variable-length records. This metadata typically includes pointers or references to data pages. A data page is where the actual data records (rows/tuples) of a database table are stored.

### Slot

In a Database Management System (DBMS), a "slot" typically refers to a specific location or position within a data page where a record (row or tuple) is stored. In the structure of a data page:

Each data page is divided into multiple slots.
Each slot holds one record or provides a reference (like a pointer) to a record.
The DBMS uses these slots to efficiently locate and manage individual records within a page.

### Buckets

In the context of hash-based structures or algorithms, a bucket is a slot in a hash table where data entries are stored. Buckets help in organizing data for efficient retrieval.

### Tuples ~ Rows ~ Record

A row ~ tuple ~ record in a relational database represents a single, implicitly structured data item in a table.

A row in the table, where each column of the row represents a value of an attribute of the tuple.
Each record is usually uniquely identified by a 'page_id' and a 'slot_id'.
In Postgress tuple can mean an occupied slot.

### Join Algorithms

**Nested Loop Join**

Iterates over each row of one table (outer loop) and for each row, it iterates over all rows of the other table (inner loop), checking for matches. It's straightforward but can be inefficient for large tables.

- **Memory Usage**: Low.
- **Disk I/O Efficiency**: Low for large datasets.
- **Speed**: Generally slow, especially for large datasets.
- **Scalability**: Poor with large datasets.
- **Dependency on Indexes**: High performance if an inner table is indexed.
- **Parallelizability**: Limited.
- **Improvement**: No, original.

**Block Nested Loop Join**

Enhances the basic nested loop join by reading blocks of rows from the outer table, reducing the number of disk accesses needed.

- **Memory Usage**: Moderate.
- **Disk I/O Efficiency**: Better than a simple nested loop.
- **Speed**: Faster than a simple nested loop for medium-sized datasets.
- **Scalability**: Moderate.
- **Dependency on Indexes**: Less than simple nested loop.
- **Parallelizability**: Moderate.
- **Improvement**: Nested Loop Join.

**Indexed Join**

Utilizes an index on the join key of one table to efficiently find matching rows in the other table. Highly efficient when an appropriate index is available. Might be perceived as Nested Loop Join improvement.

- **Memory Usage**: Low.
- **Disk I/O Efficiency**: Very efficient if using indexes.
- **Speed**: Fast when indexes are available.
- **Scalability**: Good for indexed tables.
- **Dependency on Indexes**: High.
- **Parallelizability**: Dependent on the database's ability to handle parallel index scans.
- **Improvement**: Nested Loop Join.

**Hash Join**

Builds a hash table for one table (usually the smaller one), then iterates through the other table, using the hash table to quickly find matching rows. It's efficient for equi-joins and large datasets.

- **Memory Usage**: High due to hash table creation.
- **Disk I/O Efficiency**: Good for equi-joins.
- **Speed**: Fast for equi-joins, especially with proper memory.
- **Scalability**: Good, but dependent on memory.
- **Dependency on Indexes**: Not required.
- **Parallelizability**: Good.
- **Improvement**: No, original.

**Grace Hash Join**

Splits the tables into partitions that fit into memory, applies hash join on these smaller parts. It's designed for handling very large tables that don't fit into memory.

- **Memory Usage**: Designed to handle memory limitations.
- **Disk I/O Efficiency**: Handles large datasets efficiently.
- **Speed**: Good for large datasets.
- **Scalability**: Excellent for large datasets.
- **Dependency on Indexes**: Not required.
- **Parallelizability**: Good.
- **Improvement**: Hash Join.

**Sort-Merge Join**

Sorts both tables by the join key and then merges them, efficiently finding matches. Best suited for tables that are already sorted or partially sorted.

- **Memory Usage**: Moderate.
- **Disk I/O Efficiency**: Good, especially if data is pre-sorted.
- **Speed**: Good for sorted datasets.
- **Scalability**: Good.
- **Dependency on Indexes**: Benefits from sorted data.
- **Parallelizability**: Good.
- **Improvement**: No, original.

### Joins

**Inner Join ~ Cross Join**

Returns rows with matching values in both tables. Produces the Cartesian product of the two tables. Semantically cross join and inner join are same.

**Self Join**

Comparing rows within the same table. Self join is also inner join and cross join, but not all innder join is self join.

**Outer Join**

Return all rows from one or both of the joined tables, regardless of whether a matching row exists in the other table.

**Left Outer Join**

Returns all rows from the left table and matching rows from the right table. Uses null for missing in the right table rows.

**Right Outer Join**

Returns all rows from the right table and matching rows from the left table. Uses null for missing in the left table rows.

**Full Outer Join**

Returns rows when there is a match in either left or right table. Uses null for missing in either left or right table rows.

**Semi Join**

Returns rows from the first table where a match exists in the second table.

**Anti Join**

Returns rows from the first table where no match exists in the second table.

### SQL Sub-languages

SQL (Structured Query Language) encompasses several sub-languages, each serving different purposes in the database environment.

- DDL (Data Definition Language): Used for defining and modifying the database structure and schema. Key commands include:
- DML (Data Manipulation Language): Used for managing data within database objects (like tables). Key commands include:
- DCL (Data Control Language): Used for controlling access to data in the database. Key commands include:
- TCL (Transaction Control Language): Used to manage transactions within the database. Key commands include:
- DQL (Data Query Language): It deals primarily with the retrieval of data and includes the SELECT command, which is used to query data from the database. Technically part of DML, but sometimes considered separately.

Some commands.

- DDL: CREATE, ALTER, DROP, TRUNCATE, COMMENT, RENAME
- DML: SELECT, INSERT, UPDATE, DELETE, MERGE
- DCL: GRANT, REVOKE
- TCL: COMMIT, ROLLBACK, SAVEPOINT, SET TRANSACTION
- DQL: SELECT

### Clustered Index / Non-Clustered Index

A **clustered index** determines the physical order of data in a table. It sorts and stores the data rows of the table based on the indexed columns. Each table can have only one clustered index because the data rows themselves can be sorted in only one order. The primary key of a table is often a clustered index.

A **non-clustered index**, on the other hand, does not alter the physical order of the rows. It creates a separate structure within the table which holds the values of the indexed columns and pointers to the corresponding rows. A table can have multiple non-clustered indexes.

### Left-Deep Plans / Right-Deep Plans

In a **left-deep join** tree, the left child of each join node is always a base table, not another join. This allows for the possibility of using nested loops joins efficiently, where the left table can be kept in memory while the right table is scanned multiple times. It is advantageous in scenarios where indexes are available on the inner tables.

In a **right-deep join** tree, the right child is always a base table. This structure is more conducive to hash joins, where each table is read only once and can be used for building or probing a hash table.

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

### Characteristics of a System

[Resilience](https://www.youtube.com/watch?v=NIy9HMRlpjQ)
: ability to handle and recovery from failure gracefully.

Idempotent
: in computer science, the term is used more comprehensively to describe an operation that will produce the same results if executed once or multiple times.

CAP Theorem
: in theoretical computer science, the CAP theorem, states that any distributed data store can provide only two of the following three guarantees.

<!-- ## Tags legend -->
<!-- - ( _:movie_camera:_ ) - video material -->
<!-- - ( _short_ ) - short overview -->
