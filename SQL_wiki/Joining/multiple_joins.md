
This is an example of how you can chain joins together (there may be more ways but I need to look this up):

```sql
INNER JOIN chapter 
ON book.isbn = chapter.book_isbn
INNER JOIN page
ON chapter.id = page.chapter_id;
```


Two ways of joining through a separate table known as a junction table:

SELECT book.title AS book_title, author.name AS author_name, book.description AS book_description
FROM book
INNER JOIN books_authors ON book.isbn = books_authors.book_isbn
INNER JOIN author on books_authors.author_email = author.email;

SELECT
  author.name AS author_name,
  author.email AS author_email,
  book.title AS book_title
FROM
  book, author, books_authors
WHERE 
  author.email = books_authors.author_email
AND
  books_authors.book_isbn = book.isbn;

  The idea is that we use this table to do the joins.