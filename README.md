MongoDB

What is MongoDB?
- Document-oriented NoSQL Database (Non-Relational Database) (Collections are not related to Documents, the way tables and rows are, in case of Relational Databases (MySQL, PostgreSQL)).
- Schema-free.
- Based on Binary JSON --> BSON.
- Organised in Group of Documents --> Collections.
- Auto-Sharding inorder to scale horizontally.
- Uses simple query-language.
- Has rich Document-based queries.
- Open Source.

MongoDb V/s RDBMS
- Collections V/s Tables.
- Document V/s Rows.
- Field V/s Column.
- Collection isn't strict about what goes in it (it's schema less).

Download and Setup MongoDB on MacOS.

Download and Install GUI for MongoDB - Studio3T.

Database --> Collections --> Documents.

CRUD
- use mydb --> creates a new DB called mydb if it doesn't exist initially, else switches to mydb Database if it exists initially.
- db --> tells the name of the database that you are currently using.
- show dbs --> shows the list of all the databases which are present in that particular connection along with their data usage.
- db.dropDatabase() --> drops / deletes the current database.
- db.createCollection("myCollection") --> creates a new collection inside the current database called "myCollection".
- show collections --> shows all the collections list present inside the current database.
- db.myCollection.insert({"name" : "Rahul Swar}) --> inserts {"name" : "Rahul Swar} Document in "myCollection" Collection of the current database if it already exists, else it will create a new collection "myCollection" in the current database and then add the {"name" : "Rahul Swar} Document inside it.

Query Document
- db.students.find() --> gives the dump of the documents present in the "students" collection inside the current using db.
- db.students.find().pretty() --> gives a well organised display of all the documents present in the "students" collection inside the current using db.
- db.students.findOne() --> gives the first document that was inserted inside the "students" collection of the current db.
- db.students.find({"studentNumber" : "2"}) --> query the document(s) inside "students" collection of current db, based on the field and it's corresponding value provided.
- db.students.find({"age" : {$gt : "19"}}) --> query the document(s) inside "students" collection of current db, where "age" field value is greater than "19".
- db.students.find({"age" : {$gte : "19"}}) --> query the document(s) inside "students" collection of current db, where "age" field value is greater than or equal to "19".
- db.students.find({"age" : {$lt : "21"}}) --> query the document(s) inside "students" collection of current db, where "age" field value is lesser than "21".
- db.students.find({"age" : {$lte : "21"}}) --> query the document(s) inside "students" collection of current db, where "age" field value is lesser than or equal to "21".
- db.students.find({"age" : {$ne : "19"}}) --> query the document(s) inside "students" collection of current db, where "age" field value is not equal to "19".

When you do not specify your own "_id" in your documents, MongoDB assigns a unique id of it's own to each document, that maybe used futher for querying the documents.
--> "_id" : ObjectId("642b9ef3fd37db5e8abceaf4")
This is an alphanumeric string of length 24 (by default, but can be cahnged to any length).

AND OR condition


Projections


Indexing


Using Sort , skip , limit functions


Aggregation


