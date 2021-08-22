[Home](README.md)

<br>

# Mongo and Mongoose


<br>

## Readings from [SQL vs NoSQL Database Differences Explained](https://www.thegeekstuff.com/2014/01/sql-vs-nosql-db/?utm_source=tuicool)

<br>

### `SQL` vs `NoSQL`: High-Level Differences

<br>

SQL                                               |  NoSQL
--------------------------------------------------|--------------------------------------------------
Are primarily called as Relational Databases (RDBMS) | Are primarily called as non-relational or distributed database
Are table based databases (represent data in form of tables which consists of n number of rows of data) | Are document based, key-value pairs, graph databases or wide-column stores (are the collection of key-value pair, documents, graph databases or wide-column stores which do not have standard schema definitions which it needs to adhered to)
Have predefined schema | Have dynamic schema for unstructured data
Are vertically scalable (scaled by increasing the horse-power of the hardware) |  Are horizontally scalable (scaled by increasing the databases servers in the pool of resources to reduce the load)
uses `SQL` ( structured query language ) for defining and manipulating the data | Queries are focused on collection of documents. Sometimes it is also called as `UnQL` (Unstructured Query Language)
Examples: MySql, Oracle, Sqlite, Postgres and MS-SQL |  Examples: MongoDB, BigTable, Redis, RavenDb, Cassandra, Hbase, Neo4j and CouchDb
Good fit for the complex query intensive environment |  Not good fit for complex queries
Are not best fit for hierarchical data storage | Fits better for the hierarchical data storage as it follows the key-value pair way of storing data similar to JSON data. 
You can manage increasing load by increasing the CPU, RAM, SSD, etc, on a single server | You can just add few more servers easily in your NoSQL database infrastructure to handle the large traffic
Are best fit for heavy duty transactional type applications, as it is more stable and promises the atomicity as well as integrity of the data | Are usedL for transactions purpose, it is still not comparable and sable enough in high load and for complex transactional applications.
Excellent support are available for all SQL database from their vendors | You still have to rely on community support, and only limited outside experts are available for you to setup and deploy your large scale NoSQL deployments
Emphasizes on ACID properties ( Atomicity, Consistency, Isolation and Durability) | Follows the Brewers CAP theorem ( Consistency, Availability and Partition tolerance)
Can be classified as either open-source or close-sourced from commercial vendors | Can be classified on the basis of way of storing data as graph databases, key-value store databases, document store databases, column store database and XML databases.

<br>

## Conclusion

<br>

- What kind of data is a good fit for an SQL database?
  - Non-hierarchical data storage

- Give a real world example.
  - MySQL

- What kind of data is a good fit a NoSQL database?
  - Hierarchical data storage

- Give a real world example.
  - MongoDB

- Which type of database is best for hierarchical data storage?
  - NoSQL

- Which type of database is best for scalability?
  - NoSQL databases are scaled by increasing the databases servers in the pool of resources to reduce the load

  <br>

- What does SQL stand for?
  - Structured Query Language

- What is a realational database?
  - A database that relies on relations between data inorder to retrieve data queries.

- What type of structure does a relational database work with?
  - Data in table structure

- What is a ‘schema’?
  - The requirements for what data can be stored in the tables.

- What is a NoSQL database?
  - NoSQL is a type of database that stores and retrieves data without needing to define its structure first.

- How does it work?
  - You query the data you need directly from collections instead of looking for relations between data.

- What is inside of a Mongo database?
  - It stores data as collections, where each collection is made of documents.

- Which is more flexible - SQL or MongoDB? and why.
  - MongoDB, it doesn't rely on relations between data, but on the keys you require.

- What is the disadvantage of a NoSQL databas
  - You can have duplicated data, and data needs to be updated everywhere when it changes.
  