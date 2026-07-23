# Keys

## Types of Keys
Primary, Foreign, composite

### Primary Key
This ensures that the value in this column is always unique and never `NULL`. 
```sql
CREATE TABLE munros (
    id integer PRIMARY KEY,
    name char(30),
    ...
);
```
If we have many columns that together make up a private key then we can assign a group to become a COMPOSITE KEY by using `PRIMARY KEY (COL1,COL2,...)` in the final line.

To query a table on which values have been assigned a key see the constraints section of [[create_table]]

It is possible to assign multiple columns as the primary key by not assigning a primary key when defining the data type in the `CREATE TABLE` stage, but instead at the end of the statement doing `PRIMARY KEY (col1, col2)`

## Foreign key

When we have a situation where one table is related to another table in a 
database
Preview: Docs Loading link description
, we may want to bind those tables back together in a query. For example, let’s say we have a person table and an email table. If we want a list of names and associated emails, we would need to join these tables together.

To maintain data integrity and ensure that we can join tables together correctly, we can use another type of key called a foreign key. A foreign key is a key that references a column in another table.

Where do we place this foreign key? Should it be in the person table or email table? To answer this question, we need to figure out how person is related to email. Does creating a person record require that an email record exists as well? This is not usually the case. A person can have no email address or one or more email addresses. So when creating a record in the person table, we don’t insist that this person should have a record in the email table as well.

Does creating an email record require that a valid person record exists? This is usually the case, since we shouldn’t create an email address for a non-existent person. Hence, we should place the foreign key in the email table to ensure that a valid record in the person table must pre-exist before adding a record in the email table.

In the illustration below, the foreign key is person_id in the email table.

CREATE TABLE chapter (
  id integer PRIMARY KEY,
  book_isbn varchar(50) REFERENCES book(isbn),
  number integer,
  title varchar(50),
  content varchar(1024)
);

A primary key implies uniqueness

Query Results
constraint_name	table_name	column_name
chapter_pkey	chapter	id
chapter_book_isbn_fkey	chapter	book_isbn

Using foreign keys and private keys  to do a query instead of a join:
```sql
SELECT book.title, book.price, book_details.language, book_details.rating
FROM book, book_details
WHERE book.isbn = book_details.book_isbn;
```
equivalent would be 
```sql
SELECT book.title, book.price, book_details.language, book_details.rating
FROM book
JOIN book_details
ON book.isbn = book_details.book_isbn;
```
s

### One to One
For a one to one join, use UNIQUE after REFERENCES.

### One to Many 


### Many to Many
Here the idea is if we have a many to many relationship, ie the 

YOu can end up with this after querying the key type (we have a joint private key and both those things are foreign keys in other tables).
constraint_name	table_name	column_name
books_authors_pkey	books_authors	book_isbn
books_authors_pkey	books_authors	author_email
books_authors_book_isbn_fkey	books_authors	book_isbn
books_authors_author_email_fkey	books_authors	author_email