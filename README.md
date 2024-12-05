# MongoDB-CRUD-Operations-and-Practice-Set

Open the terminal (Command Prompt or PowerShell).

Start MongoDB
If you have MongoDB installed locally, run:
mongosh

Create the Database
After entering the MongoDB shell, run the following command to create and switch to the LibraryDB database:
use LibraryDB

Create and Insert Data
// Insert Books using the insertMany because you are inserting a list of Books.
db.Books.insertMany([])

// Insert Authors using:
db.Authors.insertMany([
])

// Insert Patrons using
db.Patrons.insertMany([
])

Used CRUD Operations
I used db.Books.find();
to find all the books I have added

To Find a book by its title I used 
db.Books.find({ title: "Book title" });

To query all books by a specific author using author_id
db.Books.find({ author_id: 1 });

To show the List of all books that are currently available:
db.Books.find({ available: true });

UPDATE Operations
Update a book’s availability status when borrowed:
I used
db.Books.updateOne({ title: "book title" }, { $set: { available: false } });

Add a new genre to an existing book:
db.Books.updateOne({ title: "book title" }, { $set: { genre: "genre of the book" } });

Record a borrowed book for a specific patron:
db.Patrons.updateOne({ name: "Author" }, { $addToSet: { borrowed_books: "book title" } });

DELETE Operations
Remove a book from the collection by its title:
db.Books.deleteOne({ title: "Pride and Prejudice" });

Delete an author from the Authors collection:
db.Authors.deleteOne({ _id: 3 });

Advanced Queries
Find all books published after a certain year:
db.Books.find({ published_year: { $gt: year } });

Retrieve all authors with a specific nationality:
db.Authors.find({ nationality: "nationality" });

I used $regex to find authors whose names contain a specific keyword:
db.Authors.find({ name: { $regex: "Jane", $options: "i" } });

Increment a published year for a specific book:
db.Books.updateOne({ title: "book title" }, { $inc: { published_year: 1 } });

I Set all books as available using $set:
db.Books.updateMany({}, { $set: { available: true } });

I Combine operators like $and and $gt to query books that meet multiple conditions:
db.Books.find({ $and: [{ published_year: { $gt: 1900 } }, { available: true }] });

Exporting the Database
I used the mongodump utility to export the LibraryDB database.

Steps:
Open a new terminal window.
Run the following command:
mongodump --db=LibraryDB --out=./backup

A backup folder containing the database dump will be created.

Verification Questions
What does $and do in a query?
$and allows you to combine multiple conditions in a query. Each condition must be true for a document to be included in the results.

How does $addToSet differ from $set?
$set updates a field with a specific value, while $addToSet adds a value to an array field only if it does not already exist.

Why is $regex useful for filtering text data?
$regex enables advanced pattern matching, making it possible to search for text that meets specific criteria, such as partial matches or case-insensitive queries.