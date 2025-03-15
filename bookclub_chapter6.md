## Partitioning (Chapter 6)

#### The What?

**Partitions Are:**
- **Small databases of their own**: Subsections of a larger database, operating semi-independently.
- **Normal Partitions**: Defined so each record (row, document) belongs to exactly one partition.
- **Small Databases**: Each partition functions like a mini-database, potentially supporting multi-partition operations.

---

### Key Terms:
- <br>**Node**: A server or system component that stores and processes its own chunk of data.
  - Nodes are typically assigned to manage specific partitions, enabling distributed processing. 
- <br>**Record**: An individual database entry (e.g., `Name: John, Age: 30, City: San Antonio`).
- **Skewed Partition**: When some partitions have disproportionately more data or queries than others, reducing efficiency.
- **Hot Spot**: A partition experiencing excessively high load, often due to skewed data or access patterns.
- **Key Range Partitioning**: Assigning each node a continuous range of keys (e.g., A–B on Node 1, C–D on Node 2).
  - Each node handles records within its designated range, enabling efficient range queries.
- **Hash of Key Partitioning**: Distributing records by applying a hash function to the key.
  - Scrambles key order, losing efficient range queries but improving load distribution.
- **Consistent Hashing**: A hash-based method where partition boundaries are chosen pseudorandomly to minimize data movement when nodes are added or removed.
  - Note: Rarely used in databases as originally defined; often just called hash partitioning.
- **Secondary Indexes**: Indexes for finding records by fields other than the primary key (e.g., search by `City` instead of `Name`).
  - Think of them as dynamic lookup tools for non-key attributes.
- **Local Index**: A secondary index specific to a node’s partition, covering only its local data.
  - Contrast with global indexes, which span all partitions.

---

### Notes

> **Usually combined with replication**: Partitions are often replicated across multiple nodes for fault tolerance.
> - Each record belongs to one partition, but copies may exist on different nodes (e.g., leader-follower model).


#### The Why?
- **Mainly scalability**: Partitioning allows handling large datasets and high query throughput.
  - Distributes data across multiple disks and query load across processors.
  - Enables scaling by adding nodes, assuming even distribution.

#### The How?
- **How can a database be distributed across many disks?**
  - Partition data into manageable chunks, each stored on a separate node’s disk(s).
- **How can a query load be distributed across many processors?**
  - Assign partitions to nodes; each node processes queries for its partitions independently.
  - For single-partition queries, throughput scales with node count.
- **How do you decide which records to store on which nodes?**
  - **Key Range Partitioning**: Assign records based on a sorted key range (e.g., timestamps, alphabetical).
    - Pros: Efficient range scans (e.g., all data from January).
    - Cons: Risk of hot spots (e.g., all writes to today’s partition).
  - **Hash of Key Partitioning**: Use a hash function to assign records to partitions.
    - Pros: Evenly distributes data, reducing hot spots.
    - Cons: Loses key ordering, making range queries inefficient.
- **How do you assign records to nodes randomly?**
  - Random assignment spreads data evenly but complicates reads.
    - Disadvantage: No way to know which node has a specific record without querying all nodes (scatter/gather).
    - Solution: Use key-based partitioning (range or hash) instead of pure randomness.
- **How do you monitor partitions to ensure they are not becoming skewed?**
  - **Bookkeeping**: Track partition sizes and query loads.
  - **Rebalancing**: Adjust partition assignments when skew or hot spots occur (e.g., move partitions between nodes).
  - **Skew Mitigation**: For hash partitioning, split hot keys by adding random prefixes (e.g., `key-01`, `key-02`).

#### The Complex:
- **Parallelizing large complex queries across many nodes:**
  - Break queries into stages executable on different partitions/nodes.
  - Example: In MPP (Massively Parallel Processing) databases, a query with joins and aggregations is split into parallel tasks.
  - Challenges: Coordinating results, managing latency, and handling multi-partition dependencies.

#### Keep in Mind:
- **Cassandra’s Compromise**:
  - Uses a compound primary key (e.g., `(user_id, update_timestamp)`).
  - Only the first part (`user_id`) is hashed to determine the partition.
  - Other parts (`update_timestamp`) are used for sorting within the partition.
  - Benefit: Efficient range queries within a user (e.g., all updates by `user_id` in a time range).
  - Trade-off: Range queries across the first column (e.g., all users) hit all partitions.

---

### Additional Insights

#### Partitioning Strategies:
- **Key Range Partitioning**:
  - Example: A print encyclopedia split by letter ranges (A–B, C–D).
  - Adaptive boundaries needed for even data distribution (e.g., HBase splits large partitions dynamically).
- **Hash Partitioning**:
  - Uses a hash function (e.g., MD5) to evenly distribute keys.
  - Avoids hot spots but scatters related keys, requiring scatter/gather for ranges.
- **Secondary Indexes**:
  - **Document-Partitioned (Local)**: Each partition maintains its own index.
    - Write: Updates only one partition.
    - Read: Scatter/gather across all partitions (e.g., MongoDB, Elasticsearch).
  - **Term-Partitioned (Global)**: Indexes partitioned by indexed value (e.g., `color:red`).
    - Write: Updates multiple partitions (slower, often asynchronous).
    - Read: Queries a single partition (faster).

#### Rebalancing:
- **Fixed Number of Partitions**: Predefine many partitions (e.g., 1,000 for 10 nodes), move them between nodes.
  - Pros: Simple, predictable.
  - Cons: Must guess future growth; large partitions slow rebalancing.
- **Dynamic Partitioning**: Split/merge partitions based on size (e.g., HBase, RethinkDB).
  - Pros: Adapts to data volume.
  - Cons: Single partition initially (all load on one node until split).
- **Proportional to Nodes**: Fixed partitions per node (e.g., Cassandra’s 256 per node).
  - Pros: Stable partition size as nodes increase.
  - Cons: Random splits may be uneven.

#### Request Routing:
- **Options**: 
  - Nodes forward requests (Cassandra gossip).
  - Routing tier (e.g., MongoDB mongos).
  - Client awareness (direct connection).
- **Coordination**: Often uses ZooKeeper to track partition-to-node mappings.

---
