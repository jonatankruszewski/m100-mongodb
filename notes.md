# M100 - MongoDB for SQL Pros

## Chapter 1

### Introduction to the Course

- This course is for architects, developers

### MongoDB in five minutes

- Document based DB.
- Hard to understand
- Inneficient to pull data.
- MongoDB accomodates to the needs
- Fault tolerance is handled Tolerance.
- Scalable.
- Data near users.
- Atlas as a DAAS


### QUIZ MongoDB in Five Minutes

Problem:

Which of the following are some of the main features of MongoDB?
Attempts Remaining:∞Unlimited Attempts

Check all answers that apply:

- [X] MongoDB lets you move data where you need it, so you can keep data near users.
- [ ] The MongoDB query language is optimized to pull data from many collections at once.
- [X] Fault tolerance is natively built into MongoDB by keeping redundant copies of the same data on different servers.
- [X] Scalability allows to seamlessly scale across multiple servers to store and process data.

### Lecture: NoSQL Databases

- SQL: data growth on server improvement. Hardware couldn't keep up with the data explosion in the web
- 4 NOSQL: key/value. Graph, Column, Document.
- Key/value. Primary key gets you the ifnormaiton. DB can be partionad. Redundat data on servers. Automatic failovers.
- Graph. Limited access to primary Key. Data is polymorphoci.
- Column oriented. Great for analytics.
- Document oriented. Easy and natural representation. No complex mapping between DB and app
- Modern data is polymorphic.
- Modern apps need to be resilient and always up

### QUIZ NoSQL Databases

Problem:

Which are correct statements about NoSQL databases?
Attempts Remaining:∞Unlimited Attempts

Check all answers that apply:

- [ ] NoSQL database scale better vertically than traditional relational databases.
- [X] NoSQL databases were designed to scale large datasets horizontally.
- [X] Most NoSQL databases have built-in modern features like data redundancy and tolerance to failures.


### Lecture: Database Terminology

RDBMS Database vs. MongoDB Database

A traditional relational database is a set of tables.

In MongoDB, we also have a database, which is a set of collections.

RDBMS Table vs. MongoDB Collection

A table is a set of rows, while a MongoDB collection is a set of documents.
RDBMS Parent-Child Tables vs. MongoDB Nested Sub-Document or Array

A table has a relationship to other tables, relations like one-to-one, one-to-many, or many-to-many by linking attributes from both tables.

MongoDB can express the relationships between collections similarly. However, MongoDB has an additional feature, the ability to take the fields of child table and embed it with the parent table as a single collection.

This grouping leads to a data model with far fewer collections than the number of tables in the corresponding relational model.

RDBMS Index vs. MongoDB Index

In RDBMS, indexes are built on any number of columns in a table.

In MongoDB, because there is far less need to bring data together, indexes are mainly used for filtering and sorting, rarely for joining. This leads to lower memory usage for indexes.

Building an index on a set of fields in a collection is the equivalent of having an index that would be built on a set of tables.

And as for traditional relational databases, indexes in MongoDB are also the most important thing to look for to ensure excellent performance.

RDBMS Row vs. MongoDB Document

A row in a traditional relational database maps to a document in MongoDB.

However, a document is self-descriptive. A document includes the names of the columns for which it has data.

RDBMS Column vs. MongoDB Field

A column of a table translates to a field of a document.

The main difference is that each document can have a different list of fields, allowing for documents with different shapes (polymorphism) in a collection.

RDBMS Join vs. MongoDB Embedding, Linking, or $lookup

Joins are used in a relational database to get data from two or more tables.

With MongoDB, there is a $lookup operator to perform the same link between collections.

Additionally, some relationships are also expressed by embedding the child table in the parent table. For these relationship, there is no need to use the $lookup keyword, as the data is already pre-joined in the document. The document model makes things much natural and queries so much simpler.

RDBMS View vs. MongoDB Read-Only View or On-Demand Materialized View

Relational views are also available in MongoDB and are also called views.
RDBMS Multi-Record ACID Transaction vs. MongoDB Multi-Document ACID Transaction

Finally, the transactions you are used to in a traditional relational database are also available and named the same way in MongoDB. The code that uses MongoDB transactions is remarkably similar to what you are used to with a traditional relational database.

Because MongoDB can store data in one document that is traditionally stored across rows in different tables, the need for transactions is much less than in relational systems.

SQL/RDBMS Refreshers
Note that the following refreshers about SQL/RDBMS cover topics that are also applicable to MongoDB.

ACID

Atomicity, Consistency, Isolation, and Durability

High Availability

Ability to support applications through a group of servers to minimize down time.

Replication

Keeping many copies of each data piece on different servers by replicating the data to achieve high availability and fault tolerance

### Quiz DATABASE TERMINOLOGY

Problem:

Which of the following terms is used in MongoDB to map the concept of a row in RDBMS?
Choose the best answer:

- [ ] collection
- [ ] key
- [ ] row
- [ ] field
- [X] document

### Database Terminology Quiz 2

Problem:

Which of the following terms is used in MongoDB to map the concept of a table in RDBMS?
Choose the best answer:

- [ ] field
- [ ] key
- [ ] document
- [X] collection
- [ ] row

### Lecture: The Document Model

- Document: store data as field - data.
- Columns=> Field names. Field names appear on each document. Each document is self describing.
- int, long, float, decimal in BSON
- Sub-documents in array
- Information that should be together, keeps it together.

### Quiz The Document Model

Problem:

Which statements are good descriptions of the Document Model used in MongoDB?
Attempts Remaining:∞Unlimited Attempts

Check all answers that apply:

- [X] It is similar to maps in Java and dictionaries in Python.
- [X] It allows us to model one-to-one and one-to-many relationships.
- [ ] It is identical to JSON.

### Lecture: ACID with Transactions and Documents

- ACID. Transactions.
- To achieve data persistancy, w: majority
- Same implementation.

### Quiz ACID with Transactions and Documents

Problem:

Which of the following set of operations guarantee ACID data integrity?

Check all answers that apply:

- [X] Modify a field and array in a single document within a MongoDB transaction.
- [X] Modify two documents within a MongoDB transaction.
- [ ] Modify two documents without using a MongoDB transaction.
- [X] Modify a field and array in a single document without using a transaction.

### Lecture: Distributed Database Considerations

- Distributed systems.
- Many servers
- need to talk to each other
- Common deployments: Replica set / sharded cluster
- Replcia set: Sets of server that replicates data. High availability, data durability. Complete copy of the DB. One node will be a primary.
- Sharded cluster: group of replica sets. A sharded cluster with 3 shards, will probably have 9 nodes in total. Partition a DB
- Placing data closer to the user.
- Easier to scale.
- Higher risk of failures (more disks, more network connections)
- Less downtime
- Propagation between nodes take time
- Stronger durability
- Summary: great resiliency.

### Quiz Distributed Database Considerations

Problem:

What are the main reasons distributed systems behave differently than single server systems?

Check all answers that apply:

- [ ] More servers equate to more downtime.
- [X] Networks are a common point of failure.
- [X] Network speed is usually fast, but not instantaneous.

### Lecture: Read/Writes Operation Guarantees

- Consistency - Availability = partition
- Read concern, write concern.
- Write concerns. w:1, w:majority.
- Read concerns. Local, majority.
- Read preference. Default: primary. You can read also from 'nearest'

### Quiz Read/Writes Operation Guarantees
Problem:

Which one of the following are true about read/write preferences and concerns?

Check all answers that apply:

- [ ] The read preference tells the required durability requested for the read operation.
- [X] The read preference tells which server to read data from.
- [X] The write concern tells the required durability requested for the write operation.
- [ ] The write concern tells which server to write data to.
- [X] The read concern tells the required durability requested for the read operation.
