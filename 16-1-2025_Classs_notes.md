# Class notes for 16/1/2025

We explored Neo4J and why graph databases are useful. 

In graph databases each node represent an entity and the relation between two entities is defined by edges.

Try neo4j for free - https://neo4j.com/

We also looked into the ACID properties seen by databases - 

**Atomicity:**
- A transaction is an indivisible unit. Either all operations within it are completed successfully, or none are.
- Example: In a bank transfer, the money must be deducted from one account and added to another. Both operations succeed, or neither happens.

**Consistency:**
- The database must transition from one valid state to another, maintaining all predefined rules and constraints.
- Example: If a table has a rule that a column must not have negative values, the database should ensure this after every transaction.

**Isolation:**
- Transactions are executed independently of each other. One transaction should not interfere with another.
- Example: Two users buying concert tickets at the same time should not end up buying the same seat due to overlapping transactions.

**Durability:**

- Once a transaction is committed, it remains permanent, even in the case of a system crash.
- Example: If a booking confirmation is made, the record will persist even if the server fails afterward.