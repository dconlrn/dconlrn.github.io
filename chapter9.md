# Chapter 9 Consistency and Consensus

---

## Fault Tolerance in Distributed Systems

* The simplest way to handle faults in distributed systems is to let the entire service fail and show an error message to the user.
* A more robust approach is to implement fault tolerance, allowing the service to continue functioning correctly even when internal components fail.
* Common issues in distributed systems include packet loss, reordering, duplication, or delays; approximate clocks; and node pauses or crashes.

## Abstractions for Fault Tolerance

* Building fault-tolerant systems effectively involves creating general-purpose abstractions with useful guarantees that applications can rely on.
* This approach is similar to using transactions, which abstract away crashes, race conditions, and disk failures.
* One crucial abstraction for distributed systems is **consensus**, where all nodes agree on a specific outcome.
* Achieving reliable consensus despite network faults and process failures is a complex problem.

## Applications of Consensus

* Consensus can be used in various applications.
* In a database with single-leader replication, consensus can be used to elect a new leader if the current leader fails.
* Ensuring only one leader exists and that all nodes agree on the leader is critical to avoid **split brain**, a situation where multiple nodes believe they are the leader, potentially leading to data loss.

## Scope of Guarantees and Abstractions

* It's essential to understand the limitations of what distributed systems can and cannot guarantee in the face of faults.
* Research in distributed systems has extensively explored these limits through theoretical proofs and practical implementations.
* This chapter will provide an overview of these fundamental limits.

## Consistency Guarantees

* Replicated databases can exhibit timing issues, where different nodes may show different data at the same time due to varying write arrival times.
* This inconsistency occurs regardless of the replication method (single-leader, multi-leader, or leaderless).
* **Eventual consistency** is a common guarantee, meaning that if writes stop, all reads will eventually return the same value.
* Eventual consistency implies temporary inconsistency that resolves over time, assuming network faults are also eventually repaired.
* A better term for eventual consistency might be **convergence**.
* However, eventual consistency is a weak guarantee, providing no specific timeframe for convergence.
* Before convergence, reads might return any value or nothing.
* For example, a write followed immediately by a read might not return the written value if the read is routed to a lagging replica (see "Reading Your Own Writes" on page 162, which is not in the provided text).
* Eventual consistency can be challenging for application developers due to its difference from the behavior of variables in single-threaded programs.
* Applications working with eventually consistent databases must be aware of its limitations to avoid incorrect assumptions.
* Bugs related to eventual consistency can be subtle and may only appear during faults or high concurrency.
* Stronger consistency models exist but may come with performance or fault-tolerance trade-offs.
* Stronger guarantees can simplify application development by being easier to use correctly.
* Distributed consistency models share some similarities with transaction isolation levels but are mostly independent concerns.
* Transaction isolation focuses on avoiding race conditions from concurrent transactions, while distributed consistency focuses on coordinating replica states during delays and faults.

## Chapter Outline

* The chapter will first examine **linearizability**, a strong consistency model, and its advantages and disadvantages.
* Next, it will discuss **ordering events** in distributed systems, including causality and total ordering.
* Finally, it will explore **distributed transactions and consensus**, leading to solutions for the consensus problem.

## Linearizability

* Eventual consistency can be confusing when different replicas return different answers to the same query at the same time.
* **Linearizability** (also known as atomic consistency, strong consistency, immediate consistency, or external consistency) aims to provide the illusion of a single data copy.
* In a linearizable system, all clients see the same view of the data, eliminating concerns about replication lag.
* The core idea is to make the system appear as if all operations on the single data copy are atomic.
* Once a client successfully completes a write in a linearizable system, all subsequent reads must see the written value.
* Linearizability is a **recency guarantee**, ensuring that reads return the most up-to-date value, not from a stale cache or replica.

### Example of a Non-Linearizable System

* Figure 9-1 (not provided in the text) illustrates a non-linearizable sports website where Alice sees the final score while Bob, refreshing later, still sees the game ongoing due to a lagging replica.
* Bob's expectation that his later query should reflect at least the same information as Alice's earlier query highlights the violation of linearizability.

### What Makes a System Linearizable?

* The fundamental concept of linearizability is to simulate a single data copy.
* Figure 9-2 (not provided in the text) shows three clients concurrently reading and writing to a register `x` in a linearizable database.
* A **register** in this context represents a single key-value pair, a row, or a document.
* The diagram depicts client requests (start and end times) without showing database internals.
* Clients only know that their request was processed between sending and receiving the response, influenced by network delays.
* The example involves two operations:
    * `read(x) ⇒ v`: Client reads the value of register `x`, and the database returns `v`.
    * `write(x, v) ⇒ r`: Client sets register `x` to value `v`, and the database returns response `r` (ok or error).
* Initially, `x` is 0, and client C writes 1 to it. Clients A and B concurrently read the value.
* Client A's first read, occurring before the write, must return 0.
* Client A's last read, after the write completes, must return 1 in a linearizable system. The write is processed between its start and end, and the read starts after the write ends.
* Reads overlapping with the write might return 0 or 1, as the write's effect during the read is uncertain (these are **concurrent** operations).
* However, linearizability imposes a further constraint beyond concurrent reads returning either old or new values. A system where reads concurrent with a write can flip back and forth between old and new values is not linearizable.

### Additional Constraint for Linearizability

* Figure 9-3 (not provided in the text) illustrates the additional constraint: once any read returns the new value, all subsequent reads (by any client) must also return the new value.
* In a linearizable system, the value of `x` is considered to atomically flip from 0 to 1 at some point during the write operation.
* If client A reads the new value 1, any subsequent read by client B must also return 1, even if the write by C is still in progress. This reinforces the recency guarantee.

### Visualizing Linearizability with Timing Diagrams

* Figure 9-4 (not provided in the text) shows a more complex example with read, write, and compare-and-set (cas) operations.
* `cas(x, vold, vnew) ⇒ r`: Atomically sets `x` to `vnew` if its current value is `vold`; otherwise, it leaves `x` unchanged and returns an error.
* Each operation in the diagram has a vertical line indicating its effective execution time. These markers are connected sequentially, forming a valid sequence of reads and writes.
* The key requirement for linearizability in this visualization is that the lines connecting the operation markers always move forward in time (left to right), never backward. This ensures the recency guarantee.

### Details from Figure 9-4 Example

* Client B reads `x`, then D writes 0, then A writes 1. B's read returns 1, which is acceptable if the database processed D's write, then A's write, then B's read (even if the requests were sent in a different order due to network delays).
* B's read returns 1 before A receives confirmation of the write. This is also acceptable, as the read might have occurred after the write, but the confirmation to A was delayed.
* The model doesn't assume transaction isolation; C reads 1 and then 2 because B changed the value between the reads. cas operations (by B and C) succeed, while D's fails because the value of `x` is no longer 0 when processed.
* The final read by B (shaded) is not linearizable. It's concurrent with C's cas write (2 to 4). While returning 2 would be okay in isolation, client A has already read the new value 4 before B's read started. Thus, B cannot read an older value than A, violating linearizability.

### Formal Definition and Testing

* The formal definition of linearizability provides a more precise description.
* Testing for linearizability involves recording request and response timings and checking if they can be arranged into a valid sequential order (computationally expensive).

## Linearizability Versus Serializability

* Linearizability and serializability are often confused due to the shared idea of sequential ordering, but they are distinct guarantees.

### Serializability

* Serializability is a transaction isolation property for operations on multiple objects.
* It ensures that transactions behave as if they executed in some serial order, even if the actual execution was concurrent.
* The serial order doesn't need to match the actual execution order.

### Linearizability

* Linearizability is a recency guarantee for reads and writes on a single object (a register).
* It does not group operations into transactions and doesn't inherently prevent issues like write skew without additional mechanisms.

### Combination of Linearizability and Serializability

* A database can provide both serializability and linearizability, known as **strict serializability** or **strong one-copy serializability (strong-1SR)**.
* Implementations of serializability based on two-phase locking or actual serial execution are typically linearizable.
* However, serializable snapshot isolation (SSI) is not linearizable by design, as it reads from consistent snapshots that may not include the most recent writes.

## Relying on Linearizability

* Linearizability is crucial in scenarios where having an up-to-date, consistent view of data across all clients is essential for correctness.

### Locking and Leader Election

* Single-leader replication systems need to ensure only one leader exists to avoid split brain.
* Leader election often uses locks, which must be linearizable to ensure all nodes agree on the lock owner.
* Coordination services like Apache ZooKeeper and etcd are used for distributed locks and leader election, employing consensus algorithms to provide linearizable operations in a fault-tolerant manner.
* Implementing locks and leader election correctly involves subtle details (e.g., the fencing issue), and libraries like Apache Curator offer higher-level abstractions on top of ZooKeeper.
* A linearizable storage service forms the foundation for these coordination tasks.
* Distributed locking is also used at a finer granularity in some distributed databases like Oracle RAC, which uses linearizable locks per disk page shared by multiple nodes. This often requires a dedicated high-speed network for inter-node communication.

### Constraints and Uniqueness Guarantees

* Uniqueness constraints (e.g., usernames, email addresses, filenames) require linearizability to enforce correctly during concurrent writes.
* Enforcing uniqueness can be viewed as acquiring a "lock" on the unique identifier.
* Atomic compare-and-set operations are also relevant here, ensuring a value is set only if it hasn't been changed concurrently.
* Similar issues arise with other constraints like bank account balances, inventory levels, and seat bookings, where a single consistent, up-to-date value is needed.
* In some applications, loose constraint enforcement might be acceptable, potentially negating the need for linearizability (discussed in "Timeliness and Integrity" on page 524, not in the provided text).
* However, hard uniqueness constraints, common in relational databases, necessitate linearizability. Other constraint types (e.g., foreign key, attribute) can often be implemented without it.

### Cross-Channel Timing Dependencies

* The non-linearizability in the sports website example was only apparent due to the external communication channel (Alice telling Bob).
* Similar situations can occur in computer systems with multiple communication channels.
* Consider a website where users upload photos, and a background process resizes them using a message queue to instruct the resizer after the photo is written to a file storage service.
* If the file storage is not linearizable, a race condition can occur: the message queue might be faster than the storage replication.
* The resizer might fetch an old or non-existent version of the image, leading to permanent inconsistencies between the full-size and resized images.
* Linearizability in the file storage service prevents this race condition between the file storage and the message queue.
* This is analogous to the Alice and Bob example with two communication channels (database replication and the audio channel).
* While linearizability is a clear solution, alternative approaches (similar to "Reading Your Own Writes") exist if the additional communication channel is controlled, but they add complexity.

## Implementing Linearizable Systems

* Linearizability requires the system to behave as if there's a single data copy with atomic operations.
* The simplest (but not fault-tolerant) implementation is to indeed have only one data copy.
* The most common approach for fault tolerance is replication.

### Replication Methods and Linearizability

* **Single-leader replication (potentially linearizable):** Reads from the leader or synchronously updated followers can be linearizable. However, not all single-leader databases are linearizable due to design choices (e.g., snapshot isolation) or concurrency bugs. Relying on the leader for reads assumes correct leader identification. Failover with asynchronous replication can lose committed writes, violating both durability and linearizability.
* **Consensus algorithms (linearizable):** These algorithms, discussed later, resemble single-leader replication but include mechanisms to prevent split brain and stale replicas, enabling safe linearizable storage (e.g., ZooKeeper, etcd).
* **Multi-leader replication (not linearizable):** Generally not linearizable due to concurrent writes on multiple nodes and asynchronous replication, leading to potential write conflicts.
