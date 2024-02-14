# Key concepts of DBMS

Key concepts of DBMS.

<!-- [:arrow_down: Tags legend](#tags-legend) at the end of the page. -->

## Page

Fundamental unit of data storage and retrieval on disk. A page is a fixed-length block of data that is read from or written to the disk. In a DBMS, the data of tables (rows/tuples) is stored in these pages. A page is the term used within the context of a DBMS and refers to the unit of data that is read from or written to the disk by the database.

Pages are often composed of one or more disk blocks. The DBMS manages data in terms of pages.

In a Database Management System (DBMS), "blocks" and "pages" are often used interchangeably to refer to the fundamental units of data storage and retrieval on disk. While both blocks and pages represent data units on the disk, "block" is a more general term used in computing and storage, while "page" is specific to the context of databases and how the DBMS handles data. The DBMS abstracts the complexities of block-level operations, presenting a more manageable unit, the page, for storing and handling data.

## Blocks

These are units of data storage at the file system level. A block is typically a collection of data stored on the disk, and databases read or write data in blocks.

Pages are often composed of one or more disk blocks. The DBMS manages data in terms of pages.

In a Database Management System (DBMS), "blocks" and "pages" are often used interchangeably to refer to the fundamental units of data storage and retrieval on disk. While both blocks and pages represent data units on the disk, "block" is a more general term used in computing and storage, while "page" is specific to the context of databases and how the DBMS handles data. The DBMS abstracts the complexities of block-level operations, presenting a more manageable unit, the page, for storing and handling data.

## Directory Page / Data Page

A directory page, also known as an index page in some contexts, is used to store metadata about data pages, for indexing and to store variable-length records. This metadata typically includes pointers or references to data pages. A data page is where the actual data records (rows/tuples) of a database table are stored.

## Slot

In a Database Management System (DBMS), a "slot" typically refers to a specific location or position within a data page where a record (row or tuple) is stored. In the structure of a data page:

Each data page is divided into multiple slots.
Each slot holds one record or provides a reference (like a pointer) to a record.
The DBMS uses these slots to efficiently locate and manage individual records within a page.

## Buckets

In the context of hash-based structures or algorithms, a bucket is a slot in a hash table where data entries are stored. Buckets help in organizing data for efficient retrieval.

## Tuples ~ Rows ~ Record

A single, implicitly structured data item in a table.

A row in the table, where each column of the row represents a value of an attribute of the tuple.
Each record is usually uniquely identified by a 'page_id' and a 'slot_id'.
In Postgress tuple can mean an occupied slot.

## Cell ~ Field

The individual storage area for a single piece of information ( data point ) within a table.

## Value ~ Entry ~ Attribute Value

Since each column represents an attribute of the table, the data within a cell can also be referred to as the attribute value for that particular row.

## Join Algorithms

> **Nested Loop Join**

Iterates over each row of one table (outer loop) and for each row, it iterates over all rows of the other table (inner loop), checking for matches. It's straightforward but can be inefficient for large tables.

- **Memory Usage**: Low.
- **Disk I/O Efficiency**: Low for large datasets.
- **Speed**: Generally slow, especially for large datasets.
- **Scalability**: Poor with large datasets.
- **Dependency on Indexes**: High performance if an inner table is indexed.
- **Parallelizability**: Limited.
- **Improvement**: No, original.

> **Block Nested Loop Join**

Enhances the basic nested loop join by reading blocks of rows from the outer table, reducing the number of disk accesses needed.

- **Memory Usage**: Moderate.
- **Disk I/O Efficiency**: Better than a simple nested loop.
- **Speed**: Faster than a simple nested loop for medium-sized datasets.
- **Scalability**: Moderate.
- **Dependency on Indexes**: Less than simple nested loop.
- **Parallelizability**: Moderate.
- **Improvement**: Nested Loop Join.

> **Indexed Join**

Utilizes an index on the join key of one table to efficiently find matching rows in the other table. Highly efficient when an appropriate index is available. Might be perceived as Nested Loop Join improvement.

- **Memory Usage**: Low.
- **Disk I/O Efficiency**: Very efficient if using indexes.
- **Speed**: Fast when indexes are available.
- **Scalability**: Good for indexed tables.
- **Dependency on Indexes**: High.
- **Parallelizability**: Dependent on the database's ability to handle parallel index scans.
- **Improvement**: Nested Loop Join.

> **Hash Join**

Builds a hash table for one table (usually the smaller one), then iterates through the other table, using the hash table to quickly find matching rows. It's efficient for equi-joins and large datasets.

- **Memory Usage**: High due to hash table creation.
- **Disk I/O Efficiency**: Good for equi-joins.
- **Speed**: Fast for equi-joins, especially with proper memory.
- **Scalability**: Good, but dependent on memory.
- **Dependency on Indexes**: Not required.
- **Parallelizability**: Good.
- **Improvement**: No, original.

> **Grace Hash Join**

Splits the tables into partitions that fit into memory, applies hash join on these smaller parts. It's designed for handling very large tables that don't fit into memory.

- **Memory Usage**: Designed to handle memory limitations.
- **Disk I/O Efficiency**: Handles large datasets efficiently.
- **Speed**: Good for large datasets.
- **Scalability**: Excellent for large datasets.
- **Dependency on Indexes**: Not required.
- **Parallelizability**: Good.
- **Improvement**: Hash Join.

> **Sort-Merge Join**

Sorts both tables by the join key and then merges them, efficiently finding matches. Best suited for tables that are already sorted or partially sorted.

- **Memory Usage**: Moderate.
- **Disk I/O Efficiency**: Good, especially if data is pre-sorted.
- **Speed**: Good for sorted datasets.
- **Scalability**: Good.
- **Dependency on Indexes**: Benefits from sorted data.
- **Parallelizability**: Good.
- **Improvement**: No, original.

## Joins

[Look](./cheatsheet.md#SQL-Join)

> **Inner Join**

Returns rows with matching values in both tables.

> **Cross Join** ~ **Cartesian Product**

Produces the Cartesian product of the two tables.

Semantically cross join and cartesian product are same. The primary difference bettwen inner join and cross join is that an inner join requires a matching condition and filters results based on that condition, while a cross join does not filter rows and combines all rows from the joined tables.

> **Self Join**

Comparing rows within the same table. Self join is also inner join and cross join, but not all innder join is self join.

> **Outer Join**

Return all rows from one or both of the joined tables, regardless of whether a matching row exists in the other table.

> **Left Outer Join**

Returns all rows from the left table and matching rows from the right table. Uses null for missing in the right table rows.

> **Right Outer Join**

Returns all rows from the right table and matching rows from the left table. Uses null for missing in the left table rows.

> **Full Outer Join**

Returns rows when there is a match in either left or right table. Uses null for missing in either left or right table rows.

> **Semi Join**

Returns rows from the first table where a match exists in the second table.

> **Anti Join**

Returns rows from the first table where no match exists in the second table.

> **Natural Join**

Operation in SQL that automatically joins two tables based on columns with the same names and compatible data types in both tables. Can be either inner join or outer join.

> **Equi Join**

Operation that combines rows from two or more tables based on the equality of specified columns between these tables.

## Non-monotonic behavior

Behavior of a function or system when the addition of new information can invalidate previous conclusions or results.

In other words, a system exhibits non-monotonic behavior if a conclusion drawn from a given set of information might change when new information is added. This contrasts with monotonic behavior, where once something is proven true, it remains true even when additional information is considered.

For example, the COUNT() function is monotonic in the sense that as more rows are added to a table, the result of COUNT() will either stay the same or increase, assuming no rows are deleted. An example of a non-monotonic function is the AVG() (average) function in SQL. It calculates the average value of a numeric column. If new rows are added with values that are lower than the current average, the result of the AVG() function can decrease, which demonstrates non-monotonic behavior.

## SQL Sub-languages

SQL (Structured Query Language) encompasses several sub-languages, each serving different purposes in the database environment.

- DQL (Data Query Language): It deals primarily with the retrieval of data and includes the SELECT command, which is used to query data from the database. Technically part of DML, but sometimes considered separately.
- DDL (Data Definition Language): Used for defining and modifying the database structure and schema. Key commands include:
- DML (Data Manipulation Language): Used for managing data within database objects (like tables). Key commands include:
- DCL (Data Control Language): Used for controlling access to data in the database. Key commands include:
- TCL (Transaction Control Language): Used to manage transactions within the database. Key commands include:

Some commands.

- DQL: SELECT
- DDL: CREATE, ALTER, DROP, TRUNCATE, COMMENT, RENAME
- DML: SELECT, INSERT, UPDATE, DELETE, MERGE
- DCL: GRANT, REVOKE
- TCL: COMMIT, ROLLBACK, SAVEPOINT, SET TRANSACTION

## Clustered Index / Non-Clustered Index

A **clustered index** determines the physical order of data in a table. It sorts and stores the data rows of the table based on the indexed columns. Each table can have only one clustered index because the data rows themselves can be sorted in only one order. The primary key of a table is often a clustered index.

A **non-clustered index**, on the other hand, does not alter the physical order of the rows. It creates a separate structure within the table which holds the values of the indexed columns and pointers to the corresponding rows. A table can have multiple non-clustered indexes.

## Left-Deep Plans / Right-Deep Plans

In a **left-deep join** tree, the left child of each join node is always a base table, not another join. This allows for the possibility of using nested loops joins efficiently, where the left table can be kept in memory while the right table is scanned multiple times. It is advantageous in scenarios where indexes are available on the inner tables.

In a **right-deep join** tree, the right child is always a base table. This structure is more conducive to hash joins, where each table is read only once and can be used for building or probing a hash table.

## Classes of Schedules

> **Serial Schedule**

A schedule is serial if the actions of the different transactions are not interleaved; they are executed one after another.

> **Serializable Schedule**

A schedule where the outcome of executing transactions concurrently is the same as if the transactions had been executed serially. It doesn't require transactions to be executed in a strictly sequential manner but ensures that the final state of the database is as if they were.

Uniot of all 4 sets: Serial, Conflict Serializable, View Equivalent, Final State Equivalent schedules.

Size of sets: Serial < Conflict Serializable < View Equivalent < Final State Equivalent

> **Conflict Serializable Schedule** ~ **Conflict Equivalence**

Two schedules are conflict equivalent if they have the same set of operations, and every pair of conflicting operations is executed in the same order in both schedules.

Conflict-serializable schedules are serializable, but serializable schedules is not necessarily conflict-serializable. Even more restrictive than view equivalent schedule, but it's computationally cheap to come up and check schedule validity. Some valid view equivalent schedules are not conflict serializable schedule and perfectly good to use, but are droped by the algorithm because it's computation expansive to check their serializabness.

> **View Equivalent Schedules**

Two schedules are view equivalent if they ensure that each read operation in the schedules reads the same value from the same write operation. It focuses on the consistency of the visible data in each transaction.

More restrictive schedule thant final state equivalent schedules is the least restrictive one, but anomalies are not possible. Also it has slow concurrency control because making up perfect schedule of such time NP hard problem.

> **Final State Equivalent Schedules**

Two schedules have final state equivalence if they result in the same final state of the database after all the transactions are complete. This includes the final value of all data items.

The largest subset. Serial, conflict serializable and view equivalent schedules are final State Equivalent. Final state equivalent schedules is the least restrictive one, but anomalies are possible.

## Concurrency Controls Methods

> **Pessimistic Concurrency Control** ~ **Lock-Based Concurrency Control**

It uses locks to ensure that only one transaction can access a data item at a time.

This is one of the most common concurrency control methods.

> **Optimistic Concurrency Control**

Optimistic Concurrency Control assumes that multiple transactions can often complete without interfering with each other. Transactions proceed without locking and then verify at the end that they have not interfered with other transactions.

> **Backward Optimistic Concurrency Control** ~ **BOCC**

Type of OCC where transactions are allowed to run to completion without checking for conflicts. Only when a transaction reaches the commit point does the system check for conflicts with other transactions. If a conflict is detected, the committing transaction is rolled back.

> **Forward Optimistic Concurrency Control** ~ **FOCC**

Type of OCC where transactions are checked for conflicts during their execution phase, as soon as a potential conflict could occur. If a conflict is detected, the transaction may be rolled back immediately before it reaches the commit phase.

> **Multiversion Concurrency Control** ~ **MVCC** ~ **Snapshot Isolation**

Concurrency control method used in database management systems to provide concurrent access to the database and enhance read/write performance. MVCC achieves this by creating multiple, time-stamped versions of a data item (hence "multiversion"), which allows for more granular levels of locking and increases concurrency.

## Conflicting Actions

Two actions in a schedule conflict if they:
- are from different transactions,
- involve the same data item, and
- one of the actions is a write.

## Schedule Conflicts

> **Write Read Conflcit** (WR)

There is a WR conflict between T1 and T2 if there is an item Y: T1 writes Y and afterwards, T2 reads Y. If T, has not committed this is a *dirty read*.

> **Read Write Conflict** (RW)

There is a RW conflict between Ty and Tz if there is an item Y Ty reads Y and afterwards, Tz writes Y. This read becomes *unrepeatable*.

> **Write Write Conflict** (WW)

There is a WW conflict between T, and Ta if there is an item Y: Ty writes Y and afterwards, Ta writes Y. This write becomes overwritten, in another words it might cause *lost update*. But if there is no action which depends on the first write it's called **blind writes**.

## Read Anomalies ~ Lack of Isolation

[Look](./cheatsheet.md#SQL-Isolation-Levels)

> **Dirty Read**

Occurs when a transaction reads data written by another transaction that has not yet been committed. If the other transaction rolls back, the read data might be invalid.

> **Lost Update**

Happens when two transactions read the same data and then update it based on the read, resulting in one of the updates being overwritten by the other.

This occurs when two transactions read the same data and then both update it based on their respective reads. One of the updates can overwrite the other, leading to a "lost update". This is a write phenomenon where the inconsistency occurs because one transaction's update is overwritten by another's.

Non-repeatable Read and Lost Update might considered the same anomaly, although described differently.

> **Non-repeatable Read**

Happens when a transaction reads the same row twice and gets a different value each time, because another transaction modified the data between the two reads.

This occurs when a transaction reads the same row twice and gets different values each time because another concurrent transaction has modified or updated that row. It's about the change in value of a specific data item that a transaction has already read.

Non-repeatable Read and Lost Update might considered the same anomaly, although described differently.

> **Phantom Read**

Occurs when a transaction re-executes a query returning a set of rows that satisfy a specific condition and finds that another transaction has added or removed rows that meet the condition, thus changing the result set.

This happens when a transaction re-executes a query returning a set of rows that satisfy a certain condition and finds that another transaction has added or removed rows in the meantime, thus altering the result set of the query. It's about the change in the number of rows that satisfy a condition due to inserts or deletes by other transactions.

While multiversion concurrency control may guarantee freedom from phantom reads, it alone cannot ensure freedom from write skew anomalies.

> **Write Skew Anomaly**

A write skew occurs when two transactions concurrently read an overlapping data set, and then each transaction updates some portion of that data set such that the updates are not based on the most recent version of the data. This can result in a database state that would not be possible if the transactions were executed serially, thereby violating the database's consistency.

Only the serializable isolation level guarantees that anomalies such as write skew do not occur. While multiversion concurrency control may guarantee freedom from phantom reads, it alone cannot ensure freedom from write skew anomalies.

## SQL Isolation Levels

In summary, the differences between these levels of isolation are based on the degree of protection against different types of read inconsistencies and the level of concurrency that is allowed between transactions.

[Look](./cheatsheet.md#SQL-Isolation-Levels)

> **Read Uncommitted**

The lowest isolation level, allowing transactions to read uncommitted changes from other transactions, which can lead to dirty reads.

> **Read Committed**

Ensures that a transaction can only read data committed before the start of the transaction, preventing dirty reads but still allowing non-repeatable reads and phantom reads.

> **Repeatable Read**

Prevents dirty and non-repeatable reads by ensuring that the rows a transaction reads cannot change during the transaction, but it might still experience phantom reads. Still allowing non-repetable aggregation, because extra new row might appear.

> **Serializable**

The highest isolation level, providing full isolation from other transactions. It prevents dirty reads, non-repeatable reads, and phantom reads, ensuring complete consistency.

## Two-Phase Locking Protocol ~ (2PL)

Concurrency control method used in database systems to ensure serializability of transactions. It involves two phases. Locking Phase: In the first phase, a transaction may acquire locks but cannot release any. The transaction locks all the data items it needs to access. Unlocking Phase: In the second phase, the transaction releases all locks and cannot acquire any new ones.

This protocol ensures that the schedule (order of transactions) will be serializable, meaning the outcome is equivalent to some serial execution of the transactions. However, while it prevents non-serializable schedules, 2PL can lead to deadlocks and decreased system throughput due to the extensive locking it requires.

## Variations of Two-Phase Locking Protocol: Strict 2PL / Preclaiming 2PL

> **Strict Two-Phase Locking ~ Strict 2PL**

In this protocol, a transaction holds all its exclusive locks (write locks) until it commits or aborts. This ensures strict serializability and also avoids the issue of cascading rollbacks, as it only releases locks after the transaction is finalized.

> **Preclaiming 2PL**

Here, a transaction requests all the locks it needs at the beginning. If all the required locks are granted, the transaction proceeds; otherwise, it either waits or is rolled back. This approach can reduce the likelihood of deadlocks but may lead to underutilization of resources due to holding locks for extended periods.

## Intention Lock

A type of lock in database systems that indicates a transaction's intention to acquire a more specific lock on a lower-level database object, such as a row or page, within a larger object like a table.

In databases, there are different levels at which locks can be applied, such as the row level, page level, or table level. Intention locks are a type of lock set on a higher-level database object, such as a table or page, indicating the intention to acquire a lock on a specific lower-level object, like a row, within that higher-level object.

|    | S | X | IS | IX |
|----|---|---|----|----|
| S  |   | X |    | X  |
| X  | X | X | X  | X  |
| IS |   | X |    |    |
| IX | X | X |    |    |

IS - Intention Shared Lock. Indicates that a shared lock will be placed on some lower level object. It allows concurrent transactions to read from the higher-level object.
IX - Intention Exclusive Lock. Indicates that an exclusive lock will be placed on some lower level object. It signals that the transaction intends to modify a lower level object and that no other transactions are permitted to acquire an intention exclusive on the higher-level object.

## Deadlocks Resolving Strategies

> **Deadlock Prevention**

Adjust system conditions to prevent deadlocks, such as ordering resources or preallocating resources.

> **Deadlock Avoidance**

Use algorithms like Banker’s Algorithm to avoid deadlocks by ensuring safe resource allocation.

> **Deadlock Detection and Recovery**

Regularly check for deadlocks and take actions like terminating or rolling back transactions to resolve them. Tricky to select a victim, because it leads either to starvation or computational investments been thrown.

> **Timeout**

Use a timeout mechanism where a transaction is rolled back if it waits longer than a predefined time limit. Tricky to select proper timneout.

## Rollback Strategies

> **Immediate Rollback ~ Undo Logging**

When a transaction fails, its actions are immediately undone using a log that records all changes.

> **Deferred Rollback ~ Redo Logging**

Rollback is deferred until the end of the transaction’s execution. In case of failure, the system uses a log to redo all actions of the transaction.

> **Checkpoints**

Periodically, the system takes a checkpoint storing the current state of the database. In case of failure, the system only needs to rollback to the last checkpoint.

> **Savepoints**

Within a transaction, savepoints mark specific points that a transaction can roll back to, without needing to roll back the entire transaction.

## Scheduling Strategies thinking of Rollback

> **Recoverable Schedule**

Ensures that if a transaction T1 reads data written by another transaction T2, T2 must commit before T1. This prevents scenarios where T1 might need to be rolled back due to T2's failure, which could result in inconsistent data.

> **Cascadable Schedule ~ Cascadeless Schedule**

In a cascadeless schedule, transactions only read data that has been committed, preventing cascading rollbacks where one transaction's failure causes a chain reaction of rollbacks in other transactions.

## Domain ~ Constraints

Set of permissible values that a column (or attribute) in a database table can hold. Constraints are rules enforced on data columns on a table in a database. Domains and constraints in a DBMS work together to maintain data integrity, accuracy, and consistency across a database.

This is often defined by a data type and a range. For example, if a column is meant to store an employee's age, the domain might be set as integers ranging from 18 to 65. Domains and constraints are related in that they both serve to enforce data integrity in a database. While a domain defines what values are permissible for a given attribute, constraints enforce rules on how these values are used and related to each other in the database.

## Key

An attribute or a set of attributes used to uniquely identify rows in a table.

## Determinant

An attribute or a set of attributes on which some other attribute or set of attributes is fully functionally dependent. Essentially, if you have a functional dependency A → B, A is the determinant, because the value of A determines the value of B.

Not all determinants are keys, and a determinant does not have to be unique or mandatory.

## Key Kinds

> **Primary Key** ~ **Entity Identifier**

Uniquely identifies each record in a table. It must contain unique values and cannot be null.

> **Secondary Key**

Any key used mainly for data retrieval and not for identification purposes. Often refers to an index that's not the primary key. Secondary keys can be thought of as supplementary ways to access data efficiently, especially in large tables where multiple query patterns are common.

> **Foreign Key**

A key that links two tables together, referring to the primary key of another table.

> **Composite Key**

A key formed by combining two or more columns in a table.

> **Partial Key** ~ **Determinant**

Used in a composite key when part of the composite key is a foreign key. It's not sufficient by itself to uniquely identify a record.

> **Surrogate Key** ~ **Internal Key** ~ **Identity Column** ~ **Artificial Identifier**

An artificial key that uniquely identifies a record but is not derived from the data. It's often an auto-incrementing number.

> **Unique Key**

Similar to a primary key, but it can accept one null value and can't uniquely identify a record.

> **Candidate Key**

Any column or a combination of columns that can qualify as a primary key in the database.

> **Super Key**

Set of one or more columns (attributes) that can uniquely identify a row in a table. It's a superset of a candidate key, which means a superkey may contain additional columns that are not necessary for unique identification. Every table is guaranteed to have at least one superkey because the set of all columns combined is always a superkey. However, the goal is typically to find the minimal superkey, which is a candidate key with no unnecessary attributes.

## Primary Attribute / Secondary Attribute

> **Primary Attribute**

An attribute that is a part of some candidate key of a relation.

> **Secondary Attribute** ~ **Non-primary Attribute**

An attribute that is not part of any candidate key of a relation.

## Functional Dependency ~ FD

A functional dependency (FD) in a relational database is said to exist when one attribute (or a group of attributes) uniquely determines another attribute (or a group of attributes). This relationship is denoted as `(A → B)`, meaning the value of attribute `(A)` (or set of attributes) uniquely determines the value of attribute `(B)` (or set of attributes).

## Trivial Functional Dependency / Non-Trivial Functional Dependency

> **Trivial Functional Dependency:**

If in a functional dependency (A → B), (B) is a subset of (A), the dependency is considered trivial. It always holds true by definition.

> **Non-Trivial Functional Dependency:**

A functional dependency (A → B) is non-trivial if (B) is not a subset of (A).

## Full Functional Dependency / Partial Functional Dependency

> **Full Functional Dependency**

A functional dependency X → Y is a full functional dependency in relation schema R if removal of any attribute A from X means that the dependency does not hold anymore.

> **Partial Functional Dependency**

A functional dependency X → Y is a partial functional dependency in relation schema R if some attribute A can be removed from X and the dependency still holds.

## Multivalued Dependencies ~ MVD

Non-functional depdendency which occur in a relational database when there is a relationship between attributes that allows multiple rows to be associated independently of each other.

An MVD is a more complex form of dependency than the functional dependency typically addressed in the lower normal forms.

Example of multivalued dependencies. Due to employee ->> favoriteFramework and employee ->> databaseSystem, swap of two cells is possible

| employee     | favoriteFramework | databaseSystem |
|--------------|-------------------|----------------|
| Alice Cooper | React             | PostgreSQL     |
| Alice Cooper | Vue               | SQL Server     |

the table must also contain the following rows

| employee     | favoriteFramework | databaseSystem |
|--------------|-------------------|----------------|
| Alice Cooper | Vue               | PostgreSQL     |
| Alice Cooper | React             | SQL Server     |

## Legal Relation State / Valid Relation State

One in which all the data in the database adheres to predefined rules and constraints.

## Database Anomalies

In Database Management Systems (DBMS), data anomalies are problems or irregularities that can arise in database tables due to improper database design, especially when the database is not normalized properly. These anomalies can lead to inconsistencies, data redundancy, and issues with data integrity. The three primary types of data anomalies are:

> **Insertion Anomalies**

Occurs when certain data cannot be inserted into the database without the presence of other data. This typically happens in databases that are not normalized and where tables are designed to store multiple types of data together. For example, if a database table designed to store information about employees and their departments requires that each employee be assigned to a department, inserting an employee without a department would be problematic, leading to an insertion anomaly.

> **Deletion Anomalies**

Occurs when deleting a row from a table inadvertently results in the loss of additional, unintended data. This is common in tables that store multiple types of related data. For example, if an employee is the only one working in a particular department and their record is deleted from the database, information about the department could be lost if it's only stored in relation to employee records. This indicates poor database design, where the deletion of data from one entity indirectly affects the data of another entity.

> **Update Anomalies**

Occurs when changes to data in one row of a table require multiple rows of data to be updated to maintain consistency. This problem arises in databases where the same piece of data is stored redundantly in multiple places. For example, if an employee's address is stored in multiple records because they are associated with multiple projects, updating the address in one record requires updating it in all other records as well. Failure to do so results in inconsistent data, which is an update anomaly.

## Anomalies and Software Design Princpiles Analogies

Update anomaly ~ dont repeat yourself.

Insert anomaly ~ coupling.

Delete anomaly ~ single responsibility principle.

## Decomposition Theorem

The split of relations is guaranteed to be lossless if the intersection (the shared set attributes) of the attributes of the new tables is a key of at least one of them.

## Multivalued Dependencies

Occur in a relational database when there is a relationship between attributes that allows multiple rows to be associated independently of each other. An MVD is a more complex form of dependency than the functional dependency typically addressed in the lower normal forms. A multivalued dependency is considered trivial if the attribute(s) on the left side of the arrow and the attribute(s) on the right side of the arrow together make up all the attributes in the table.

## Normal Forms

> **First Normal Form** ~ **1NF**

Each table cell should contain a single value, and each record needs to be unique, order of rows should not be used to convey information.

First level of database normalization that a database table must satisfy:
- Using row order to convey information is not permitted.
- Mixing data types within the same column is not permitted.
- Having a table without a primary key is not permitted.
- Several values per cell is not permitted.

> **Second Normal Form** ~ **2NF**

Each non-key attribute must depend on the entire primary key.

The table is in 1NF and all non-key attributes are fully functional dependent on the primary key.

> **Third Normal Form** ~ **3NF**

Every non-key attribute in a table should depend on the key, the whole key, and nothing but the key.

The table is in 2NF and all the attributes are functionally independent of any other non-primary-key attributes.
3NF unlike BCND does preserve all functional dependencies, normalization does not lead to losing any of FDs.

> **Boyce-Codd Normal Form** ~ **BCNF**

Every ( not only non-key ) attribute in a table should depend on the key, the whole key, and nothing but the key.

With the exception of trivial functional every functinal dependency in a table must be a dependency on a superkey.
A stricter version of 3NF where for every dependency X → Y, X should be a superkey.
BCNF unlike 3NF does not preserve all functional dependencies, some could be lost during normalization.

Example of relation in 3NF, but not in BCNF

```
Addresses( streetAddress, city, state, zip )
streetAddress, city, state → zip
zip → state
```

> **Fourth Normal Form** ~ **4NF**

There is no non-trivial multivalued dependencies on a non-key.

Multivalued dependencies occur in a relational database when there is a relationship between attributes that allows multiple rows to be associated independently of each other. An MVD is a more complex form of dependency than the functional dependency typically addressed in the lower normal forms. A multivalued dependency is considered trivial if the attribute(s) on the left side of the arrow and the attribute(s) on the right side of the arrow together make up all the attributes in the table.

> **Fifth Normal Form** ~ **5NF** ~ **PJNF**

The table is in 4NF and cannot be decomposed into any number of smaller tables without loss of data.

> **Domain-Key Normal Form** ~ **DKNF**

Every constraint on the table is a domain constraint or a key constraint.

> **Sixth Normal Form** ~ **6NF**

The table is in 5NF and has no temporal data anomalies.

## Data Lake
: ...

## Data Lakehouse
: ...

## Data Mesh
: method ...

## Data Fabric
: method ...

## Data base / Data Mesh / Data Warehouse / Data Lake
: ...

## Data Warehouse ~ EDW
: ...

## ETL ~ Extract Transform Load
: ...

## BI ~ Business Intelligence
: ...

## PAML ~ Prediction Analytic Machine Learning
: ...

## Column-oriented database / Row-oriented database
: ...

## Internal Sorting / External Sorting

> **Internal Sorting**

Sorting algorithms that work on data that entirely fits into the main memory (RAM) of a computer. These algorithms assume that all the data to be sorted can be held in the memory at one time for processing.

> **External Sorting**

Used for large data sets that do not fit into the main memory. It involves sorting data that resides on external storage devices, such as disk drives. This process requires the algorithm to read, process, and write data in chunks that the main memory can accommodate.

## Column-wide database ~ Big Table database

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

> **Example**

HBase, Google Big Table, Cassandra, ScyllaDB

## Graph DB
...

> **Example**

Neo4J, FlockDB

## Consistency in reads : Strict Consistence / Eventual Consistency / Causal consistency

> **Strict consistency** is a guarantee that any read operation on the data will always return the latest version of the data. In other words, if a data is updated, any subsequent read of that data will always return the latest version. Strict consistency is often achieved by locking data during updates, which can cause delays and potentially slow down the system.

> **Causal consistency** ensures that causally related operations are seen in a specific order by all nodes in the system, but does not necessarily require that all nodes see all operations in the same order. This means that there may be some operations that are seen in a different order by different nodes, as long as there is a causal relationship between them.

> **Eventual consistency** is a weaker form of consistency that allows for temporary inconsistencies to exist between replicas of the data, but guarantees that the replicas will eventually converge to the same value. This means that if a data is updated, there may be a delay before all replicas of the data are updated with the latest version. However, given enough time and no new updates, all replicas will eventually be updated and converge to the same value.

In summary, strict consistency guarantees immediate consistency at the expense of performance, while eventual consistency allows for temporary inconsistencies in exchange for higher performance and availability. Causal consistency strikes a balance between strong consistency and weak consistency, and is often used in distributed systems where strict consistency is not feasible due to performance or network limitations. Causal consistency provides strong ordering guarantees while eventual consistency provides weaker ordering guarantees but allows for more flexibility and scalability.

## Consistency in data

Consistency in data refers to the property of data being accurate and valid over time. It means that the data remains consistent in all copies of the database, even when it is updated or modified. In a consistent database, all data is correctly synchronized, and there are no conflicting or contradictory copies of the same data. Consistency ensures that data is reliable and can be trusted by users and applications. It is a fundamental aspect of database design and is achieved through various mechanisms such as transactions, locking, and replication.

## Durability of data storage

In the context of data storage and database systems, durability refers to the ability of a transaction to survive permanently in the event of a system failure. In other words, once a transaction has been committed, its changes must be stored and protected in a way that ensures they will not be lost or undone due to hardware or software failure.

There are typically two types of durability guarantees:

> **Volatile Durability**: In this level of durability, changes are written to volatile memory (such as RAM) before they are stored on disk. As a result, if the system fails before the changes are written to disk, they may be lost.

> **Non-Volatile Durability**: In this level of durability, changes are written directly to disk or other non-volatile storage before a transaction is considered to be complete. This guarantees that the changes will be retained even in the event of a system failure.

Most modern database systems provide some form of non-volatile durability, as it is considered to be a critical component of transaction processing.

## Atomicity : All-or-nothing atomicity / Atomicity with partial failure

> **All-or-nothing atomicity**: In this type of atomicity, a transaction is either completed in its entirety or not at all. If any part of the transaction fails, the entire transaction is rolled back and the database is left in the state it was in before the transaction began.

> **Atomicity with partial failure**: In this type of atomicity, a transaction can be partially completed even if some part of it fails. The completed part of the transaction is still committed to the database, while the failed part is rolled back.

## Document-based database
...

## OLTP DB / OLAP DB
: ...

## Relational database / Document-based database
: ...

## Entity Set ~ Entity Class ~ Entity Type / Entity ~ Entity Instance

> **Entity Set ~ Entity Class ~ Entity Type**

A set of similar or related entities, a set of entities that share the same attributes but have different sets of values for those attributes.

An entity set can be thought of as a table in a relational database, where each row represents an entity and each column represents an attribute. Sometimes in conversation, the term "entity" may be used to mean "entity set", which is consistent with the Barker taxonomy.

> **Entity ~ Entity Instance**

Any distinct, identifiable object or thing of interest, an instance that can contain various attributes to describe its properties.

Entities are usually physical objects like a person, a book, a car, or abstract concepts like a course or an idea.

## Weak / Strong Entity

> **Weak Entity**

Entity that cannot exist independently and relies on another, stronger entity for its identification. A weak entity does not have a primary key of its own but instead uses a foreign key in combination with some of its attributes to form a composite key.

> **Strong Entity**

Entity that can exist independently of other entities. It has a primary key, which uniquely identifies each of its instances. The primary key is composed of one or more attributes that are inherent to the entity.

> **Difference**

Independence: Strong entities are independent and have their own primary keys. Weak entities are dependent on other entities and use a combination of foreign keys and their attributes to form a composite key.

Existence: A strong entity does not need any other entity to exist in the database, whereas a weak entity's existence is contingent upon the existence of a related strong entity.

Identification: Strong entities are identified by their own primary key. Weak entities are identified by a composite key, which includes a foreign key linking them to a strong entity.

## ID-Dependent Weak Entity

Type of entity in database modeling that requires a strong entity for its identification and existence. Its primary key is a composite of its own attributes and the primary key of the related strong entity.

## Identifying Relationship

Type of relationship where a weak entity is associated with a strong entity, and this association is essential for the identification of the weak entity. In other words, the weak entity's existence and identity depend on the strong entity it is related to. Such weak entity is ID-Dependent weak entity.

## Has-A Relationship ~ Composition Relationship ~ Aggregation Relationship / Is-A Relationship

> **Has-A Relationship ~ Composition Relationship ~ Aggregation Relationship**

Also known as composition or aggregation, represents an association between two classes where one class is a part or member of another class. It indicates that one object "contains" or "possesses" another object.

Composition/Aggregation: One class (the container or owning class) contains or owns the other class (the contained or member class).

Dependency: The contained class is dependent on the container class for its existence (in the case of strong composition) or may exist independently (in the case of aggregation).

Example: In a class design, if a 'Car' class has an object of 'Engine', this is a "Has-A" relationship. A 'Car' has an 'Engine'.

> **Is-A Relationship ~ Inheritance Relationship**

Relationship where a subclass inherits from a superclass. It represents an "inheritance" relationship in object-oriented programming, indicating that one class (the subclass) is a type of another class (the superclass).

Inheritance: The subclass inherits attributes and methods from the superclass.

Subtyping: It implies that objects of the subclass can be treated as objects of the superclass.

Example: In a class hierarchy, if 'Dog' is a subclass of 'Animal', this is an "Is-A" relationship. Every 'Dog' is an 'Animal'.

"Is-A" is an inheritance relationship indicating that one entity is a specialized form of another. "Has-A" is a compositional relationship indicating that one entity contains or consists of other entities. In an "Is-A" relationship, the subclass can be substituted where the superclass is expected (polymorphism). In a "Has-A" relationship, the member class is not interchangeable with the container class.

## Subtype Discriminator

An attribute of a supertype entity used to determine to which subtype entity a particular instance of the supertype belongs. Essentially, it discriminates among the various subtypes that a supertype can have. Only exclusive inheritance could use subtype descriminator bacause in case of inclusive inheritance there could be more than one subtype entity inheriting supertype entity.

## Minimal Cardinality / Maximal Cardinality

> **Maximal Cardinality**

Maximum number of instances of one entity that can be associated with a single instance of another entity in a relationship.
In relational databases, the maximum cardinality of a relation is enforced by the uniqueness constraint on a foreign key, which effectively converts a many-to-one relationship. Maximum cardinality could be one or many, but not zero.

> **Minimal cardinality**

Minimum number of instances of one entity that must be associated with a single instance of another entity in a relationship. In relational databases, the minimum cardinality of a relation is enforced by the nullability constraint of a foreign key. A non-nullable constraint changes a zero-or-more relationship to a one-or-more relationship. Minimum cardinality could be zero or one, but not many.

> **Difference**

While maximal cardinality focuses on how many entity instances can be in a relationship, minimal cardinality focuses on how many must be in that relationship. Cardinality usually shortcut for Maximal Cardinality, not Minimal.

## Nuances

- When there are zero rows, all aggregation functions return null, except `count( * )`, which returns 0. However, `count(attribute)` behaves as expected.
- The `sum` function returns null, not zero, when applied to zero rows.
- The order of attributes in a `GROUP BY` clause does not affect the results.
- A universal quantifier can be implemented using `NOT EXISTS NOT`.
- Avoid using natural joins due to their implicit nature, which often leads to problems.
- Prefer outer joins over inner joins, unless there's a specific reason not to. Outer joins can help identify and mitigate issues in the data.
- In relational databases, the maximum cardinality of a relation is enforced by the uniqueness constraint on a foreign key, which effectively converts a many relationship to one relationship. Maximum cardinality could be one or many, but not zero.
- In relational databases, the minimum cardinality of a relation is enforced by the nullability constraint of a foreign key. A non-nullable constraint changes a zero-or-more relationship to a one-or-more relationship. Minimum cardinality could be zero or one, but not many.
- While possible, a mandatory many-to-many relationship is usually avoided because it can complicate database operations and does not typically align with the real-world scenarios that the database is intended to model. You cannot insert an entity in one table without already having a related entity in the other table, and vice versa. This can make the initial population of the database very difficult.
- A join can be conceptualized as a Cartesian product followed by a selection operation.
- BCNF unlike 3NF does not preserve all functional dependencies, some could be lost during normalization.

## Characteristics of a System

> **[Resilience](https://www.youtube.com/watch?v=NIy9HMRlpjQ)**
Фbility to handle and recovery from failure gracefully.

> **Idempotent**
An operation that will produce the same results if executed once or multiple times.

> **CAP Theorem**
States that any distributed data store can provide only two of the following three guarantees.

<!-- ## Tags legend -->
<!-- - ( _:movie_camera:_ ) - video material -->
<!-- - ( _short_ ) - short overview -->
