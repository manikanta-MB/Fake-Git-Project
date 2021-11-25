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
