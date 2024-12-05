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

Exporting the Database
I used the mongodump to Export the Database
mongodump is used to export the entire database. Open a new terminal window
