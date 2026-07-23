# CREATE TABLE

## Contents
1. [sql syntax](##sql-syntax)
2. [variable types](##variable-types)
3. examples

## SQL syntax
The syntax for this is 
```sql
CREATE TABLE
table_name (
    var_1 vartype,
    var_2 vartype,
    ...
    var_n vartype
);
```


Some key things to remember:
- No comma in last variable type to declare.
- The bracket after declaring table name.
- Can only run this command once else will get an error saying that table already exists.
- semi colon after the closing bracket.

## Variable Types

### Syntax
This table shows examples of how to assign variable types

| Data Type  | Representation | Value | Display |
|------------|---------------|--------|---------|
| integer | whole number | `617` | `617` |
| decimal | floating-point number | `26.17345` | `26.17345` |
| money | fixed floating-point number with 2 decimal places | `6.17` | `$6.17` |
| boolean | logic | `TRUE`, `FALSE` | `t`, `f` |
| char(n) | fixed-length string (removes trailing blanks) | `'123 '` | `'123'` |
| varchar(n) | variable-length string | `'123 '` | `'123 '` |
| text | unlimited-length string | `'123 '` | `'123 '` |
add date and text[] to this table?

Note that it does not matter whether we assign using `integer`, `INTEGER`, or `InTeGeR`.

### Constraints
If we want to assign constraints to our variables (such as being unique or less than a certain number)

Also, if we want to find which constraints have been placed on a table, we can use:
```sql
SELECT constraint_name, table_name, column_name
FROM information_schema.key_column_usage
WHERE table_name = 'book' OR table_name = 'author';
```
This will produce a table like:
constraint_name	table_name	column_name
chapter_pkey	chapter	id


hello