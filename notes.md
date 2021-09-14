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

### CHAPTER 2

### QUIZ What to Know Before You Model

Problem:

Which of the following should you keep in mind when you design a data model with MongoDB?
Attempts Remaining:∞Unlimited Attempts

Check all answers that apply:

- [X] MongoDB supports ACID with the document model and with transactions.
- [X] The document model encourages keeping related information together.
- [X] - MongoDB is a distributed database.

### Flexible Methodology for Data Modeling

- Emphasis on workload, not on ER diagram
- Solution depends on workload
- Normalization  vs simplicity or performance.
- Flexible. Three phasses.
- Identify the worlokad. Size data, quantify ops, qualify ops.
- Model relationshups. Embed or link.
- Apply patterns if possible.

### QUIZ Flexible Methodology for Data Modeling

Which are the three phases of our data modeling methodology?

Check all answers that apply:

- [X] Describe the Workload.
- [ ] Write the Application Code.
- [X] Model the Relationships.
- [X] Apply Patterns.
- [ ] Draw an Entity-Relationship Diagram.

### Describing a workload

- First step of our methodology.
- List of operations, queries. For example, Coffee to deliver to stores. Quantify amount. Qualify the time, is it critial? What is the latency needed? What is the writeConcern needed? From which node to read?
- Is it a critical write?
- Usually one or two operations will stand out
- Latest version: account information, password.
- Staleness acceptable: reviews, ratings, list of restaurants
  
### QUIZ Describing a Workload

Problem:

Which one of the following is the best reason to describe the workload as the first phase of the methodology?
Attempts Remaining:∞Unlimited Attempts

- [ ] There is only one solution to data normalization.
- [ ] A solution for a huge amount of data requires an entity relationship diagram.
- [X] Different workloads could lead to different data model solutions.
- [ ] Because you want to apply schema design patterns.

### QUIZ Describing a Workload Quiz 2

Which of the following would be a qualitative aspect of a write operation?
Attempts Remaining:∞Unlimited Attempts

Choose the best answer:

- [ ] The operation happens 1000 times per second.
- [X] The operation requires a durability of "majority."
- [ ] The data written should be destroyed in 1 year.
- [ ] The operation must be acknowedged back to the client in 10 ms.

### EMBEDDING VS REFERENCING

- Embedding is placing the child into the parent
- Referencing, uses a unique idenifier
- Reference for 1 to many
- Prefer embedding over referencing
- Embed: for integrity, for data deleted together
- Reference: When the many is considerably large
- Ref: For integrity on write operations many-many
- Ref: when a piece is used, but not the other one and memory is an issue.

### QUIZ Embedding vs Referencing

Problem:

Which of the following criteria influence the choice of embedding instead of referencing a given relationship?
Attempts Remaining:∞Unlimited Attempts

Check all answers that apply:

- [X] The two entities are always read together.
- [X] The two entities have a one-to-many relationship and are always modified together.
- [ ] One entity can be related to 10 million entities in the second table.

### QUIZ Embedding vs Referencing Quiz 2

Problem:

The queries on a application are mostly on users. In other words, it user-centric.

Each user can have many addresses. The addresses and the user are always read or updated together.

How should you model the relationship between the user and the addresses in MongoDB?

Attempts Remaining:∞Unlimited Attempts

Choose the best answer:

- [ ] The address document should reference a collection holding the user document.
- [X] The addresses should be embedded as an array in the user document.
- [ ] The user should be a subdocument in the address document.
- [ ] The user document should reference a collection holding the address documents.

### Applying patterns

- Schema design pattern
- Common language to express representation in your schema model

Some patterns:

- Computed pattern: Good for repetitive calculations.
- Bucket pattern: Most common on IOT. Data is grouped. One document per device per day, or per hour.
- Extended reference: Reference to another collection, but keeping the most frequent fields within the parent.
- Recipes to improve schemas.
- Some patterns may intruduce data staleness or data duplication.

### QUIZ Schema Design Patterns Quiz 1

Problem:

Which of the following are true statements about schema design patterns?
Attempts Remaining:∞Unlimited Attempts

Check all answers that apply:

- [ ] They help normalize the data model.
- [X] They are a common language to understand design intents.
- [X] They often are denormalizations or transformations to improve performance.

### QUIZ Schema Design Patterns Quiz 2

Problem:

How are schema design patterns used in modeling for MongoDB?
Attempts Remaining:∞Unlimited Attempts

Check all answers that apply:

- [ ] They normalize the data model.
- [X] They are applied when needed for a given use case
- [X] They are all applied to all use cases

### SCHEMA VALIDATION

- Constrains in your data
- Ensure field exists, are non nul, have a type, restrict some values.
- Uses JSON Schema
- Report: warning or error.
- Validate: new documents, existing.

### QUIZ

Schema Validation
Problem:

Which of the following can be validated through schema validation in MongoDB?
Attempts Remaining:∞Unlimited Attempts

Check all answers that apply:

- [X] A document has either one of two strict shapes.
- [X] Values are within a set of acceptable values for a given field.
- [ ] Documents in different collections have referential integrity.
- [X] Values have the right type for a given field.
  
### Sharding

- Process of splitting the DB into 2 or more parts.
- Scale a large data set horizontally. Instead of better servers.
- Allows to put data in different geographical regions.
- A DB is partitioned in several shard. The shards are based on a sharded key.
- Scale for read or for write.
- Scaling for write: choosing a key that will distribute the writes evenly among the shards.
- Scaling for read:
- Queries that don't use the shard key, won't scale, they will query all the shards
- Most dataset don't require shards
- Sharding for write or for read?
- Choose the best shard key.

### QUIZ Sharding

Problem:

Which one of the following actions permits to scale horizontally?
Attempts Remaining:∞Unlimited Attempts

Choose the best answer:

- [X] Add a shard to the cluster.
- [ ] Add more disk space.
- [ ] Add more memory to the servers.
- [ ] Move the cluster to Atlas in the Cloud.
- [ ] Add a member in the replica set.

### Data INTEGRITY

- Entity, refrential, domain, user-defined. (SQL)
- Unique primary key.
- Unique compound indexes.
- No foreign keys.
- Cascading deletes not supported.
- Document Validation with JSON Schema
- Change streams on write operations.
- Atlas triggers.

### QUIZ Data Integrity

Problem:

Which of the following are ways MongoDB helps keep the integrity of the data?
Attempts Remaining:∞Unlimited Attempts

Check all answers that apply:

- [ ] Cascading deletes are supported in the MongoDB database server.
- [X] Change streams can be used to create triggers to implement user-defined integrity checks.
- [X] The document model guarantees referential integrity between parent and child entities.

## CHAPTER 3

### Query languages

- MQL, mongo query language. Easy to handle, simple queries for CRUD.
- Aggregation, pipeline transformations. Composable, easy to debug. Designed by stages. For data processing.

### QUIZ Query Languages

Problem:

How are nested SQL queries interpreted to understand the query logic?
Attempts Remaining:∞Unlimited Attempts

Choose the best answer:

- [ ] bottom-to-top
- [ ] top-to-bottom
- [X] inside-out
- [ ] outer-to-inner

### QUIZ Query Languages Quiz 2

Problem:

How are MongoDB Aggregation Pipelines interpreted to understand the query logic?
Attempts Remaining:∞Unlimited Attempts

Choose the best answer:

- [ ] outer-to-inner
- [ ] bottom-to-top
- [X] top-to-bottom
- [ ] inside-out

### QUIZ Query Languages Quiz 3

Problem:

Which of the following are available query languages in MongoDB?
Attempts Remaining:∞Unlimited Attempts

Check all answers that apply:

- [ ] Structure Query Language (SQL)
- [X] MongoDB Aggregation Framework
- [ ] MongoDB MongoShell
- [X] MongoDB Query Language (MQL)

### QUIZ Query Languages Quiz 4

Problem:

Which are valid statements for SQL queries and for Aggregation queries?
Attempts Remaining:∞Unlimited Attempts

Check all answers that apply:

- [X] SQL uses nested statements.
- [ ] MongoDB Aggregations use nested stages.
- [X] MongoDB Aggregations uses sequential stages.
- [ ] SQL uses sequential statements without nesting.

### MongoDB query language

- Key-value pairs. Fields are stringified. Separated by comma.
- db.collection.find() can filter documents.
- Query operator can specify conditions in the query filter document.

### QUIZ MongoDB Query Language

Problem:

Which function in MQL is equivalent to the SELECT statement in SQL?
Attempts Remaining:∞Unlimited Attempts

Choose the best answer:

- [ ] query
- [ ] project
- [X] find
- [ ] count
- [ ] limit

### QUIZ MongoDB Query Language Quiz 2

Problem:

Which of the following functions exist both in SQL and MQL for queries?
Attempts Remaining:∞Unlimited Attempts

Check all answers that apply:

- [X] skip
- [X] limit
- [X] count

### QUIZ MongoDB Query Language Quiz 3

Problem:

Which function in MongoDB Query Language (MQL) is equivalent to the less than (<) operator in SQL?
Attempts Remaining:∞Unlimited Attempts

Choose the best answer:

- [X] $lt
- [ ] $lessthan
- [ ] <

### QUIZ MongoDB Query Language Quiz 4

Problem:

Which function in MongoDB Query Language (MQL) is equivalent to the ORDER BY operator in SQL?
Attempts Remaining:∞Unlimited Attempts

Choose the best answer:

- [ ] order by
- [X] sort
- [ ] order

### MONGODB AGGREGATION FRAMEWORK QUERY

- Complex queries.
- Doesn't require additional frameworks

SQL     MONGODB
SELECT      db.aggregate()
WHERE       $match
GROUP       $group
COUNT       $count
LIMIT       $limit
ORDER BY    $sort
JOIN        $lookup
UNION ALL   $unionWith

### QUIZ MongoDB Aggregation Framework Queries

Problem:

Which stage in the MongoDB Aggregation Framework is equivalent to WHERE clause in SQL's SELECT statement?
Attempts Remaining:∞Unlimited Attempts

Choose the best answer:

- [X] match
- [ ] count
- [ ] limit

### QUIZ MongoDB Aggregation Framework Queries Quiz 2

Problem:

Which stage in the MongoDB Aggregation Framework is equivalent to the ORDER BY function in SQL's SELECT statement?
Attempts Remaining:∞Unlimited Attempts

Choose the best answer:

- [X] sort
- [ ] order by
- [ ] limit
- [ ] count

### QUIZ MongoDB Aggregation Framework Queries Quiz 3

Problem:

Which stage in the MongoDB Aggregation Framework is equivalent to the LIMIT clause in SQL's SELECT statement?
Attempts Remaining:∞Unlimited Attempts

Choose the best answer:

- [ ] where
- [ ] count
- [ ] limit

### QUIZ MongoDB Aggregation Framework Queries Quiz 4

Problem:

Select the MongoDB Aggregation Framework pipeline that is equivalent to the following SQL statement:

'SELECT * FROM people WHERE status = "A" OR age = 50'

Choose the best answer:

```js
db.people.aggregate([ { $where: { $or: [ { status: { $eq: "A" } }, { age: { $eq: 50 } } ] } } ])
```

```js
db.people.aggregate([ { $match: { $or: [ { status: { $eq: "A" } }, { age: { $eq: 50 } } ] } } ])
```

This one ↓

```js
db.people.aggregate([ { $match: { $and: [ { status: { $eq: "A" } }, { age: { $eq: 50 } } ] } } ])
```

### Object mappers

- Code layer that Maps DB tables to objects.
- Not neccesary.
- Adds extra latency as a new layer.

### QUIZ Object Mappers

Problem:

Which are the following highlight the impact of an Object Mapper on a database?

Check all answers that apply:

- [ ] In MongoDB, you must index the created object representation.
- [X] In MongoDB, the data already represents the object so it can be sent without processing.
- [ ] In a relational database, you must index the created object representation.
- [X] In a relational database, it gathers data from multiple tables by performing joins to create the object.

### QUIZ Object Mappers Quiz 2

Problem:

What typically maps directly to an object?

Choose the best answer:

- [ ] A record in a RDBMS
- [X] A document in MongoDB

### QUIZ Code Samples

Problem:

Which programming languages can use the exact same query syntax for the conditions than the MongoDB shell?

Check all answers that apply:

- [ ] Java
- [X] Python
- [ ] .NET (CSharp)
- [X] Javascript (NodeJS)

### QUIZ Code Samples Quiz 2

Problem:

In translating a common MQL query to a coding language, our examples showed several common steps.

Which of the following translation steps was done for all the coding languages?

Attempts Remaining:∞Unlimited Attempts

Check all answers that apply:

- [X] Used a variable to hold the result of the query on the collection.
- [X] Used the MongoClient in the programming language to connect to the database.
- [ ] Used a variable to indicate an index to use when querying the collection.
- [X] Used a variable which referenced the collection we wanted to query.
- [X] Used a variable to hold the conditional / filter criteria for the query.

## CHAPTER 4

### QUIZ Providing High Availability

Problem:

Which of the following is the best definition of High Availability (HA)?
Attempts Remaining:∞Unlimited Attempts

Choose the best answer:

- [ ] The ability to scale a cluster
- [X] The capacity to serve operations, even in the event of failures or planned downtime
- [ ] The replication of the data to other servers

### Server Maintenance

- Upgrading Mongod
- Install OS
- fixing hardware
- challenge: Doing it with the less downtime possible.
- Replication is built in.
- If the primary fails, an automatic election will occur.
- Rolling upgrade: Puting down 1 server on the time for maintainance.
- Atlas: Auto scaling feature!
- No need to plan downtime window.
- Retryable writes

### QUIZ Server Maintenance

Problem:

What happens automatically in MongoDB that allows for server maintenance without downtime?
Attempts Remaining:∞Unlimited Attempts

Check all answers that apply:

- [ ] MongoDB automatically upgrades itself to the latest available version.
- [X] Failed write operations are retried automatically once by the MongoDB drivers.
- [X] A faulty Primary will be replaced by a new Primary by an automatic election.

### QUIZ Server Maintenance Quiz 2

What are the recommended steps to do maintenance on a Primary node without downtime?
Attempts Remaining:∞Unlimited Attempts

Check all answers that apply:

- [ ] Stop the application from interacting with the MongoDB cluster.
- [ ] Stop all the nodes in the replica set at the same time.
- [X] Step down the Primary node and wait for a Secondary node to take over as the new Primary.

### SCHEMA Migration

- SQL requires datetime.
- No downtime for migration.
- Migrations just reshape the documments.

### QUIZ Schema Migration

Problem:

Which of the following help achieve a no-downtime schema migration with MongoDB?
Attempts Remaining:∞Unlimited Attempts

Check all answers that apply:

- [X] The polymorphism aspect of having documents with different shapes within a collection.
- [X] Each document can carry its schema version number.
- [ ] Database replication allows us to update one node at the time

### MONGODB as a data Platform

### QUIZ MongoDB as a Data Platform

Problem:

Which of the following are tools within MongoDB's data platform ecosystem?
Attempts Remaining:∞Unlimited Attempts

Check all answers that apply:

- [X] MongoDB Charts
- [X] MongoDB BI Connector
- [ ] RDMBS server
- [X] MongoDB Compass
