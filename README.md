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

MongoDB Commands
- use mydb --> creates a new DB called mydb if it doesn't exist initially, else switches to mydb Database if it exists initially.
- db --> tells the name of the database that you are currently using.
- show dbs --> shows the list of all the databases which are present in that particular connection along with their data usage.
- db.dropDatabase() --> drops / deletes the current database.
- db.createCollection("myCollection") --> creates a new collection inside the current database called "myCollection".
- show collections --> shows all the collections list present inside the current database.
- db.myCollection.insert({"name" : "Rahul Swar}) --> inserts {"name" : "Rahul Swar} Document in "myCollection" Collection of the current database if it already exists, else it will create a new collection "myCollection" in the current database and then add the {"name" : "Rahul Swar} Document inside it.

CRUD


QueryDocument


AND OR condition


Projections


Indexing


Using Sort , skip , limit functions


Aggregation


