---
title: SQL Basic
date: 2020-1-24
tags: 
	- SQL
	- Data Science
	- Database
categories: 
	- Computer Science
	- Big Data
	- SQL
---
# Basic Syntax

## CREATE

```sql
CREATE People 

CREATE TABLE Users(
name VARCHAR(128),
email VARCHAR(128)
);

DESCRIBE People;
```

## DROP

```sql
DROP TABLE Users;
```

## INSERT INTO

```sql
INSERT INTO Users (name, email) VALUES ('Chuck', 'csev@umich.edu') ;
INSERT INTO Users (name, email) VALUES ('Somesh', 'somesh@umich.edu') ;
INSERT INTO Users (name, email) VALUES ('Caitlin', 'cait@umich.edu') ;
INSERT INTO Users (name, email) VALUES ('Ted', 'ted@umich.edu') ;
INSERT INTO Users (name, email) VALUES ('Sally', 'sally@umich.edu') ;
```

## DELETE

```sql
DELETE FROM Users WHERE email='ted@umich.edu'
```

## UPDATE

Replace / Change the values

```sql
UPDATE Users SET name='Charles' WHERE email='csev@umich.edu'
```

## SELECT

Retrieving Records

```sql
SELECT * FROM Users
```

### WHERE

```sql
SELECT * FROM Users WHERE email='csev@umich.edu'
```

here, `*` is for all the columns

### ORDER BY

```sql
SELECT * FROM Users ORDER BY email
```

### LIKE

Include or some characteristics

```sql
SELECT * FROM Users WHERE name LIKE '%e%'
```

### LIMIT

```sql
SELECT * FROM Users ORDER BY email DESC LIMIT 2;
SELECT * FROM Users ORDER BY email LIMIT 1,2;
```

### COUNT

Counting rows with select

```sql
SELECT COUNT(*) FROM Users;
SELECT COUNT(*) FROM Users WHERE email='csev@umich.edu';
```



# Data Types

## String Fields

String Fields are indexable for searching

### CHAR

__CHAR__ allocates the entire space (faster for small strings where length is known)

### VARCHAR

__VARCHAR__ allocates a variable amount of space depending on the data length (less space)

## Text Fields

Have a character set - paragraphs or HTML pages

Generally not used with indexing or sorting - and only then limited to a prefix

+ TINYTEXT

+ TEXT
+ MEDIUMTEXT

+ LONGTEXT

## Binary Types (rarely used)

Character = 8 - 32 bits of information depending on character set

## Binary Large Object (BLOB)

Large raw data, files, images, word documents, PDFs, movies, etc.

No translation, indexing, or character set.

## Integer Numbers

+ TINYINT (-128, 128)
+ SMALLINT (-32768, +32768)
+ INT or INTEGER (2 Billion)
+ BIGINT - (10**18 ish)

## Floating Point Numbers

+ FLOAT (32-bit) 10**38 with seven digits of accuracy
+ DOUBLE (64-bit) 10**308 with 14 digits of accuracy

## Dates

+ TIMESTAMP - 'YYYY-MM-DD HH:MM:SS' (1970, 2037)
+ DATETIME - 'YYYY-MM-DD HH:MM:SS'
+ DATE - 'YYYY-MM-DD'
+ TIME - 'HH:MM:SS'
+ Built-in MySQL function `NOW()`



# Database Keys and Indexes

## AUTO_INCREMENT

```sql
DROP TABLE Users;

CREATE TABLE Users (
user_id INT UNSIGNED NOT NULL
AUTO_INCREMENT,
name VARCHAR(128),
email VARCHAR(128),
PRIMARY KEY(user_id),
INDEX(name)
);


INSERT INTO Users (name, email) VALUES ('Chuck', 'csev@umich.edu');
INSERT INTO Users (name, email) VALUES ('Somesh', 'somesh@umich.edu');
INSERT INTO Users (name, email) VALUES ('Caitlin', 'cait@umich.edu');
INSERT INTO Users (name, email) VALUES ('Ted', 'ted@umich.edu');
INSERT INTO Users (name, email) VALUES ('Sally', 'sally@umich.edu');
```

## Specifying Indexes

```sql
ALTER TABLE Users ADD INDEX ( email ) USING BTREE
```

Relation, B-Tree and Hashes