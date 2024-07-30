# Databases-and-SQL-for-Data-Science-with-Python
This is my summary from this course that i'm getting by IBM on Coursera 
# MODULE 1
## Basic SQL Commands
- Create a table
- Insert
- Select
- Update
- Delete

## SELECT Statment
SELECT is use to see the data
```SELECT * from <tablename>``` <b>
e.g. let's say that a table called "Movies" has some columns as Title, Edition, Year, .. <b>
You can select everything: ```SELECT * from Movies```; <b>
or to specify columns: ```SELECT <Title>,<Year> from Movies```
### WHERE
Where is use to restricts the result set, or as kind of a Filter. <b>
It's evaluate to: True, False or Unknown.
The comparison operators are:
```
Equal to: = 
Greater than: >
Lesser than: <
Greater than or equal to: >=
Less than or equal to: <=
Not equal to: <>
```
e.g: 
```
SELECT * FROM Movies
WHERE Year > 2000;
```
### COUNT, DISTINCT, LIMIT
- COUNT: It's use to count the rows or lines from a data. It can be used with 'WHERE':
```
SELECT COUNT(Title) from Movies
WHERE Title = 'STAR';
```
- DISTINCT: It's use to removes duplicate values from a result:
```
SELECT DISTINCT Title from Movies
WHERE Title = 'STAR';
```
- LIMIT: Restricts the number of rows retrieved from the database:
```
SELECT * from Movies
WHERE Year = 2024 LIMIT 5
```

## INSERT Statment
Used to read and modfy data
```
INSERT INTO Movies
  (Title, Edition, Year)
VALUES ('Star Wars', 'The Last Jedi', '2017')
```

## UPDATE and DELETE Statment
To update something in the dataset:
```
UPDATE Movies SET Edition 'The Last Jedi (Edition VIII)'
WHERE Year = 2017, Title = 'Star Wars';
```
To delete, as to update, the row has to be specified in the WHERE condition:
To update something in the dataset:
```
DELETE FROM Movies
WHERE Edition = 'The Last Jedi (Edition VIII)';
```

# MODULE 2
## Types of SQL statements
### DDL (Data Definition Language)
It's use to define, change or drop data:
```
CREATE
ALTER
TRUNCATE
DROP
```
### DML (Data Manipulation Language)
It's use to read and modify data:
```
INSERT
SELECT
UPDATE
DELETE
```
## CREATE TABLE statements
To create a table, it's necessary to define the column name plus datatypes:
```
CREATE TABLE NFL_Teams(
  id CHAR(2) PRIMARY KEY NOT NULL,
  name VARCHAR(24) NOT NULL,
  city VARCHAR(15) NOT NULL,
  state VARCHAR(15) NOT NULL
)
```
```
INSERT INTO NFL_Teams VALUES
	(1, 'Arizona Cardinals', 'Phoenix', 'AZ'),
	(2, '49ers', 'San Francisco', 'SA');
```	
## ALTER, DROP, and Truncate Tables
- ALTER: Add or remove columns, keys or constraints. It also modifies datatype of columns.
to add columns:
```
ALTER TABLE Movies
  ADD COLUMN Season CHAR(12);
```
to modify datatype of a column:
```
ALTER TABLE Movies
MODIFY Year CHAR(4);
```
to drop column:
```
ALTER TABLE Movies
  DROP COLUMN Title;
```
to remove the table from the database:
```
DROP TABLE Movies;
```
- TRUNCATE: It deletes all rows of data in a table
```
TRUNCATE TABLE Movies;
  IMMEDIATE;
```
### e.g. coding on IBM DB2 on Cloud
![](https://raw.githubusercontent.com/gboaventura93/Databases-and-SQL-for-Data-Science-with-Python/main/assets/Screenshot_IBM_Cloud1.png)

# MODULE 3
## String Patterns and Ranges
To use a *String Pattern*, it's just to use the LIKE + letter(s) + %, _ or both:
```
SELECT Title FROM Movies
WHERE Title LIKE 'S%'
```
```
WHERE Title LIKE 'Star_s'
```
```
WHERE Title LIKE '%Wa_s'
```
For *Range*, we can use AND, BETWEEN, OR and IN:
```
SELECT Year FROM Movies
WHERE Year >= 2005 AND Year <=2015
```
```
WHERE Year BETWEEN 2005 AND 2015
```
## Sorting Results Sets
*ORDER BY* will order the selection:
```
SELECT Title from Movies
	ORDER BY Title (ASC [Default] or DESC)
```
## Grouping Result Sets
*DISTINCT* is use to eliminate Duplicates values in the database:
```
SELECT DISTINCT(Title) FROM Movies
```
*GROUP BY* could be use to count variables:
```
SELECT Title, COUNT(Title) FROM Movies
	GROUP BY Title
```
*HAVING* could be use as a kind of condition:
```
SELECT Title, COUNT(Title) AS COUNT FROM Movies
	GROUP BY Title
	HAVING COUNT(Title) > 2
```
