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

## JOINS
A SQL Join statement is used to combine data or rows from two or more tables based on a common field between them. Different types of Joins are:

1. INNER JOIN
2. LEFT JOIN
3. RIGHT JOIN
4. FULL JOIN

#### 1.INNER JOIN
The INNER JOIN keyword selects all rows from both the tables as long as the condition satisfies. This keyword will create the result-set by combining all rows from both the tables where the condition satisfies i.e value of the common field will be same.
##### Syntax
```
SELECT table1.column1,table1.column2,table2.column1,....
FROM table1 
INNER JOIN table2
ON table1.matching_column = table2.matching_column;
```
![inner join](https://blog.codinghorror.com/content/images/uploads/2007/10/6a0120a85dcdae970b012877702708970c-pi.png)

#### 2. LEFT JOIN
This join returns all the rows of the table on the left side of the join and matching rows for the table on the right side of join. The rows for which there is no matching row on right side, the result-set will contain null. LEFT JOIN is also known as LEFT OUTER JOIN.
##### Syntax
```
SELECT table1.column1,table1.column2,table2.column1,....
FROM table1 
LEFT JOIN table2
ON table1.matching_column = table2.matching_column;
```
![left join](https://i.stack.imgur.com/VkAT5.png)

#### 3. RIGHT JOIN
RIGHT JOIN is similar to LEFT JOIN. This join returns all the rows of the table on the right side of the join and matching rows for the table on the left side of join. The rows for which there is no matching row on left side, the result-set will contain null. RIGHT JOIN is also known as RIGHT OUTER JOIN.
##### Syntax
```
SELECT table1.column1,table1.column2,table2.column1,....
FROM table1 
RIGHT JOIN table2
ON table1.matching_column = table2.matching_column;
```
![right join](http://www.databasejournal.com/img/jk_JustSQL4_image004.jpg)

#### 4. FULL JOIN
FULL JOIN creates the result-set by combining result of both LEFT JOIN and RIGHT JOIN. The result-set will contain all the rows from both the tables. The rows for which there is no matching, the result-set will contain NULL values.
##### Syntax
```
SELECT table1.column1,table1.column2,table2.column1,....
FROM table1 
FULL JOIN table2
ON table1.matching_column = table2.matching_column;
```
![full join](https://i.stack.imgur.com/3Ll1h.png)

## Aggregate functions
In database management an aggregate function is a function where the values of multiple rows are grouped together as input on certain criteria to form a single value of more significant meaning.

Following are some of the basic Aggregate functions,
```
1) Count()
2) Sum()
3) Avg()
4) Min()
5) Max()
```
Now let us understand each Aggregate function with a example:
```
Id     Name     Salary
-----------------------
1       A        80
2       B        40
3       C        60
4       D        70
5       E        60
6       F        Null
```
#### 1. Count()
**Count(*):** Returns total number of records .i.e 6.<br />
**Count(salary):** Return number of Non Null values over the column salary. i.e 5.<br />
**Count(Distinct Salary):**  Return number of distinct Non Null values over the column salary .i.e 4.

#### 2. Sum()
**Sum(salary):**  Sum all Non Null values of Column salary i.e., 310. <br />
**Sum(Distinct salary):** Sum of all distinct Non-Null values i.e., 250.

#### 3. Avg()
**Avg(salary)** = Sum(salary) / Count(salary) = 310/5. <br />
**Avg(Distinct salary)** = Sum(Distinct salary) / Count(Distinct Salary) = 250/4.

#### 4. Min()
**Min(salary):** Minimum value in the salary column except NULL i.e., 40.

#### 5. Max()
**Max(salary):** Maximum value in the salary i.e., 80.

## Normalization
Normalization is the process of minimizing redundancy from a relation or set of relations. Redundancy in relation may cause insertion, deletion, and update anomalies. So, it helps to minimize the redundancy in relations. Normal forms are used to eliminate or reduce redundancy in database tables.

#### 1.First Normal Form
If a relation contain composite or multi-valued attribute, it violates first normal form or a relation is in first normal form if it does not contain any composite or multi-valued attribute. A relation is in first normal form if every attribute in that relation is singled valued attribute.

##### Example
```
ID   Name   Courses
------------------
1    A      c1, c2
2    E      c3
3    M      C2, c3
```
In the above table Course is a multi-valued attribute so it is not in 1NF.

Below Table is in 1NF as there is no multi-valued attribute
```
ID   Name   Course
------------------
1    A       c1
1    A       c2
2    E       c3
3    M       c2
3    M       c3
```
#### 2.Second Normal Form
To be in second normal form, a relation must be in first normal form and relation must not contain any partial dependency. A relation is in 2NF if it has **No Partial Dependency**, i.e., no non-prime attribute (attributes which are not part of any candidate key) is dependent on any proper subset of any candidate key of the table.

**Partial Dependency** – If the proper subset of candidate key determines non-prime attribute, it is called partial dependency.

##### Example
```
STUD_NO            COURSE_NO        COURSE_FEE
1                     C1                  1000
2                     C2                  1500
1                     C4                  2000
4                     C3                  1000
4                     C1                  1000
2                     C5                  2000
```
COURSE_FEE would be a non-prime attribute, as it does not belong to the one only candidate key {STUD_NO, COURSE_NO} ;
But, COURSE_NO -> COURSE_FEE, i.e., COURSE_FEE is dependent on COURSE_NO, which is a proper subset of the candidate key. Non-prime attribute COURSE_FEE is dependent on a proper subset of the candidate key, which is a partial dependency and so this relation is not in 2NF.

To convert the above relation to 2NF,
we need to split the table into two tables such as :

Table 1: STUD_NO, COURSE_NO<br />
Table 2: COURSE_NO, COURSE_FEE

```
       Table 1                                    Table 2
STUD_NO            COURSE_NO          COURSE_NO                COURSE_FEE     
1                 C1                  C1                        1000
2                 C2                  C2                        1500
1                 C4                  C3                        1000
4                 C3                  C4                        2000
4                 C1                  C5                        2000        
```

#### 3.Third Normal Form
A relation is in third normal form, if there is no transitive dependency for non-prime attributes as well as it is in second normal form.
A relation is in 3NF if at least one of the following condition holds in every non-trivial function dependency X –> Y

1. X is a super key.
2. Y is a prime attribute (each element of Y is part of some candidate key).

![3NF table](https://media.geeksforgeeks.org/wp-content/cdn-uploads/Normalisation_normalforms_3.png)

**Transitive dependency** – If A->B and B->C are two FDs then A->C is called transitive dependency.
##### Example
In relation STUDENT given in Table 4,<br />
FD set: {STUD_NO -> STUD_NAME, STUD_NO -> STUD_STATE, STUD_STATE -> STUD_COUNTRY, STUD_NO -> STUD_AGE}
Candidate Key: {STUD_NO}

For this relation in table 4, STUD_NO -> STUD_STATE and STUD_STATE -> STUD_COUNTRY are true. So STUD_COUNTRY is transitively dependent on STUD_NO. It violates the third normal form. To convert it in third normal form, we will decompose the relation STUDENT (STUD_NO, STUD_NAME, STUD_PHONE, STUD_STATE, STUD_COUNTRY_STUD_AGE) as:

STUDENT (STUD_NO, STUD_NAME, STUD_PHONE, STUD_STATE, STUD_AGE)<br />
STATE_COUNTRY (STATE, COUNTRY)

#### 4. Boyce-Codd Normal Form (BCNF)
A relation is in BCNF, if it is in 3NF and it should not contain the following dependency,<br />
Non-prime/Prime Attribute   --->  Prime Attribute.

## Indexes
An index is a schema object. It is used by the server to speed up the retrieval of rows by using a pointer. It can reduce disk I/O(input/output) by using a rapid path access method to locate data quickly. An index helps to speed up select queries and where clauses, but it slows down data input, with the update and the insert statements. Indexes can be created or dropped with no effect on the data.

#### Creating an Index
##### Syntax
```
 CREATE INDEX index_name
 ON table_name column_name;
 ```
 ##### For multiple columns
 ##### Syntax
 ```
 CREATE INDEX index_name
 ON table_name (column1,column2,.....);
 ```
 #### Unique Indexes
 Unique indexes are used for the maintenance of the integrity of the data present in the table as well as for the fast performance, it does not allow multiple values to enter into the table. 
 ##### Syntax
 ```
 CREATE UNIQUE INDEX index_name
 ON table_name column_name;
 ```
 
 #### When should indexes be created
* A column contains a wide range of values.
* A column does not contain a large number of null values.
* One or more columns are frequently used together in a where clause or a join condition.

#### When should indexes be avoided
* The table is small.
* The columns are not often used as a condition in the query.
* The column is updated frequently.

#### Removing an Index
To remove an Index from your database, just use the following command,
```
DROP INDEX index_name
```
To drop an index, you must be the owner of the index or have the **DROP ANY INDEX** privilege. 

#### Altering an Index
To modify an existing table’s index by rebuilding, or reorganizing the index.
```
ALTER INDEX index_name 
ON table_name REBUILD;
```
#### Confirming Indexes
You can check the different indexes present in a particular table given by the user or the server itself and their uniqueness. 
##### Syntax
```
select * from USER_INDEXES;
```
It will show you all the indexes present in the server, in which you can locate your own tables too.

#### Renaming an Index
 You can use the system stored procedure sp_rename to rename any index in the database.
##### Syntax
```
EXEC sp_rename  
   index_name,  
   new_index_name,  
   N'INDEX'; 
```
## Transactions
Transactions group a set of tasks into a single execution unit. Each transaction begins with a specific task and ends when all the tasks in the group successfully complete. If any of the tasks fail, the transaction fails. Therefore, a transaction has only two results: **success** or **failure**.
A database transaction, by definition, must be atomic, consistent, isolated and durable.
### How to implement transactions using SQL
Following commands are used to control transactions. It is important to note that these statements cannot be used while creating tables and are only used with the DML Commands such as – INSERT, UPDATE and DELETE. 
#### 1.BEGIN TRANSACTION
It indicates the start point of an explicit or local transaction. 
##### Syntax
```
BEGIN TRANSACTION transaction_name ;
```
#### 2.SET TRANSACTION
Places a name on transaction.
##### Syntax
```
SET TRANSACTION [ READ WRITE | READ ONLY ];
```
#### 3.COMMIT
 If everything is in order with all statements within a single transaction, all changes are recorded together in the database is called **committed**. The COMMIT command saves all the transactions to the database since the last COMMIT or ROLLBACK command.
 ##### Syntax
 ```
 COMMIT;
 ```
 ##### Example
 ![sample_table](https://media.geeksforgeeks.org/wp-content/uploads/1-38.jpg)
 
 Following is an example which would delete those records from the table which have age = 20 and then COMMIT the changes in the database. 
 ##### Queries:
 ```
DELETE FROM Student WHERE AGE = 20;
COMMIT;
```
##### Output:
Thus, two rows from the table would be deleted and the SELECT statement would look like, 
![output_table](https://media.geeksforgeeks.org/wp-content/uploads/2-34.jpg)

#### 4.ROLLBACK
If any error occurs with any of the SQL grouped statements, all changes need to be aborted. The process of reversing changes is called rollback. This command can only be used to undo transactions since the last COMMIT or ROLLBACK command was issued.
##### Syntax
```
ROLLBACK;
```
##### Example
From the above example Sample table1,<br />
Delete those records from the table which have age = 20 and then ROLLBACK the changes in the database.
##### Queries:
```
DELETE FROM Student WHERE AGE = 20;
ROLLBACK;
```
##### Output:
![output_table](https://media.geeksforgeeks.org/wp-content/uploads/3-23.jpg)

#### 5.SAVEPOINT
 creates points within the groups of transactions in which to ROLLBACK. <br />
A SAVEPOINT is a point in a transaction in which you can roll the transaction back to a certain point without rolling back the entire transaction.
##### Syntax for creating a savepoint:
```
SAVEPOINT SAVEPOINT_NAME;
```
This command is used only in the creation of SAVEPOINT among all the transactions.<br />
In general ROLLBACK is used to undo a group of transactions.
##### Syntax for rollback to a savepoint:
```
ROLLBACK TO SAVEPOINT_NAME;
```
you can ROLLBACK to any SAVEPOINT at any time to return the appropriate data to its original state. 

#### 5.RELEASE SAVEPOINT
This command is used to remove a SAVEPOINT that you have created. 
```
RELEASE SAVEPOINT SAVEPOINT_NAME;
```
Once a SAVEPOINT has been released, you can no longer use the ROLLBACK command to undo transactions performed since the last SAVEPOINT.

## Locking Mechanism
Locking mechanisms are a way for databases to produce sequential data output without the sequential steps. The locks provide a method for securing the data that is being used so no anomalies can occur like lost data or additional data that can be added because of the loss of a transaction.
### Problems that Locks solve
* **Lost Update Problem:** A lost update occurs when two different transactions are trying to update the same column on the same row within a database at the same time.
* **Temporary Update Problem:** Temporary update or dirty read problem occurs when one transaction updates an item and fails.
* **Incorrect Summary Problem:** Incorrect Summary issue occurs when one transaction takes summary over the value of all the instances of a repeated data-item, and second transaction update few instances of that specific data-item.
* **Phantom Reads:** A lower isolation level increases the ability of many users to access the same data at the same time, but increases the number of concurrency effects (such as dirty reads or lost updates) users might encounter.

### Different Types of Locks
There are three primary types of locks that are used in a database.
* **Read Locks:** These types of locks make it so that data can only be read. Depending on the database system and restrictions on the read lock, this can make it so only one user can read the data to allowing every user access to reading the data but not being able to modify anything. The read lock can be applied to a single row, a section of rows, or an entire table. This can also be dependent on the type of database system that is being used that could limit the amount of data that can be locked for reading.
* **Write Locks:** This type of lock is used for updates in the database system. When this lock is applied it prevents any other transactions from changing the records that are being accessed. This does allow transactions to read the data before it is modified and the changes are made permanent.
* **Exclusive Write Locks:** This type of lock is similar to a write lock. The only difference is that with an exclusive write lock, the only things that can look at the data or modify the data is the original transaction. No other transaction can read the data while this lock is applied.
* There are also many other locks that signal intention to request another type of lock. These locks are called multi-level-locks. This is useful to show other transactions what types of locks the transaction has throughout the hierarchy of data levels.

#### Multi-level Locks:
* **Update Lock:** Signals intention to request an exclusive lock in the near future.
* **IS Lock:** Signals intent to request shared (read) lock in the near future.
* **IX Lock:** Signals intent to request an exclusive (write) lock in the near future.

#### Two-Phase Locking Protocol
The Two Phase Commit is designed to coordinate the transactions of the requests to the system. The idea behind the protocol is to produce serialized results from a non-serialized system. This protocol requires that each transaction issues lock and unlock requests in two phases: the shrinking phase and the growing phase. During the growing phase transactions may obtain locks, but cannot release any. During the shrinking phase transactions may release locks but may not obtain any new locks. By following this protocol any update problems with the transaction can be detected and one transaction gets rolled back. It also can raise the priority of the affected transaction to prevent a repeat of the problem.
