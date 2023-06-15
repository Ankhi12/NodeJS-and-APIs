These past few days, i was working on building database models and related HTTP methods based on relevant project ogic. 
While doing so, i have come across some important concepts and wanted to share.

I have used:

a. Backend - Mongodb

b. Driver - Mongoose

# Cursor
I had to understand this term, to understand when to use find() and findOne().

A cursor is like a pointer which points to a specific collection of documents.

When we do find() it return a cursor to the collection of documents. You might ask but how are we getting all the relevant collection's records.
It's because, when we do find() along with returning the cursor it is also iterating the cursor through all the relevant collections of the document.
Think of it like, automating moving pointers through records in a collection.

**Issue faced**

At some point in my project findOne() was working and not find() and vice versa.

findOne() returns null if the condition that we passed doesn't match.


**findOne({id: id}) vs findById(id) vs find({id:id})**

- finOne({id: id}) returns the first occurance of a record when the condition is satisfied. Otherwise finOne() returns null.

- findById(id) - Is used when you surely know the id, and want to check related data under that id. If somehow the id does not exists in the database, it returns null.

- findOneAndUpdate(filter condition) - Once the filter condition is met, that particular record is updated. Returns the found document.

**Note** - For all the above find methos variations we can pass multiple filter options as find({id: id, rollNo: rollNo}), findOne({id: id, rollNo: rollNo}), findOneAndUpdate({id: id, rollNo: rollNo})



...will write more on these concepts this week. Stay tuned!
