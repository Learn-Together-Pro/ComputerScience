# Key concepts of Systems Design

Key concepts of Systems Design, Distributed Systems, DevOps and DBMS.

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

## Geneal

Horizontal / Vertical scaling
: ...


High-level design / Low-level design
: High-level design : explains the architecture that would be used to develop a system. Low-level design is a component-level design process that follows a step-by-step refinement process, this process can be used for designing data structures, required software architecture, source code and ultimately, performance algorithms.

Column-based database / Row-based database
: ...

OLTP DB / OLAP DB
: ...

Relational database / Document-oriented database
: ...

Distributed consensus
: ...
Types: 2PC, 3PC, SAGA

Replication strategy
: ...

Split brain
: failure when more than single component believes it is a master

Sharding
: a database architecture pattern related to horizontal partitioning — the practice of separating one table’s rows into multiple different tables, known as partitions.

## Characteristics

[Resilience](https://www.youtube.com/watch?v=NIy9HMRlpjQ)
: ability to handle and recovery from failure gracefully.

Idempotent
: in computer science, the term is used more comprehensively to describe an operation that will produce the same results if executed once or multiple times.

CAP Theorem
: in theoretical computer science, the CAP theorem, states that any distributed data store can provide only two of the following three guarantees.

## Communication

Pub-Sub ~ Publish-Subscribe ~ Broker
: Implementation of publish-subscribe as a service. Conceptually it is message queue + namespace ~ channels ~ types of events.

Message queue
: Implementation of publish-subscribe as a service. Conceptually it is pub-sub with a single channel ~ type of event.

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
