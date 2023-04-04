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
- db.students.find() --> gives the dump of the documents present in the "students" collection inside the current using db.
- db.students.find().pretty() --> gives a well organised display of all the documents present in the "students" collection inside the current using db.
- db.students.update({"_id" : ObjectId("642b9ef3fd37db5e8abceaf4")},{$set : {"lastName" : "test"}}) --> updates the document with "_id" specified.
- db.students.update({"age" : "22"},{$set : {"firstName" : "test"}}) --> this just updates the first document that it finds with the given condition, i.e., "age" = "22", and not all the documents with "age" = "22".
- db.students.update({"age" : "22"},{$set : {"firstName" : "test"}},{multi : true}) --> updates all the documents that it finds with the given condition, i.e., "age" = "22".
- db.students.save({"_id" : ObjectId("642b9ef3fd37db5e8abceaf4"),"studentNumber" : "1","firstName" : "Rahul","lastName" : "Swar","age" : "22"}) --> searches for the doc, if it already exists with the mentioned "_id", if it is already present, then it modifies / updates it with the mentioned fields, else creates a new document with this "_id".
- db.students.remove() --> removes / deletes all the documents in the "students" collection of the current db.
- db.student.remove({"_id" : ObjectId("642b9ef3fd37db5e8abceaf4")}) --> removes / deletes documnet with "_id" same as the one mentioned inside the remove function.
- db.student.remove({"age" : "22"}) --> removes / deletes all the documents with "age" = "22".
- db.student.remove({"age" : "22"}, 1) --> removes / deletes a single document, which it finds first with matching condition.

Query Document
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
- db.students.find({"firstName" : "Rahul", "age" : "22"}) --> querying using AND operation
- db.students.find({$and : [{"firstName" : "Rahul"}, {"age" : "22"}]}) --> alternative for querying using AND operation
- db.students.find({$or : [{"firstName" : "Rahul"}, {"age" : "22"}]}) --> querying using OR operation
- db.students.find({"lastName" : "Swar", $or : [{"age" : "22"}, {"age" : "25"}]}) --> querying using combination and AND as well as OR operations.

Projections
- Projections means selecting / querying only the necessary data, rather than selecting / querying whole of the data of the document.
- db.COLLECTIN_NAME.find({}, {KEY : 1})  --> KEY here is the field or property of the document, 1 means that it's set to true, that means we want to see this key results, 0 means it's set to false, which means we don't want to see this key results.
- db.students.find({},{"firstName" : 1}) --> displays the "firstName" fields of all the documents present in the "students" collection of the "school" db. (also "_id" field is visible, as it comes by default).
- db.students.find({},{"firstName" : 1, "_id" : 0}) --> displays only the "firstName" fields of all the documents and not the "_id" field, present in the "students" collection of the "school" db.

Using Sort , skip , limit functions
- limit - db.students.find({}, {"firstName" : 1, "age" : 1, "_id" : 0}).limit(4) --> limit is used to fetch only a precise number of outputs n. (in this case n = 4).
- skip - db.students.find({}, {"firstName" : 1, "age" : 1, "_id" : 0}).skip(2) --> skip is used to skip the first n results obtained and output the results obtained after the skipped documents. (in this case n = 2).
- db.students.find({}, {"firstName" : 1, "age" : 1, "_id" : 0}).skip(2).limit(4) --> skips the first two, and then limits the number of outputs to 4 out of te remaining.
- sort - db.students.find({}, {"firstName" : 1, "age" : 1, "_id" : 0}).sort({"firstName" : 1}) --> sorts the outputs in ascending order of their firstNames. (here "firstName" field is used to sort, 1 means ascending order, -1 means descending order) (since "firstName" is a string, hence it will follow lexicographic order).

Indexing
- Indexes are special data structures, that store a small portion of data, set in the easy to pass way. 
- Indexes are supposed to make efficient resolution of queries.
- Without indexes, it is very inefficient to query a document out of millions of documents in a database or a collection of the database.
- db.posts.ensureIndex({"student_id" : 1}) --> does the indexing of all the documents in the "posts" collection of "temp" db, which speeds up the query time.
- Important condition for indexing : All indexes of all the documents must be unique.
- db.posts.dropIndex({"student_id" : 1}) --> removes / drops the indexing of all the documents in the "posts" collection of "temp" db.

Aggregation
- Aggregation operation groups values from various documents together and can perform various operations on the grouped data and returns a single result after the operation.
- db.students.aggregate([{$group : {_id : "$gender", MyResult : {$sum : 1}}}]) --> aggregation to get count of number of "Male" and "Female" documents based on "gender" field inside "students" collection of "school" database.
- db.students.aggregate([{$group : {_id : "$gender", MaxAge : {$max : "$age"}}}]) --> aggregation to get maximum age of "Male" and "Female" documents based on "gender" field inside "students" collection of "school" database.
- db.students.aggregate([{$group : {_id : "$gender", MinAge : {$min : "$age"}}}]) --> aggregation to get minimum age of "Male" and "Female" documents based on "gender" field inside "students" collection of "school" database.

MongoDB BackUp and Restore
