# Questions for interview on DBMS

<!-- [:arrow_down: Tags legend](#tags-legend) at the end of the page. -->

## SQL :: Optimization

- Outline the procedure for optimizing an SQL query.
- Describe the sequence of operations in SQL statement execution.

## SQL :: General

- What are the definitions and examples of DDL and DML in SQL?
- Can you elucidate the differences between the DELETE and TRUNCATE statements in SQL?
- Can you elucidate the differences between the DELETE and DROP statements in SQL?
- For what reasons would one utilize the CASE statement in SQL, and could you provide an illustrative example?
- How do the DISTINCT clause and GROUP BY clause differ in their functionality?
- What are the essential principles to follow when employing the UNION operator in SQL queries?
- What are the distinctions between the UNION and UNION ALL operators?
- Describe the role of aggregate functions in SQL and enumerate various types with explanations.
- How do scalar functions differ from aggregate functions in SQL?
- What distinguishes COUNT(*) from COUNT(column) in terms of their output?
- Differentiate between the WHERE and HAVING clauses in the context of SQL queries.
- Which SQL syntax would be used to express a year in words?
- How can one convert a textual representation of a date, such as "22-05-2013", into a recognized date format in SQL?
- What function would you use to obtain yesterday's date in SQL, and can you provide an example?
- In SQL, if you have a FNAME column with entries like "James Bond", "Avraam Lincoln", and "Merlin Menson", which functions would you use to extract only the first name? Include an example.
- Define the MERGE statement in SQL and illustrate its application with an example.
- Which SQL operations are reversible with a rollback, and which are irreversible?
- What is the purpose of the `COALESCE` function in SQL?

## SQL :: Window Functions

- Can aggregate functions be repurposed as window functions in SQL, and if so, how is this achieved?
- Detail the differences among the ROW_NUMBER, RANK, DENSE_RANK and NTILE window functions in SQL.
- Detail the differences among the CUME_DIST and PERCENT_RANK window functions in SQL.
- Define Analytical functions in SQL.

## SQL :: Code

- What are the key differences between SQL and PL/SQL?
- Under what circumstances is a function not callable within a SELECT statement?
- Compare and contrast triggers with functions in SQL.
- Highlight the distinctions between SQL functions and procedures.
- Define the concept of a trigger in SQL.
- Explain the role of PRAGMA AUTONOMOUS TRANSACTION in SQL.

## SQL :: Join

- Describe the relationship between the cartesian product and the SQL JOIN operation.
- When would you utilize a Cross Join in SQL?
- Elucidate the differences among LEFT JOIN, RIGHT JOIN, FULL OUTER JOIN, and INNER JOIN.
- Explain the concept of Joins in SQL and list the various kinds of Joins that exist.
- What is the minimum number of Joins needed to connect 6 separate tables?

## SQL :: Constraints and Relationships

- Define Constraints in the context of SQL and enumerate the different types available.
- What is the maximum number of primary keys and unique keys allowed in a single SQL table?
- Delineate the differences among primary key, unique key, and foreign key constraints.
- What ranges of values are possible for minimal and maximal cardinality? Does this range vary?
- Identify which constraints affect the minimum cardinality and which influence the maximum cardinality. Is this consistent across all cases?

## SQL :: Subqueries

- Is repeatedly including the same subquery in a single query advisable? If not, what strategies can be employed to address this?
- Define subqueries and explain their possible applications.
- Can subqueries be assigned a name for reuse within the same SQL statement?
- Is there a method to make a subquery permanent?
- How do subqueries differ from Common Table Expressions (CTEs)?
- Contrast subqueries with views in SQL.
- Compare and contrast Common Table Expressions (CTEs) with views.
- Describe the distinctions between views and synonyms, providing examples.
- Compare views with materialized views in terms of functionality and usage.
- How to avoid creating a view if you need to add few request-time columns?

## Index

- Define indexes in the context of databases and explain their purpose.
- Enumerate the various types of indexes available in SQL databases.
- Contrast btree indexes with hash indexes in terms of structure and usage.
- Explain the purpose of a bloom filter index and provide an illustrative example.

## Normalization

- Discuss the benefits and drawbacks of data normalization and denormalization.
- Identify the normal form that ensures all functional dependencies are maintained. Which normal form fails to guarantee this?

###

- Can foreign key refer non-primary key? When? Yes, if it has unique constraint
- Can unqiue cooumn have duplicates? When? Only nulls.
- Can foreign key refer nullable key? Yes
- Can primary key field be changed?
