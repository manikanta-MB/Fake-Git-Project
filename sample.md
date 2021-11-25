# SQL

## ACID Properties
In order to maintain consistency in a database, before and after the transaction, certain properties are followed. These are called ACID properties. 
#### 1.Atomicity 
It means that either the entire transaction takes place at once or doesn’t happen at all. There is no midway i.e. transactions happens partially.
Each transaction is considered as one unit and either runs to completion or is not executed at all. It involves the following two operations. 
 * **Abort:** If a transaction aborts, changes made to database are not visible. 
 * **Commit:** If a transaction commits, changes made are visible.

Atomicity is also known as the **All or nothing rule**. 

#### 2.Consistency
It means Database should be consistent before and after transaction.<br />
For example, if there are two accounts which are transaferring their amount. So Before and After a transaction, the sum of money of both accounts should be same.
Money should not go anywhere else except these two accounts.

#### 3.Isolation
This property ensures that multiple transactions can occur concurrently without leading to the inconsistency of database state. 
Transactions occur independently without interference. Changes occurring in a particular transaction will not be visible to any other transaction 
until that particular change in that transaction is written to memory or has been committed. 
This property ensures that the execution of transactions concurrently will result in a state that is equivalent to a state achieved 
when these were executed serially in some order. <br />
Every transaction should feel like they were running alone in server.

#### 4.Durability
This property ensures that once the transaction makes some changes to your database and those changes are commited, those changes should be there in database even if the 
system failure occurs after that transaction.

## CAP Theorem
The CAP theorem, originally introduced as the CAP principle, can be used to explain some of the competing requirements in a distributed system with replication. It is a tool used to make system designers aware of the trade-offs while designing networked shared-data systems. 

The three letters in CAP refer to three desirable properties of distributed systems with replicated data: consistency (among replicated copies), availability of the system for read and write operations) and partition tolerance in the face of the nodes in the system being partitioned by a network fault). 

The theorem states that networked shared-data systems can only strongly support two of the following three properties: 
#### 1.Consistency
Consistency means that the nodes will have the same copies of a replicated data item visible for various transactions. A guarantee that every node in a distributed cluster returns the same, most recent, successful write. Consistency refers to every client having the same view of the data. There are various types of consistency models. Consistency in CAP refers to sequential consistency, a very strong form of consistency. 
#### 2.Availability
Availability means that each read or write request for a data item will either be processed successfully or will receive a message that the operation cannot be completed. Every non-failing node returns a response for all read and write requests in a reasonable amount of time. The key word here is every. To be available, every node on (either side of a network partition) must be able to respond in a reasonable amount of time.
#### 3.Partition Tolerant
Partition tolerance means that the system can continue operating if the network connecting the nodes has a fault that results in two or more partitions, where the nodes in each partition can only communicate among each other. That means, the system continues to function and upholds its consistency guarantees in spite of network partitions. Network partitions are a fact of life. Distributed systems guaranteeing partition tolerance can gracefully recover from partitions once the partition heals.
