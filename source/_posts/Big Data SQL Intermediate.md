---
title: SQL Intermediate
date: 2020-1-25
tags: 
	- SQL
	- Database
categories: 
	- Computer Science
	- Big Data
	- SQL
---
# Speed Up Querying

## Index

### General Index

For a `students` table:

| id   | class_id | name  | gender | score |
| ---- | -------- | ----- | ------ | ----- |
| 1    | 1        | Alex  | M      | 90    |
| 2    | 1        | Bob   | M      | 95    |
| 3    | 1        | Cindy | F      | 88    |

If we want to query by score quickly, we can create an index for score.

```sql
ALTER TABLE students
ADD INDEX idx_score (score);
```

The name of index `idx_score` could be anything. If there are multiple indexes, then

```sql
ALTER TABLE students
ADD INDEX idx_name_score (name, score);
```

+ The index should be updated when inserting or deleting the records.

## Unique Index

The unique column which is not primary key can be assigned with a unique index

```sql
ALTER TABLE students
ADD UNIQUE INDEX uni_name (name);
```

We can also add unique constraint to a column rather than unique index

```sql
ALTER TABLE students
ADD CONSTRAINT uni_name UNIQUE (name);
```



## Get more complex

```sql
SELECT Track.title, Genre.name FROM Track JOIN Genre ON Track.genre_id = Genre.genre_id

SELECT Track.title, Artist.name, Album.title, Genre.name FROM Track JOIN Genre JOIN Album JOIN Artist ON Track.genre_id = Genre.genre_id AND Track.album_id = Album.album_id AND Album.artist_id = Artist.artist_id
```

## ON DELETE CASCADE

+ Default / Restrict - Don’t allow changes that break the constraint
+ CASCADE – Adjust child rows by removing or updating to maintain consistency
+ SET NULL – Set the foreign key columns in the child rows to null

```sql
DELETE FROM Genre WHERE name = 'Metal'
```

# Many to Many Relationships

+ Sometimes we need to model a relationship that is many to many.
+ We need to add a “connection” table with two foreign keys.
+ There is usually no separate primary key

```sql
CREATE TABLE User (
user_id INTEGER NOT NULL AUTO_INCREMENT PRIMARY KEY,
email VARCHAR(128) UNIQUE,
name VARCHAR(128)
) ENGINE=InnoDB CHARACTER SET=utf8;

CREATE TABLE Course (
course_id INTEGER NOT NULL AUTO_INCREMENT PRIMARY KEY,
title VARCHAR(128) UNIQUE
) ENGINE=InnoDB CHARACTER SET=utf8;
```

## Combination Keys

+ Combination key is unique

```sql
CREATE TABLE Member (
user_id INTEGER,
course_id INTEGER,
role INTEGER,
CONSTRAINT FOREIGN KEY (user_id) REFERENCES User (user_id)
ON DELETE CASCADE ON UPDATE CASCADE,
CONSTRAINT FOREIGN KEY (course_id) REFERENCES Course (course_id)
ON DELETE CASCADE ON UPDATE CASCADE,
PRIMARY KEY (user_id, course_id)
) ENGINE=InnoDB CHARACTER SET=utf8;
```

+ Insert contents:

```sql
INSERT INTO User (name, email) VALUES ('Jane', 'jane@tsugi.org');
INSERT INTO User (name, email) VALUES ('Ed', 'ed@tsugi.org');
INSERT INTO User (name, email) VALUES ('Sue', 'sue@tsugi.org');
INSERT INTO Course (title) VALUES ('Python');
INSERT INTO Course (title) VALUES ('SQL');
INSERT INTO Course (title) VALUES ('PHP');

INSERT INTO Member (user_id, course_id, role) VALUES (1, 1, 1);
INSERT INTO Member (user_id, course_id, role) VALUES (2, 1, 0);
INSERT INTO Member (user_id, course_id, role) VALUES (3, 1, 0);
INSERT INTO Member (user_id, course_id, role) VALUES (1, 2, 0);
INSERT INTO Member (user_id, course_id, role) VALUES (2, 2, 1);
INSERT INTO Member (user_id, course_id, role) VALUES (2, 3, 1);
INSERT INTO Member (user_id, course_id, role) VALUES (3, 3, 0);
```

+ Select rows you want: 

```sql
SELECT User.name, Member.role, Course.title
FROM User JOIN Member JOIN Course
ON Member.user_id = User.user_id AND
Member.course_id = Course.course_id
ORDER BY Course.title, Member.role DESC, User.name
```

# Complexity Enables Speeds

+ Complexity makes speed possible and allows you to get very fast results as the data size grows.
+ By normalizing the data and linking it with integer keys, the overall amount of data which the relational database must scan is far lower than if the data were simply flattened out.
+ It might seem like a tradeoff - spend some time designing your database so it continues to be fast when your application is a success.



# Other Usage

## UNION ALL

`UNION` is used to merge two or multiple resulting set of SELECT. The Name, datatype and order of column should be identical. `UNION` is used to select the different records from both SELECT.

```sql
SELECT column_name(s) FROM table1
UNION
SELECT column_name(s) FROM table2;
```

If allowing the duplicated records, we should use UNION ALL.

```sql
SELECT column_name(s) FROM table1
UNION ALL
SELECT column_name(s) FROM table2;
```

With `where` operation:

```sql
SELECT column_name(s) FROM table1
WHERE column_name(1)='xx'
UNION ALL
SELECT column_name(s) FROM table2
WHERE column_name(1)='xx'
ORDER BY column_name(1);
```



