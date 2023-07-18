# SQL / Database Bootcamp: MySQL + SQLite

# Structure

0. SQLite commands
1. Creating databases and tables
2. Inserting data
3. CRUD Commands
4. String functions
5. Refining Selections
6. Aggregate functions
7. Data Tyes
8. Logical operators
9. One To Many relationships
10. Many To Many relationshps
11. Instagram database clone
12. Working with lots of data
13. Node and Web Apps + SQL

# INtroduction

#### DB & DBMS

- A database is a collection of data, e.g. phonebook, ledger
- We need a reliable program / code that's part of the database that provides reliable methods of manipulating, adding, and retreiving data from the DB.
- This program is a Database Management System (DBMS) such as MySQL, SQLite, PostgresSQL, OracleDB. THese inlcude the database and the DBMS
- THe DBMS provides an interface btn the actual database our program
- So A database / DBMS is a structured set of computerised data with an accessible interface.

#### SQL

- it is the language we use to talk to our databases. We do things like Find data, conditionally retrieve data, sort data, delete data

- Relational DBMS like mysql, sqlite, postgres,oracle, etc use SQL, and when we use any of these we use SQL.

- These RDBMS have slight differences in the implementation of udeas and syntax. Thy all should follow the SQL standard
- Therefore learning SQL makes it easy to move from one DBMS to another.

- Th RDBMS are not identical. THere are different factors like Size, Speed, Security, User permissions, embedded or hosted

- To use any of the RDBMS visit their website, download and install it, following the particular instructions.

# MySQL

- It is a hosted DBMS that is very secure and scalable.
- You need to download it from the official page, and install it to your machine.
- YOu go through a series of configuration step: where

  - You set up a password for the root user,
  - You can create different accounts/instances with different passwords and purposes like root, admin, user, manager, etc i.e people who have low level access to the DB
  - You choose whether you hhave installed on a development computer or server computer

- The MySQL server program shhould be running.
- You can connect to the server via the MySQL shell CMD prog or via the MySQL workbench GUI application
- If the server stopped running, due to server restart or long time without running th server, follow these innstructions

> Open RUN by pressing Windows+R
> Type `services.msc` & press Enter
> Select the MySQL service and select restart button
> Follow same procedure to stop, start or restart the server

- or: To start and to stop the server, run the cmd commnads

> `C:\> "C:\Program Files\MySQL\MySQL Server 8.0\bin\mysqld"` > ` C:\> "C:\Program Files\MySQL\MySQL Server 8.0\bin\mysqladmin" -u root shutdown`

- For other Operating sytems (macOS, Linux), befriend google.

- For every comand you type into the command line postpend a ";"

- To run the CMD program

> `C:\> cd "C:\Program Files\MySQL\MySQL Server 8.0\bin\` > `C:\> mysql`

- Connecting to an instance

  > `C:\> mysql -u root -p`
  > Enter password and viola

- In the MySQL shell

  > `mysql-js >` > `mysql-js > \sql` > `mysql-sql > \connect username@servername (root@localhost)`
  > Enter password

- Connect to remote server
  > `myql -u USERNAME -pPASSWORD -h HOSTNAME -P PORTNUMBER DATABASE;` > `myql -u root -phrn12345 -h 127.0.0.1 -P 3306 testdb;`

> Head over to `cloud9.com` or search `cloud9`, it could help to host your sql database, and you can work with it

# Simple SQLite commands

- The best source of information about sqlite = `www.tutorialspoint.com/sqlite/`
- Enclosed in question marks are not part of the syntax but some points to note.

> sqlite is an embedded databes, meaning your have access to the `.db` or `.sqlite` file that you can include in your directory.
> To connect to this db, you have to install the sqlite command line program, which we can use to manipulate the databases
> The program executes sql commands, in addition
> The program has some unique commands that will be identified whenever i find them..

```sql
.help # For instructions

# 1. Backup database/DB (default = "main") to FILE
.backup ?DB? ?FILE?

#2. Stop after hitting an error. Default = OFF
.bail ON | OFF

#3. List names of dbs
.databases

#4. Dump the database in an sql text format. if TABLE is specified, only dumps tables matching LIKE pattern TABLE. You can perform a restoration
.dump
.dump ?TABLE?
$ sqlite3 testdb.db < testdb.sql

#5. Turn command echo ON or OFF
.echo on | OFF

#6. Turn output mode suitable for EXPLAIN on or off. With no args, it turns explain on
.explain ON | OFF

#7. Turn display of headers on or off
.header(s) ON | OFF

#8. Import data from FILE into TABLE
.import ?FILE? ?TABLE?

#9. Show names of all indices. if TABLE specified, only show indices for the tables matching LIKE pattern TABLE
.indices ?TABLE?

#10. Load an extension library
.load FILE ?ENTRY?

#11. Turn logging on or off
.log ON | OFF

#12. set output mode
.mode csv #comma separted values
.mode column #left aligned column
.mode html #HTML <table> code
.mode insert #sql insert statements for TABLE
.mode line #one value per line
.mode list #values delimitd by `.seperator` string
.mode tabs #tab-separated values
.mode tcl #TCL list elements

#13. Print STRING instead of null value
.nullvalue STRING

#14. Send output to FILENAME
.output FILENAME

#15. Send output to screen
.output stdout

#16. print literal string
.print STRING...

#17. Replace standard prompts
.prompt MAIN CONTINUE

#18. Exit SQLite prompt
.quit

#19. Execute SQL in FILENAME
.read FILENAME

#20. Show the create statements. if TABLE specifed, only show tables matching LIKE pattern
.schema
.schema ?TABLE?

#21. hangeseperator useed by the output mode and `.import`
.seperator STRING

#22. SHow current values for various settings
.show

#23. Turn stats on or off
.stats ON | OFF

#24. List names of tables matching LIKE pattern
.tables ?PATTERN?

#25. Try opening locked tables for MS milliseconds
.timeout MS

#26. Set column widths for "column" mode
.width NUM NUM NUM ...

#27. Turn CPU timer measurement on o off
.timer ON | OFF

```

# 1. Creating Databases and tables

- A database is a computer on a network where many databases are stored. Eg. An instance of MYSQL can have several databases...The instance requires a password to access
- List the current databases

```sql
show databases;

# sqlite3
.databases

```

- Creating a database

```sql
CREATE DATABASE <name>;

create database my_app;
create database myApp;

# sqlite3
sqlite3 database_name.db
sqlite3 database_name.sqlite
```

- Deleting a db

```sql
drop database OWNDBNAME;

# do not mess with preexisting/default databases
```

- Using databases: Tell mysql which database you want to be woking with. Switchng btn dfft dbs on the server

```sql
USE databasename;

# Tell the currently used db
SELECT database();
```

## Tables

- The heart of databases. Databases are a collection of related tables
- Tables hold the data
- _Columns_: refer to headers
- _Rows_ are the actual data in the data

- _Data types_
- THere are many MySQL data types
- _Numeric types_: INT, SMALLINT, TINYINT, MEDIUMINT, BIGINT, DECIMAL, NUMERIC, FLOAT, DOUBLE, BT

- _String types_: CHAR, VARCHAR, BINARY, VARBINARY, BLOB, TINYBLOP, MEDIUMBLOB, LONGBLOB, TEXT, TINYTEXT, MEDIUMTEXT, LONGTEXT, ENUM

- _Date types_: DATE, DATETIME, TIMESTAMP, TIME, YEAR

- You don't even have to know all of these. Initially we'll use INT for numercs and VARCHAR for text and strings

- INT = a whole number, no decimals, max value of 4294967295
- VARCHAR = a variable-length string, btn 1 to 255 characters. `varchar(15)` - max value is 15
- Each column should have a defined datatype

#### CReating tables

- Put the columns into parantheses, in colomnaname-datatype pairs separted by commas

```sql
CREATE TABLE tablename (
    column_name datatype,
    column_name datatype,
    column_name datatype
);

# e.g.
CREATE TABLE cats (
    name VARCHAR(100),
    age INT
)

# PLuralize table names
```

- To see the tables

```sql
show tables;

.tables #sqlite

# show tables cols
SHOW COUMNS FROM table_name; #either

DESC table_name; #or
```

- Deleting tables

```sql
DROP TABLE tablename;
```

# Inserting data into tables

```sql
# order matters
INSERT INTO tablename(COL1, COL2, COL3) VALUES('Val1', VAL2, VAL3);

# View everythin gin the tabl
SELECT * FROM tablname;

# Inserting multiple rows/values
INSERT INTO tablename(name, age)
    VALUES ('charli', 10),
           ('orange', 3),
           ('Panut', 2);
```

> SQL warnings
> Most warnings occur silently, and you need to look out for them
>
> ```sql
> SHOW WARNINGS;
> ```

- THere are extra columns when we use `DESC tablename`, Null, Key, Default, Extra. These show some settings applied to the table
- NULL and NOTNULL
- NULL = the valu is not known. Used as default when a value is not specified when inserting.
- If is a permitted value

```sql
INSERT INTO tablename() values ();

# Will insert NULL every where
```

- How do we prevent this?
- Specify NOT NULL whne creating the table

```sql
CREATE TABLE(
    name VARCHAR(100) NOT NULL,
    age INT NOT NULL
);

# If data is not provided, mysql looks for default values.
# If no default, the default values are set to 0 for INT & "" for VARCHAR
```

- Setting default values

```sql
CREATE TABLE tablename
(
    name VARCHAR(100) NOT NULL DEFAULT 'Unnamed',
    age DEFAULT 99
);
```

- The `Key` column: Uniquely identify identical fields
- A primary key is a unique identifier. We can assign any column to primary key, and all values must be unque.

```sql
# Setting primary key and auto increment
CREATE TABLE tablename(cat_id INT NOT NULL AUTO_INCREMENT,
    ,name VARCHAR(30)
    ,PRIMARY KEY (cat_id)
);

# or
CREATE TABLE tablename(cat_id INT NOT NULL AUTO_INCREMENT PRIMARY KEY,
    ,name VARCHAR(30)
);

```

- Features like auto_increment are added to the Extra fields.

# CRUD commands

- CReate, Read, Update, Delete commands
- They are the fundamental parts of a DBMS
- We have looked at inserting and selecting

1. READ

- The command we use is `SELECT`
- ` SELECT * FROM cats;`
- To specify the only crtain columns: We use the `SELECT` expression.

```sql
# Select one column
SELECT colname FROM tablename;

# select two or more fields - outputs specifed order
SELECT col1, col2 FROM tablename;
SELECT age, breed, name FROM cats;
SELECT name, cat_id FROM cats;


```

- The `WHERE` cluase
- Retreive specfic data
- We use WHERE all the time, when reading, updating, and deleting

```sql
SELECT * FROM cats WHERE colname=operand; # operators work: <, <=, >=, =,!=
SELECT * FROM cats WHERE age=4;
SELECT name, age FROM cats WHERE cat_id>=5;

```

- ALIASES
- We can specify how the data is displayed to me
- Doesn't change actual data but simply name the output column headers, doesn't change table.

```sql
# output cat_id as just 'id'
SELECT cat_id AS id, name FROM cats;
SELECT cat_id AS id, name AS 'Kitties' FROM cats;
```

2. UPDATE

```sql
UPDATE cats SET breed='Shorthair' WHERE breed='Tabby';
# SET = the list of chnages to make
# Where = specfy which fields
```

> A good rule of thumb
> Try SELECTing before you UPDATE, to make sure you are targeting the right thing.

3. DELETE

- Delete things from the table
- Similar to select statement

```sql
# first SELECT
SELECT * FROM cats WHERE name='Egg';

# if you're sure, you can delete
DELETE FROM cats WHERE name='Egg';
```

> Important
> When creating table, make sure not to use possibly reserved words (internally used by sql) like size

# String functions

1. Running sql files, instead of passing ommands into the command line.

- Makes it easier to review and correct mistakes,
- We can store seed files fo longer times.

```sql
# Make usre you're in the correct directory and have opened the correct db
source filename.sql

# For this tp worl, make sure, you run the mysql command where the file is located, or ina dir where to provde a relative path
$ cd into/the/folder
$ mysql -u root -p1234
mysql$ use dbname
mysql source sourcefile.sql #viola
```

> Note
> The sqlite version of table creation is
>
> ```sql
> book_id INTEGER NOT NULL PRIMARY KEY AUTOINCREMENT
> # while mysql is
> book_id INT NOT NULL PRIMARY KEY AUTO_INCREMENT
>
> ```

> You should avoid using the autoincrement constraint in sqlite as it is cpu instensive. Sqlite automatically adds a `rowid` field

2. ### The string functions

- There are several string functions, if you searh in the documentation. So if you need to do somethiing new, search for it.
- String functions are those use to wok with string data

  1. CONCAT

  - Combine two strings into one.

  ```sql
    CONCAT(x, y,z)
    CONCAT(column, anotherColumn)

    #It simply concatenates them. To add a seperator
    CONCAT(author_fname, " ", author_lname)

    # Usage: we use it with SELECT
    SELECT CONCAT('Hello', '...', 'World') #-> Hello...World

    SELECT CONCAT(author_fname, ' ', author_lname) FROM books;
    SELECT CONCAT(author_fname, ' ', author_lname) AS fullname, title FROM books;

  ```

- CONCAT_WS: concat with seperator
- When we are concatenating multiple strings, with the same seperator

```sql
SELECT CONCAT_WS(' - ', author_fname, author_lname) FROM books;
```

2.  SUBSTRING

- Output a part of the string
- SUBSTR works the same and works fine.

```sql
 SELECT SUBSTRING('Hello World', 1, 4) #-> Hell
 SELECT SUBSTRING('Hello World', 3) #-> llo World
 SELECT SUBSTRING('Hello World', -3) #-> rld
```

> Important
> Indices in MySQL are 1-based(start from 1) not zero unlike many programming languags

- We can use different string functions together

```sql
 SELECT CONCAT(
   SUBSTRING(title, 1, 10), '...'
   ) AS 'short title' FROM books;
```

3. REPLACE: used to replace parts of a str with a new str

- replace is case insensitiv

```sql
SELECT REPLACE('Hello World', 'Hell', '@#%') # replace all occurances of 'Hell' with @#%

SELECT REPLACE(title, ' ', ' and ') FROM books;

# replacing multiple
SELECT REPLACE(title, 'e', '3', 'A', '4', 'l', 'I') FROM books;

# Combined with it self and anotehr fn - Hiren made this up
SELECT
  CONCAT
  (REPLACE
  (REPLACE
  (REPLACE(title, 'e', '3'), 'A', '4'), 'l', 'I'), ' - by -',
  CONCAT(author_fname, ' ', author_lname)
  )
 FROM books;


```

4. REVERSE

- reverse the selected string

```sql
SELECT REVERSE(author_fname) FROM books;
```

5. CHAR_LENGTH

- returns the number of xters in a string

```sql
SELECT CHAR_LENGTH('Hell') #-> 3
```

6. Change a string case with UPPER() and LOWER()

- Used like other string functions

```sql
SELECT UPPER(title) FROM books;
SELECT LOWER(author_fname) FROM books;
```

# Refining our selections

- Sorting, Ordering, Limiting, Searches

1. DISTINCT

- Only return the unique values in a selection
- Comes immediately after SELECT

```sql
SELECT DISTINCT author_lname FROM books;
```

2. ORDER BY

- Allows us to sort our results
- Works with strings and numbers

```sql
# Order by last name in ascending order
# - It i ascending by defualt
SELECT author_lname FROM books ORDER BY author_lname;

# - Use descending order, postpend `DESC`
SELECT author_lnam FROM books ORDEr BY author_lname DESC
```

- Using a number to refer to one of the selected fields

```sql
# 2 refers to author_fname
SELECT author_lname, author_fname, title FROM books ORDER BY 2 DESC;
```

- We can order by mulptiple fields, after we sort by first sort, we sort by the second sort, if there is an conflict

```sql
# firstorder by last name, then order by 1st name
# I.e. if there r many authors that have the same lname, we then sort by the fname
SELECT author_lname, author_fname, title FROM books ORDER BY 1, 2 DESC;

```

3. LIMIT

- Specify a number for how many result we want to select
- Eg. retrieve top ten recent books
- We sort by the publish time and we limit to 10. So it is not useful to do it on ts own.

```sql
# We often use it wth ORDER BY
SELECT title, released_year FROM books ORDER BY released_year DESC LIMIT 5;

# Selecting a range, a starting point to end point. The rows start on zero(1st row is 0). We use this feature in server side pagination
SELECT title, released_year FROM books ORDER BY 2 DESC LIMIT 0, 15;
SELECT title, released_year FROM books ORDER BY 2 DESC LIMIT 10, 15;

# select from a start point to the end - use a ggantc number
SELECT * FROM books LIMIT 10, 1234567892345678

```

4. Data search using LIKE

- WHERE is used in simple cases
- LIKE allows us to more sophisticated searches

```sql
# Any thing followed by 'da' and anything afterwards i.e contains 'da'
SELECT * FROM books WHERE author_fname LIKE '%da%';

```

- THe wild cards exp

- Percent
  'da' = exactly 'da'
  '%da%' = contains 'da'
  'da%' = starts with 'da'
  '%da' = ends with 'da'

- Underscore: designates any characters
- `'____'` matches exactly four characters

- The percents are `wild cards`
- Matching patterns like '(234) 3456-3456', we use something like `(___) ____-____`
- If the pattern uses an % or \_ sign, you have to escape these characters with a backslash, i.e.

```sql
WHERE title LIKE '%\% \_%'
```

- LIKE also match regular expressions.

- The similar functions `REGEXP` and `RLIKE` work similar to `LIKE` but they match a regular exp provided
- To search for multiple strings

```sql
WHERE title LIKE '%a%e%i%o%u%' # search for values that contain atleast all vowel letters
```

```sql
SELECT * FROM books ORDER BY pages DESC LIMIT 1;
```

# Aggregate functions

- Grouping multiple rows and do calculaton so that group. E.g. Finding the monthly profit, which ig user is an influencer, which hashtag generates the most attraction, which product generate the most attraction.
- These allow us to perform analysis on the data.
- They work on aggregated data

1. COUNT

- Counts anything. How many books are in our database?

```sql
# Count every row in the table
SELECT COUNT(*) FROM books;

# How many authors, count only authors
SELECT COUNT(author_lname) FROM books;

# How mnay distinct authors, only unque authors
SELECT COUNT(DISTINCT author_fname) FROM books;
```

- How many unique authors, based on both 1st and last names

```sql
SELECT COUNT(DISTINCT author_fname, author_lname) FROM books;
```

- How many titles contain 'the'

```sql
SELECT COUNT(*) FROM books WHERE title LIKE '%the%'
```

2. GROUP BY

- Summerizes / aggregates identical data into single rows
- e.g. group the movies in the db by genre and tell the number in each genre

```sql
# Group the books of the same author, prnts only one book but internally creates grouped rows
SELECT title, author_lnam FROM books GROUP BY author_lname; # won't print out results

# then count them
SELECT author_lname, COUNT(*) FROM books GROUP BY author_lname;
```

> With COUNT, the GROUP BY function prints the selected column with aggregated data that is then countd by count
> COUNT adds an extra column to indicate the numbers
> For GROUP BY to output reasonable data, you have to include a column of COUNT

- more examples

```sql
# Count releases per year.
SELECT released_year, COUNT(author_fname) FROM books group by released_year;
```

3. MIN / MAX

- Alllow us identify smallest and largest values in gh table.
- Can be used alone and/or GROUP BY

```sql
# earliest book release
SELECT Min(relaesed_year) FROM books;

# longest book
SELECT Max(pages) FROM books;
```

- What if i want to know the title of the longest book or other info of the returned the Min/Max

```sql
# This returns in correct data
SELECT Max(pages), title FROM books;
```

- One potential solution: SUBQUERIES

```sql
# Do a query in another query
SELECT * FROM books WHERE pages=(SELECT Max(pages) FROM books);

# 2nd Solution: Better soln
SELECT * FROM books ORDER BY pages ASC LIMIT 1;
```

- Using MIN/MAX with GROUP BY
- Eg. Find the year in whch each author published their first book

```sql
SELECT author_fname, author_lname, Min(released_year) FROM books GROUP BY author_lname, author_fname;

# Find the longst page count for each author
SELECT author_fname, author_lname, Max(pages) FROM books GROUP BY author_lname, author_fname;
```

4. SUM

- Sum all things in the database. Eg. The total of values in a column

```sql
SELECT Sum(pages) FROM books;
```

- In conjuction with GROUP BY

- eg. Sum all the pages each author has written

```sql
SELECT author_fname, author_lname, Sum(pages) AS 'Total Pages' FROM books GROUP BY author_lname;
```

> Important some times, you need to include the columns that you grouping by in the SELECTion. For Mysql `[sql_mode=only_full_group_by] `, there is a wierd error. Eg.
> `SELECT author_fname, author_lname, Sum(pages) AS 'Total Pages' FROM books GROUP BY author_lname;` may generate an error;
>
> ```console
> Expression #1 of SELECT list is not in GROUP BY clause and contains nonaggregated column 'bookstore.books.author_fname' which is not functionally dependent on columns in GROUP BY clause; this is incompatible with sql_mode=only_full_group_by mysql> SELECT author_fname, author_lname, Sum(pages) AS 'Total Pages' FROM books GROUP BY author_lname, >author_fname;
>
> ```

> We should the selectd columns into the GROUP BY clause:
> `SELECT author_fname, author_lname, Sum(pages) AS 'Total Pages' FROM books GROUP BY author_lname, author_fname;` works fine

5. AVG

- GEt an average of things/values in the table

```sql
SELECT AVG(released_year) FROM books;
```

- With group by:

```sql
# Avg stock qqty for books released in the same year
SELECT AVG(stock_quantity) FROM books GROUP BY released_year;
```

6. The secton challenges, **i passed all of them**

```sql
# Print the no of books in the db
SELECT COUNT(*) FROM books;

# Print how many books were released each year
SELECT released_year, COUNT(*) FROM books GROUP BY released_year;

# Print total no of books in stock
SELECT Sum(stock_quantity) FROM books;

# Find the average year of release for each author
 SELECT author_fname, author_lname, Avg(released_year) FROM books GROUP BY author_fname, author_lname;

# Find the full name of the author who wrote the longest book
 SELECT CONCAT(author_fname, ' ', author_lname) AS 'full name' FROM books ORDER BY pages DESC LIMIT 1

# Print a table of avergae pages and number of books per year, sort the years from earliest
SELECT released_year, COUNT(*) AS '#books', AVG(pages) FROM books GROUP BY released_year ORDER BY released_year ASC;
```

# Data Types

- How we store text, numeric, dates & time,

1. VARCHAR & CHAR

- There are both for text, but the dffc is that CHAR has a fixed length.
- CHAR is faster for fixed length text like State abbreviations, yes/no flags, sex
- Otherwise use VARCHAR

2. NUMERIC data types

- **INT** for whole numbers where decimals don't matter
- **DECIMAL** for floating point numbers. It take is two arguments: `DECIMAL(13, 2)`. First arg = maximum numbr of digits in the whole number. Second arg = the maximum number of deciimal places
- **FLOAT** & _DOUBLE_, work similar to DECIMAL. The differences are internal to sql, in the way data is stored in memory, how binary works.
- Floats and doubles are approximate, while Decimals are exact
- Floats and doubles use less space to store data at the expense of slight inaccuracies, whil decimals use more space.
- THerefore, for high precision data like currencies & forex, use decmals
- For low precision, e.g jsut some quantitative values and for space preservaton.
- For FLOATs, precsion issues come after approx. 7 digits
- For DOUBLEs, precision issues come after 15 digits

3. Dates and Times

- **DATE**: stores dates without times, formart = 'YYYY-MM-DD'
- **TIME**: STores time but no date, format = 'HH:MM:SS'
- **DATETIME**: values with a DAte and Time, format = 'YYYY-MM-DD HH:MM:SS'

4. CURDATE(), CURTIME(), NOW()

- Theyy give us the current Date, current Time and Current DateTime respectively.

5. Formatting Dates

- There's a massive amount of datetime functions in the documents. The more important ones are ons that extract a pece of info from the datatime
- DAY(), DAYNAME(), DAYOFWEEK(), DAYOFYEAR(), MONTH(), MONTHNAME(), HOUR(), MINUTE()
- These methods work on datetimes, some work specifically on Date and Time

```sql
SELECT name, DAYNAME(dob) FROM people;
```

- DATE_FORMAT()
  > There are shortcuts to reference the data from the dates and times, called **specifiers**, that can be used by the DATE_FORMAT () function. Visit the documentation for these, they are pretty straightforward

```sql
SELECT DATE_FORMAT('2009-10-03 22:23:00', '%W %M %Y');
SELECT DATE_FORMAT('2009-10-03 22:23:00', '%H:%i:%s');

'%m/%d%/%Y'
```

6. DATE maths

- How do we do calculations on dates
- There are many functions in the docs.
- DATEDIFF(expr1, expr2): returns the number of days btn the provided dates

```sql
SELECT DATEDIFF(NOW(), birthdate) FROM people;

# add
DATE_ADD(date, INTERVAL exprunit)
SELECT DATE_ADD('2009-10-03 22:23:00', INTERVAL 2 DAY); # SECOND | QUARTER | MONTH

# subtract
DATE_SUB(date, INTERVAL expreunit)
```

- Instaed of using these date add and sub functions, we can use the plus and minus operators

```sql
SELECT birthdate - INTERVAL 5 MONTH FROM people
```

7. TIMESTAMPS

- Keep track of data entry time. Take up a tny space. Can be automatically flled in.

```sql
CREATE TABLE comments (
  content VARCHAR(100),
  created_at TIMESTAMP DEFAULT NOW()
);
```

- Another usage

```sql
CREATE TABLE comments (
  content VARCHAR(100),
  changed_at TIMESTAMP DEFAULT NOW() ON UPDATE CURRENT_TIMESTAMP
);
```

# Logical operators

- Allow us to add logic into our sql queries
- Eg. select all books not published in 2017, select items in stock with a price < 20$, select red and and blue cars

1. Not Equal (!=)

```sql
SELECT title FROM books WHERE released_year != 2017
```

2. NOT LIKE

- Opposite of LIKE

```sql
SELECT title FROM books WHERE title NOT LIKE 'W%';
```

3. Greater than, GTorEqual to, Less than, Less than or equal too

```sql
SELECT * FROM books WHERE released_year > 2006; # >= | < | <=

# return a boolean
SELECT 99 > 1 #-> 1 = true, 0 = false
SELECT title, released_year > pages FROM books;
```

4. LOGICAL AND (&&)

- Combine two queries that are dependent on each other, i.e both parts have to be true

```sql
# Eggers' books release after 2010
SELECT * FROM books WHERE author_lname='Eggers' AND released_year > 2010;

# Multiple AND operators can be added one after the other
# Get all Eggers recent novels that r in stock
SELECT * FROM books WHERE author_lname='Eggers' AND released_year > 2010 AND title LIKE '%novel%' AND stock_quantity > 0;

# We can double && instead of the word AND
SELECT * FROM books WHERE author_lname='Eggers' && released_year > 2010 && title LIKE '%novel%' && stock_quantity > 0;
```

5. LOGICAL OR (||)

- Query data that for which any of the provided clauses return true, i.e Either Condition 1 applies Or Conditon two or Both

```sql
# Eggers' books release after 2010 or the most recent ones
SELECT * FROM books WHERE author_lname='Eggers' OR released_year=NOW();

# Multiple OR operators can be added one after the other
SELECT * FROM books WHERE author_lname='Eggers' OR author_lname='Smith' OR title LIKE '%novel%' AND stock_quantity > 0;

# We can double && instead of the word AND
SELECT * FROM books WHERE author_lname='Eggers' || author_lname='Smith' || title LIKE '%novel%' && stock_quantity > 0;
```

- Using both the Logical AND and Logical OR together

```sql
SELECT * FROM books WHERE author_lname='Eggers' OR author_lname='Smith' OR title LIKE '%novel%' AND stock_quantity > 0;
```

6. BETWEEN and NOT BETWEEN

- Select a range of values from the stored data
- This can accomplished by Logical And , but BETWEEN is more straight forward

- NOT BETWEEN is the opposite of BETWEEN and we simply prepend an AND before.

```sql
# syntax - take note, this AND is here as a keyword not as an operator
BETWEEN x AND y

#
SELECt * FROM books WHERE released_year BETWEEN 2004 AND 2015;

#
SELECt * FROM books WHERE released_year NOT BETWEEN 2004 AND 2015;
```

> IMportant
> For best results when using `BETWEEN` with date or tme values, use `CAST()` to eexplicitely convert the vallues to the desired data type..
> E.g. If you compare DATETIME values to TIME values, convert the TIME to DATETIME
>
> ```sql
>   SELECT CAST('2013-1-1' AS DATETIME) BETWEEN CAST(NOW() AS DATETIME) AND CAST('2001-1-1' AS DATETIME); # 0 = false
> ```

7. IN and NOT IN

- Allows to provide a set values and check whether the table values match any of the listeed values

```sql
# longer version
SELECT * FROM books WHERE author_lname='Carver' OR author_lname='Lahiri' OR author_lname='Smith';

# IN version
SELECT * FROM books WHERE author_lname IN ('Carver', 'Lahiri', 'Smith');
SELECT * FROM books WHERE released_year IN (2017, 2016, 2015, 2014, 2013, 2012); # Makes this easier
```

- NOT IN is the opposite of IN

> There is a MODULO (%) operator to return the reminder of numbers, used to tell even and odd values

8. CASE STATEMENTS (`CASE...WHEN...THEN...ELSE...END`)

- Allows us to make condition queries and to print conditional data on a larger scale
- We can mow make decisons in our code

```sql
SELECT title, released_year,
  CASE
    WHEN released_year >= 2016 THEN 'Breakthrough'
    WHEN released_year >= 2000 THEN 'Modern Lit'
    ELSE '20th Century Lit'
  END
  AS GENRE #add an aliase
FROM books;


# Graphically represent the stock
SELECT title,
  CASE
    WHEN stock_quantity <=50 THEN '*'
    WHEN stock_quantity <=100 THEN '**'
    WHEN stock_quantity <=150 THEN '***'
    WHEN stock_quantity BETWEEN 150 AND 200 THEN '****'
    ELSE '*****'
  END
  AS IN_STOCK #add an aliase
FROM books;
```

# One To Many relationship

> Relations and Joins

- A real world app db has many tables that contain inter related data, and that depend on each other.
- Real world data is interrelated, eg. data of user accouts, posts, blogs, imgaes, etc
- Eg. in our books app: we need to store orders, authors, versions, customers, transaction information, reviews, Genres

### Types of relationships

1.  One to One

- Not that common
- Eg. One row in a table is related to only one in another table. A user name s associated with one row in a user details table

2.  One to Many

- Most common relationship
- Eg. A book-to-reviews, where one book can have many reviews, and many reviews belong to one book

3.  Many to many

- E.g. Books to authors. A book can have many authors, and each authr can have many books.

1. 1 : MANY

- If we have two tables:: customers and orders tables
- A customer can have many orders
- But an order is associated with exactly one customer

- We want to store, Customers names, email, date and time of purchase, price of order
- we can do it in a giant table with all these columns, but a real app would have several sevaral columns
- And imagine the same person has many orders, we would be storing their names, contacts for evry order. THere would be alot of duplication,
- We may have new customers who dont have orders, so they would also have the order and price columns, which would be null.

- SO, we need to seperate the data in a more efficent, more organised manner
- So, we make two tables, they share a similar column (customer_id) that references data from each table
- Customers -> id, first_name, last_name, email
- orders -> order_id, order_date, amount, customer_id references id in Customers' table

- we use primary keys as the reference b'se they are unique.
- Foreign Keys: These are references to anothe table within a given table
- Schema = The structure of the tables in the db and their relationships

- Implementation

```sql
# customers
CREATE TABLE customers (
  id INT AUTO_INCREMENT PRIMARY KEY,
  first_name VARCHAR(100),
  last_name VARCHAR(100),
  email VARCHAR(100)
);


# orders
CREATE TABLE orders (
  id INT AUTO_INCREMENT PRIMARY KEY,
  order_date DATE,
  amount DECIMAL(8, 2),
  customer_id INT,
  FOREIGN KEY (customer_id) REFERENCES customers(id) # explicitely state the rltnshp
);

#syntax
FOREIGN KEY (col_in_current_table) REFERENCES another_table(col_in_other_tbl_ref)

# sample data
insert into customers (first_name, last_name, email)
values ('Boy', 'George', 'george@gmail.com'),
('George', 'Michael', 'gm@gmail.com'),
('David', 'Bowie', 'dvdbw@gmail.com'),
('Blue', 'Steele', 'blue@gmail.com'),
('Bette', 'Davis', 'bette@gmail.com')

insert into orders (order_date, amount, customer_id)
values ('2016/02/10', 99.99, 1),
('2017/11/11', 33.50, 1),
('2014/12/12', 800.4, 2),
('2015/01/03', 12.3, 2),
('1999/04/11', 450.25, 5);

# Now you cannot insert any data into the orders tables if the foreign key constraint fails i.e if the foreign keys is not found.

```

- Joins
- Allow us to gt data from multiple data and join them in a meaningful way

- cross join

```sql
SELECT * FROM customers, orders; #cross join - meanngless
```

- Explicit join

```sql
SELECT * FROM customers, orders WHERE customers.id=orders.customer_id;
```

- Explicit inner join

```sql
SELECT * FROM customers JOIN orders ON customers.id = orders.customer_id;
```

- Left join
- Returns the union of the two tables but with ever column of the first / left table
- The rows in the first/left table that donot match any data in the right table, ae filled with NULL
- Prepend `LEFT` before `JOIN`

```sql
SELECT first_name, IFNULL(SUM(amount), 0) AS total_spent #substitut NULL with 0
FROM customers
LEFT JOIN orders ON customers.id=orders.customer_id
GROUP BY customers.id
ORDER BY total_spent;
```

```sql
# doing other things onth results of a join
SELECT first_name, last_name, SUM(amount) AS total_spent
FROM customers
JOIN orders
  ON customers.id = orders.customer_id
GROUP BY orders.customer_id
ORDER BY total_spent DESC;

```

- Right Joins.
- Works opposite to Left joins

2. Many To Many
   - E.g. Books & authors, Blog Posts and tags, Students and classe: students can belong to dfft classes, and each class can have dfft students

- We'll build a tv show reviewing application
- We need to store the series data, reviews, reviewers data.
- The series an reviewers table are seperate bu tthey r connected through the reviews tables
- REVIEWERS: id, first_name, last_name
- SERIES: id, title, released_year, genre
- REVIEWS: id, rating, series_id, reviewer_id. The series_id points to the series table, same idea for the reviewer_id foreign key

```sql
# DATA schema
create table reviewers (
  id int primary key,
  first_name VARCHAR(50),
  last_name VARCHAR(50)
);

create table series (
  id int primary key,
  title VARCHAR(50),
  released_year YEAR(4),
  genre VARCHAR(50)
);

create table reviews (
  id int primary key,
  rating decimal(2, 1),
  series_id INT,
  reviewer_id INT,
  foreign key(series_id) references series(id),
  foreign key(reviewer_id) references reviewers(id)
);

# Printing series title and there ratings - joining 2 tables
SELECT title, rating FROM series
JOIN reviews
  ON series.id = reviews.series_id;

# Print series and their avg rating
SELECT title,
AVG(rating) AS average_rating
FROM series
JOIN reviews
  ON series.id = reviews.series_id
GROUP BY series.id
ORDER BY average_rating DESC;

# Print unreviewed series
# Left join takes everything from the left/1st table and outputs them even if they have no reviiews, it polyfills them with NULL
# INNER join only returns matching data
SELECT title AS unreviewed_series
FROM series
LEFT JOIN reviews
  ON series.id=reviews.series_id
WHERE rating IS NULL;

# Print the avg rating for each genre
SELECT
genre,
ROUND(AVG(rating), 2) AS avg_rating
FROM series
INNER JOIN reviews --INNER join is then same as just JOIN
  ON series.id=reviews.series_id
GROUP BY genre;

# Return analytics from data - review count for each reviewer, max and min review
SELECT
first_name, last_name,
COUNT(rating) AS 'COUNT',
IFNULL(MIN(rating), 0.0) AS 'MIN',
IFNULL(MAX(rating), 0.0) AS 'MAX',
ROUND(IFNULL(AVG(rating), 0.0), 2) AS 'AVG',
IF(COUNT(rating) >= 1, 'ACTIVE', 'INACTIVE') AS STATUS

-- CASE
--   WHEN COUNT(rating) >= 1 THEN 'ACTIVE'
--   ELSE 'INACTIVE'
-- END AS 'STATUS'

FROM reviewers
LEFT JOIN reviews
  ON reviewers.id=reviews.reviewer_id
GROUP BY first_name, last_name, rating;

# Get data from all THREE TABLE: Print teh series, the rating each use gave it, and the reviewers name
SELECT
title, rating, CONCAT(first_name, ' ', last_name) AS 'reviewer'
FROM reviewers

INNER JOIN reviews
  ON reviewers.id=reviews.reviewer_id

INNER JOIN series
  ON series.id=reviews.reviewer_id

ORDER BY title;
```

# Instagram database clone

1. Schema design

- What we'll need to store: users, images, likes, hashtags, comments, followers and following
- Tables

  1. Users: id, username, created_at which could also contain | email, pwd, loc, profilepic, etc
  2. Photos: id, image_url, user_id -> (users.id), created_at | loc, type, etc
  3. Comments: id, comment_text, user_id, photo_id, created_at
  4. Likes: user_id, photo_id, created_at
  5. Follows: follower_id, followee_id, created_at
  6. tags: id, tag_name
  7. photo_tags: photo_id, tag_id

```sql
CREATE DATABASE ig_clone_db;
USE ig_clone_db;

#1. users
CREATE TABLE users(
  id INTEGER AUTO_INCREMENT PRIMARY KEY,
  username VARCHAR(50) UNIQUE NOT NULL,
  created_at TIMESTAMP DEFAULT NOW()
);

#2. Photos
CREATE TABLE photos (
  id INTEGER AUTO_INCREMENT PRIMARY KEY,
  image_url VARCHAR(255),
  user_id INTEGER NOT NULL,
  created_at TIMESTAMP DEFAULT NOW(),
  FOREIGN KEY (user_id) REFERENCES users(id)
);

#3. Comments
CREATE TABLE comments(
  id INTEGER AUTO_INCREMENT PRIMARY KEY,
  comment_text VARCHAR(255) NOT NULL,
  user_id INTEGER NOT NULL,
  image_id INTEGER NOT NULL,
  created_at TIMESTAMP DEFAULT NOW(),
  FOREIGN KEY(user_id) REFERENCES users(id),
  FOREIGN KEY(image_id) REFERENCES photos(id)
);

#4. likes
CREATE TABLE likes (
  user_id INTEGER NOT NULL,
  photo_id INTEGER NOT NULL,
  created_at TIMESTAMP DEFAULT NOW(),
  FOREIGN KEY(user_id) REFERENCES users(id),
  FOREIGN KEY(photo_id) REFERENCES photos(id),
  PRIMARY KEY(user_id, photo_id) #both primary keys, so it doesnt allow duplicates
);
#5. Follows
CREATE TABLE follows (
  follower_id INTEGER NOT NULL,
  followee_id INTEGER NOT  NULL,
  created_at TIMESTAMP DEFAULT NOW(),
  FOREIGN KEY (follower_id) REFERENCES users(id),
  FOREIGN KEY (followee_id) REFERENCES users(id),
  PRIMARY KEY(follower_id, followee_id) #make them both unique, i.e no following the same user multiple times
);

#6. hashtags: tags & photo_tags
CREATE TABLE tags (
  id INTEGER AUTO_INCREMENT PRIMARY KEY,
  tag_name VARCHAR(255) UNIQUE,
  created_at TIMESTAMP DEFAULT NOW()
);

CREATE TABLE photo_tags (
  photo_id INT NOT NULL,
  tag_id INTEGER NOT NULL,
  FOREIGN KEY(tag_id) REFERENCES photos(id),
  FOREIGN KEY(tag_id) REFERENCES tags(id),
  PRIMARY KEY (photo_id, tag_id)
);
```

- Working with the data

```sql
#1. Find 5 oldest users
SELECT * FROM users ORDER BY created_at LIMIT 5;

#2. What day of the week do most users register on?
SELECT
  DAYNAME(created_at) AS day,
  COUNT(username) AS total_reg
  FROM users
  GROUP BY day
  ORDER BY total_reg DESC;

#3. Target our inactive users - find users who have never posed a photo
SELECT
  username AS inactive_users #, image_url
  FROM users
  LEFT JOIN photos ON users.id = photos.user_id
  WHERE image_url IS NULL;

#4. Which user has the most likes on a single photo
SELECT photos.image_url, users.id AS user_id, users.username, COUNT(likes.photo_id) AS num_likes
  FROM photos
  JOIN likes ON photos.id = likes.photo_id
  JOIN users ON users.id = photos.user_id
  GROUP BY likes.photo_id, photos.image_url
  ORDER BY num_likes DESC
  LIMIT 10;

#5 How many times does teh average user post
  SELECT (SELECT COUNT(*) FROM photos) / (SELECT COUNT(*) FROM users)
-- SELECT users.username, COUNT(photos.id) AS posts FROM users
-- INNER JOIN photos ON users.id = photos.user_id
-- GROUP BY users.id
-- ORDER BY posts DESC;

#6. 5 most commonly used hastags
SELECT tag_id,tags.tag_name,  COUNT(tag_id) as num_tags
FROM photo_tags
JOIN tags ON tags.id = photo_tags.tag_id
GROUP BY tag_id
ORDER BY num_tags DESC
LIMIT 5;

#7. Find bots - users who have liked every single photo on the site
SELECT
username, COUNT(likes.photo_id) AS num_likes
FROM users
JOIN likes ON users.id = likes.user_id
GROUP BY username
HAVING num_likes = (SELECT COUNT(*) FROM photos);
#-> where doesn't work b'se it should go b4 group by


```

# Web app

- When creating an app that uses an SQL database. THey is a package/module/libary designed for any programming language to inerface with the mysql database. For node js: the `mysql2` and `sqlite3` packages that do this.
- Refer to my server side notes to take a look into this.

# Database Triggers

- SQL statements that are automatiically run whena specific event occurs e.g when data is updataed or deleted
- Normally this logic is implemented by the appliication code (server code) instead of doing it at database level

- Syntax

```sql
CREATE TRIGGER
trigger_name trigger_time trigger_event
  ON table_name FOR EACH ROW
  BEGIN
  ---
  END;

# trigger_time | BEFORE | AFTER
# trigger_event | INSERT | UPDATE | DELETE
# table_name | one of your tables
```

- Applications:
- Validating data and enforcing constraints on data before inserting it. Normally this should occur in the app code

```sql
#simple validation
DELIMITER $$

CREATE TRIGGER must_be_adult # the nameis readability
  BEFORE INSERT ON people FOR EACH ROW
  BEGIN
      IF NEW age < 18 # refers to new data being inserted into the sepcified col
      THEN
        SIGNAL SQLSTATE '45000' # It is a sql thing
          SET MESSAGE_TEXT = 'Must be an adult';

      END IF; # The semi colon enclose a multiple line statement / code block
  END;

$$
DELIMITER

# The delimiter encloses a long code block, even if there are semi colons, the code doesn't run until they r enclosed

#ex2: Prevent self follows
DELIMITER $$
CREATE TRIGGER prevent_self_follows
  BEFORE INSERT ON follows FOR EACH ROW
  BEGIN
    IF NEW.follower_id = NEW.followee_id
    THEN
      SIGNAL SQLSTATE '45000'
      SET MESSAGE_TEXT = 'You cannot follow yourself';;
    END IF;
  END;

$$
DELIMITER
```

- More senseful applcation: Logger triggers
- Store logs of acions that occur on the database

```sql
# logger table
CREATE TABLE unfollows (
  follower_id INTEGER NOT NULL,
  followee_id INTEGER NOT NULL,
  FOREIGN KEY(follower_id) REFERENCES users(id),
  FOREIGN KEY(followee_id) REFERENCES users(id),
  PRIMARY KEY (follower_id, followee_id)
);

# logger trigger
DELIMITER $$
CREATE TRIGGER log_unfollow
  AFTER DELETE ON follows FOR EACH ROW
  BEGIN
    -- INSERT INTO unfollows(follower_id, followee_id)
    -- VALUES(OLD.follower_id, OLD.followee_id)
    # another inseting syntax
    SET
      follower_id = OLD.follower_id,
      followee_id = OLD.followee_id; -- close with a semi colon
  END;
$$
DELIMITER
```

- Managing triggers

```sql
DROP TRIGGER trigger_name;

SHOW TRIGGERS;
```

> Note: triggers can make debugging hard, because thy run in the background and it is hard tell that some changes where ade by triggers

> PS
> When you ned to do something new, try googling it around. Now that you are very familiar and comfortable with SQL
