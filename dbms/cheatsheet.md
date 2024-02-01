# Cheat sheets

## SQL Join

![SQL Join](./cheatsheet/sql_join.jpg)

## Other SQL Join

![OTher SQL Join](./cheatsheet/other_sql_join.jpg)

## SQL Isolation Levels

![SQL Isolation Levels](./cheatsheet/sql_isolation_level.png)

## Many to Many in Relational DB

![Many to Many in Relational DB](./cheatsheet/erd_many_to_many_in_relational_db.jpg)

## Self-Referential Structure

![Self-Referential Structure](./cheatsheet/erd_self_referential.jpg)

## Exclusive / Inclusive Inheritance

```text
+-------------+                                             +-------------+
|   STUDENT   |                                             |   STUDENT   |
|-------------|                                             |-------------|
| StudentID   |                                             | StudentID   |
| LastName    |                                             | LastName    |
| FirstName   |                                             | FirstName   |
| isGradStudnt|                                             +-------------+
+-------------+                                                    |
        | isGradStudent                                            |
        |                                                          |
+-------------------+   +------------------+                 +-----------+
|  UNDERGRADUATE    |   |    GRADUATE      |                 |           |
|-------------------|   |------------------| +-------------------+   +------------------+
| StudentID         |   | StudentID        | |  HIKING_CLUB      |   |  SAILING_CLUB    |
| HighSchoolGPA     |   | UndergradGPA     | |-------------------|   |------------------|
| ScoreOnSAT        |   | ScoreOnGMAT      | | StudentID         |   | StudentID        |
+-------------------+   +------------------+ | DateDuesPaid      |   | DateDuesPaid     |
                                             | AmountPaid        |   | AmountPaid       |
                                             +-------------------+   +------------------+

(a) Exclusive Subtypes with Discriminator          (b) Inclusive Subtypes
```
