# :mortar_board: High Performance Computing

### Concepts

##### Work

The total amount of computation that a particular task or algorithm involves.

This includes all the operations, like additions, multiplications, comparisons, etc. The work of a parallel computation is the total time it would take to execute on a single processor.

##### Span ~ Critical Path Length ~ Depth

The longest sequence of dependent computations in a parallel task.

In other words, it's the minimum time that the computation can take, even if you had an unlimited number of processors. This is because some tasks cannot begin until others have been completed.

##### Average Available Parallelism ~ AAP ~ Parallelism

Average amount of work that could potentially be executed concurrently during the execution of a program

```
AAP = ceil( W(n) / D(n) )
W(n) - work
D(n) - span
```

##### Span Law

No parallel algorithm can execute in less time than the span or depth of the computation graph.

```
Tp(n) >= D(n)
Tp(n) ~ time to compute
D(n) ~ span
```

No matter how many processors you have, the time it takes to execute a parallel program can never be less than the total time it takes to execute the longest chain (or span) of dependent calculations.

This is due to dependencies in the computation that create a 'critical path' through the computation graph, which must be executed serially. This law is a measure of the inherent limit to how much a computation can be sped up by parallelization, regardless of how many processors you have.

##### Work Law

No parallel algorithm can execute in time less than the work divided by the number of processors.

```
Tp(n) >= W(n) / P
Tp(n) ~ time to compute
W(n) ~ work
p ~ number of processors
```

In other words, even if you had an infinite number of processors, you cannot execute faster than the total work divided by the infinity. This law shows that the best-case scenario is that linear speedup can be achieved (time reduces proportionally with the increase in processors).

##### Brent's theorem

Given a parallel algorithm and work W (total computations), the algorithm can be executed on P processors in time Tp <= ( W - D ) / p + D, where D is the time complexity of the algorithm on an infinite number of processors (the critical path length).

```
Tp <= ( W - D ) / p + D
D ~ span
p ~ number of processors
```

This theorem highlights the trade-off between the number of processors used and the total amount of work done. It shows that even if an infinite number of processors are used, the total execution time can't be less than the time taken by the longest (critical) sequence of dependent computations, which is represented by D.

##### Speed Up

```
Sp(n) = Ts(n) / Tp(n) = Ws(n) / Tp(n)
Sp(n) >= P / ( Wp / Ws + P * D / Ws )
Ts(n) ~ time to compute sequentially
Tp(n) ~ time to compute in parallel
Ws(n) ~ work to compute
p ~ number of processors
D ~ span
```

##### Amdahl's Law

The speedup of a program using multiple processors in parallel computing is limited by the time needed for the sequential part of the program.

```
Speedup ≤ 1 / ( S + ( 1 - S ) / N )
Speedup is the factor by which the time to complete the task is reduced,
S is the proportion of execution time for the sequential part of the process,
N is the number of processors.
```

A key takeaway from Amdahl's law is that if a fraction of a program is serial and thus cannot be parallelized (let's call this fraction B), then the program's execution time cannot be improved beyond 1/B by just using parallelization. This limitation is often referred to as Amdahl's bottleneck. As such, even with an infinite number of processors and perfect load balancing, this inherently serial part of the program dictates a limit on the speedup that parallelization can achieve.

##### Ceiling / Flooring

```
ceil( a / b ) = floor( a + b - 1 / b )
ceil( a / b ) = floor( a - 1 / b ) + 1

floor( a / b ) = ceil( a - b + 1 / b )
floor( a / b ) = ceil( a + 1 / b ) - 1
```

##### Weak Scalability

System's ability to process fixed-size problem faster instead of processing increasingly larger problem sizes.

The condition for weak scalability is that when you increase the number of processors, you also have to increase the problem size proportionally, with the goal of keeping the workload per processor constant.

```
P = O( W_s / D )
W_s / P = Omega( D )
W_s ~ total work of sequential algorithm
D ~ span
```

##### Work Optimality

The total work done by the parallel algorithm is within a constant factor of the total work done by the best sequential algorithm.

In other words, a work optimal parallel algorithm does not do asymptotically more work than the best sequential algorithm.

```
W(n) = O( W_s(n) )
W(n) ~ total work of parallel algorithm
W_s(n) ~ total work of sequential algorithm
```

##### Decomposition Granularity: Coarse-Grained / Fine-Grained

Measure of the amount of computation in relation to communication or coordination between processes or tasks.

Coarse-Grained: A coarse-grained system is one in which the computation to communication ratio is high. This means that the tasks can perform a significant amount of computation without needing to interact with other tasks. This is beneficial for parallel computing as it reduces the overhead of communication between tasks and can increase efficiency.

Fine-Grained: In a fine-grained system, the computation to communication ratio is low. This means that tasks frequently need to interact with each other. While this can lead to more overhead due to the increased need for communication, fine-grained systems can provide better load balancing and can utilize parallel hardware more fully than coarse-grained systems.

The optimal level of granularity depends on several factors, including the nature of the computations being performed, the architecture of the parallel system, and the costs associated with communication or synchronization.

##### Decomposition: Structural / Functional

Functional Decomposition and Domain Decomposition are two different ways of structuring parallel computing tasks.

In **functional decomposition**, the problem is divided based on the computations that need to be performed, rather than on the data that is being processed. Each parallel task represents a specific function or computation that needs to be performed. The same function may be performed on different pieces of data, or different functions might be performed in parallel. For example, in a graphics rendering application, one task might be responsible for calculating lighting, another for handling physics, and so forth.

In **domain decomposition**, the problem is divided based on the data domain of the problem. Each parallel task performs the same operation but on different subsets of the data. This is often used in problems where the same operation needs to be performed on a large set of data. For example, in a weather simulation, the area being modeled might be divided into a grid, with each task responsible for simulating the weather in one cell of the grid.

The main difference between functional and domain decomposition lies in how the problem is divided: functional decomposition is based on the different computations or functions that need to be performed, while domain decomposition is based on splitting the data domain into subsets. The choice between functional and domain decomposition depends on the nature of the problem being solved and the characteristics of the data and computations involved.

##### Deadlock

Deadlock is a state in a multi-process system where a process cannot proceed because it needs to access a resource held by another process that is similarly waiting for a resource, creating a cycle of dependencies.

The four conditions necessary for a deadlock:

- Mutual Exclusion: This condition states that at least one resource must be held in a non-sharable mode, or else, the process holding the resource does not release it until it has finished its task.
- Hold and Wait: This condition states that a process must be holding at least one resource and waiting for additional resources that are currently being held by other processes.
- No Preemption: This condition states that a resource can be released only voluntarily by the process holding it, after that process has completed its task. It cannot be forcibly taken away from the process.
- Circular Wait: The fourth condition implies that there exists a set (possibly the set of all system processes) such that for each process in the set, it is waiting for a resource that the next process in the set holds.

##### Communication Attributes

- Latency
- Bandwidth
- Throughput
- Concurrency ~ Synchronicity
- Visibility ~ Explicitness

##### Latency of Communication

Delay between a sender sending a message and the receiver receiving it.

It's usually measured in units of time like milliseconds or microseconds. Latency can be affected by several factors, including the physical distance between sender and receiver, the quality of the transmission medium, and the number of hops (i.e., intermediate devices like routers or switches) that the message must pass through. In HPC, low latency is crucial, especially in systems that require frequent communication between tasks or nodes, as high latency can significantly reduce the performance of the system.

##### Bandwidth of Communication

Maximum amount of data that can be transferred in a specific period of time between nodes in a cluster or across a network.

It's usually measured in bits per second (bps), or its multiples (e.g., Mbps, Gbps). High bandwidth is desired in HPC to allow the rapid transfer of large volumes of data.

##### Throughput of Communication

Actual rate at which data is successfully transferred from one part of a system to another over a given period of time.

While bandwidth refers to potential capacity, throughput is what's actually achieved. It is influenced by factors like network congestion, system load, and the computational efficiency of the processes involved.

##### Concurrency ~ Synchronicity of Communication: Synchronous / Asynchronous

**Synchronous communication**, also known as blocking communication, is a method of exchanging information where a handshake process is involved.

In this approach, the sender initiates the communication and waits for the receiver to acknowledge receipt of the message before proceeding. This sequential operation ensures the completion of one process before the next one starts, hence the term "blocking".

**Asynchronous communication**, on the other hand, is also known as non-blocking communication.

It is a communication method where the sender doesn't have to wait for the receiver's acknowledgment before proceeding. The sender can continue with other tasks or computations while the communication is still in progress. This is beneficial as it allows for the interleaving of computation and communication, effectively utilizing resources and enhancing overall system performance.

##### Visibility ~ Explicitness of Communication

Level of control and awareness a programmer has over the process of data exchange within a parallel computing system.

It's a concept related to how communication mechanisms are exposed or hidden in the design of parallel programming models.

In Message Passing communication, the visibility is explicit, which means that the programmer has direct control over the communication process. They need to explicitly write code to send and receive messages between processes. This level of control allows for fine-tuning, making it potentially more efficient, but also requires a deeper understanding of communication mechanisms. The programmer must manage the data exchange, deciding when and where data is sent or received.

On the other hand, with the Data Parallel model, the communication visibility is implicit. The programmer doesn't need to write specific communication code as data exchanges are automatically handled by the system. The programmer simply specifies the parallel operations, and the underlying system decides when and how to exchange data to fulfill those operations. While this can make programming simpler and more streamlined, it may not be as efficient or flexible since the programmer does not have direct control over when communication occurs. In this model, communication is abstracted away, allowing the programmer to focus more on computation logic.

Visibility of communication is a crucial factor when choosing a programming model for parallel computing, as it directly influences programming complexity, control over efficiency, and potential performance optimization.

##### Bitonic Sequence

Sequence of numbers that first increases monotonically (either strictly or not), and then decreases monotonically. In other words, it's a sequence that first goes up, then goes down. Alternatively, it can be a sequence that first decreases, then increases.
