# MongoDB
### Concepts of NoSQl. Advantages and Features.
NoSQL is a type of database management system (DBMS) that is designed to handle and store large volumes of unstructured and semi-structured data. Unlike traditional relational databases that use tables with pre-defined schemas to store data, NoSQL databases use flexible data models that can adapt to changes in data structures and are capable of scaling horizontally to handle growing amounts of data.

### Key Features of NoSQL:

1. **Dynamic schema:** NoSQL databases do not have a fixed schema and can accommodate changing data structures without the need for migrations or schema alterations.
2. **Horizontal scalability:** NoSQL databases are designed to scale out by adding more nodes to a database cluster, making them well-suited for handling large amounts of data and high levels of traffic.
3. **Document-based:** Some NoSQL databases, such as MongoDB, use a document-based data model, where data is stored in a schema-less semi-structured format, such as JSON or BSON.
4. **Key-value-based:** Other NoSQL databases, such as Redis, use a key-value data model, where data is stored as a collection of key-value pairs.
5. **Column-based:** Some NoSQL databases, such as Cassandra, use a column-based data model, where data is organized into columns instead of rows.
6. **Distributed and high availability:** NoSQL databases are often designed to be highly available and to automatically handle node failures and data replication across multiple nodes in a database cluster.
7. **Flexibility:** NoSQL databases allow developers to store and retrieve data in a flexible and dynamic manner, with support for multiple data types and changing data structures.
8. **Performance:** NoSQL databases are optimized for high performance and can handle a high volume of reads and writes, making them suitable for big data and real-time applications.

### Advantages of NoSql
There are many advantages of working with NoSQL databases such as MongoDB and Cassandra. The main advantages are high scalability and high availability.
1. **High scalability:** NoSQL databases use sharding for horizontal scaling. Partitioning of data and placing it on multiple machines in such a way that the order of the data is preserved is sharding.NoSQL can handle a huge amount of data because of scalability.
2. **Flexibility:** NoSQL databases are designed to handle unstructured or semi-structured data, which means that they can accommodate dynamic changes to the data model
3. **High availability:** The auto, replication feature in NoSQL databases makes it highly available because in case of any failure data replicates itself to the previous consistent state.
4. **Scalability:** NoSQL databases are highly scalable, which means that they can handle large amounts of data and traffic with ease.
5. **Performance:** NoSQL databases are designed to handle large amounts of data and traffic, which means that they can offer improved performance compared to traditional relational databases.
6. **Cost-effectiveness:** NoSQL databases are often more cost-effective than traditional relational databases, as they are typically less complex and do not require expensive hardware or software.

### Key Highlights on SQL vs NoSQL

| SQL | NoSQL |
| :-------: | :------: |
| RELATIONAL DATABASE MANAGEMENT SYSTEM (RDBMS) | Non-relational or distributed database system. |
| These databases have fixed or static or predefined schema | They have a dynamic schema |
| These databases are not suited for hierarchical data storage. | These databases are best suited for hierarchical data storage. |
| These databases are best suited for complex queries | These databases are not so good for complex queries |
| Vertically Scalable | Horizontally scalable |
| Follows ACID property | Follows CAP(consistency, availability, partition tolerance) |
| Examples: MySQL, PostgreSQL, Oracle, MS-SQL Server, etc | Examples: MongoDB, HBase, Neo4j, Cassandra, etc |

### What is MongoDb?
MongoDB is an **open-source,** **non-relational database management system (DBMS)** that stores and processes data as documents instead of tables and rows. **MongoDB is known for its flexibility and scalability, and is designed to be simple and fast for developers.** 

#### MongoDb Features:
- **Document model:** MongoDB's document model is flexible and JSON-like, allowing for unstructured data storage. 
- **Data storage:** MongoDB stores data in Binary JSON (BSON) format. 
- **Scalability:** MongoDB is a distributed database that's designed for high availability, horizontal scaling, and geographic distribution. 
- **Query API:** MongoDB has a developer-native query API. 
- **Time series data:** MongoDB has features for managing time series data, including native time series collections and parameters for controlling storage. 
- **Integration:** MongoDB can be integrated with other data tools, management systems, and more.

### How to Create Database in MongoDb?
1. **Switch to Database & Create new database:**
Use the ``use`` command followed by the name of your new database. For example, to create a database named myNewDatabase:
```JavaScript
    use myNewDatabase;
```
> Note that if myNewDatabase does not exist, MongoDB will create it for you once you insert data into it.

### How to Insert Database in MongoDb Database?
2. **Insert Data into the Database:**
Create a collection and insert a document to ensure the database is created. For example:
- **Create a Collection :** Collections in MongoDB are created implicitly when you first insert a document into them. However, you can also explicitly create a collection using the db.createCollection() method.
**Example of Implicit Creation:**
```JavaScript
    db.newCollection.insert({ name: "Alice", age: 25 })
```
**Example of Explicit Creation:**
```JavaScript
    db.createCollection("myCollection");
```
- **Show all Collections in Database:** To see the collections in your current database:
```JavaScript
    show collections;
```
- **Drop a collection:**
```JavaScript
    db.myNewCollection.drop()
```
-  **Verify the Database:** To see the list of databases, you can use:
```JavaScript
    show databases;
```
- **Drop a database:**
```JavaScript
    use myNewDatabase
    db.dropDatabase()
```

**Insert Documents:** In MongoDB, the insert() method was used to add documents to a collection it allows us to insert both single and multiple documents at once.  It is now recommended to use more specialized methods like insertOne(), insertMany() and bulkWrite() Add documents to a collection using insertOne or insertMany.

**Example 1: Insert a Document without Specifying an _id Field**
```Javascript
    myDatabase> db.myCollection.insert({Name:"Suraj",marks:95})
    {
        acknowledged: true,
        insertedIds: { '0': ObjectId('66e96d0ce2f06bee81c73bf9') }
    }
```
**Example 2: Insert Multiple Documents** Here, we insert multiple documents in the **collection by passing an array of documents in the insert method.**
```JavaScript
    myDatabase> db.myCollection.insert([{Name:"Krishna"},{Name:"Niraj"},{Name:"Sohan"}])
    {
        acknowledged: true,
        insertedIds: {
             '0': ObjectId('66e96dc4e2f06bee81c73bfa'),
             '1': ObjectId('66e96dc4e2f06bee81c73bfb'),
             '2': ObjectId('66e96dc4e2f06bee81c73bfc')
             }
    }
```
**Example 3: Insert a Document Specifying an _id Field:**
```JavaScript
     myDatabase>db.myCollection.insert({_id:100,Name:"KPBHAI",marks:98})
    { acknowledged: true, insertedIds: { '0': 100 } 
}
```
Output:
```JavaScript
myDatabase> db.myCollection.find().pretty()
[
  {
    _id: ObjectId('66e96b84e2f06bee81c73bf8'),
    roll: 1,
    Name: 'Suraj',
    marks: 95
  },
  {
    _id: ObjectId('66e96d0ce2f06bee81c73bf9'),
    Name: 'Suraj',
    marks: 95
  },
  { _id: ObjectId('66e96dc4e2f06bee81c73bfa'), Name: 'Krishna' },
  { _id: ObjectId('66e96dc4e2f06bee81c73bfb'), Name: 'Niraj' },
  { _id: ObjectId('66e96dc4e2f06bee81c73bfc'), Name: 'Sohan' },
  { _id: 100, Name: 'KPBHAI', marks: 98 }
]
```

### How to update documents in MongoDb?
The MongoDB update() method is a method that is used to update a single document or multiple documents in the collection. When the document is updated the _id field remains unchanged. The db.collection.update() method updates a single document by default.
> Note: In MongoDB, the update() method has been deprecated in favor of using updateOne() or updateMany() depending on your specific use case.

**Example 1: Update a Single Document:**
Write a query to update the marks of a student where rollno 1 in the “myCollection” collection.
```JavaScript
    myDatabase> db.myCollection.updateOne({Name:"Suraj"},{$set:{marks:99}})
    {
       acknowledged: true,
       insertedId: null,
       matchedCount: 1,
       modifiedCount: 1,
       upsertedCount: 0
    }
-------------------------------------------------------------------
    myDatabase> db.myCollection.find().pretty()
         [
           {
             _id: ObjectId('66e96b84e2f06bee81c73bf8'),
             roll: 1,
             Name: 'Suraj',
             marks: 99
           },
           {
             _id: ObjectId('66e96d0ce2f06bee81c73bf9'),
             Name: 'Suraj',
             marks: 95
           },
           { _id: ObjectId('66e96dc4e2f06bee81c73bfa'), Name: 'Krishna' },
           { _id: ObjectId('66e96dc4e2f06bee81c73bfb'), Name: 'Niraj' },
           { _id: ObjectId('66e96dc4e2f06bee81c73bfc'), Name: 'Sohan' },
           { _id: 100, Name: 'KPBHAI', marks: 98 }
        ]
```
