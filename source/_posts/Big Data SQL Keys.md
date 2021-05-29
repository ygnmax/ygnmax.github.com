---
title: SQL Keys
date: 2020-1-25
tags: 
	- SQL
	- Database
categories: 
	- Computer Science
	- Big Data
	- SQL
---
# Key Terminology

## Three Kinds of Keys

### Primary key

+ generally an integer autoincrement field, indicating the row.

+ Relationships that are based on matching string fields are less efficient than integers.

### Logical key

+ what the outside world uses for lookup.
+ __Never use your logical key as the primary key__.
+ Logical keys can and do change, albeit slowly.

### Foreign key

+ A foreign key is when a table has a column containing a key that points to the primary key of another table.

# One to Many / Many to One

```sql
CREATE DATABASE Music DEFAULT CHARACTER SET utf8;

USE Music;

CREATE TABLE Artist (
  artist_id INTEGER NOT NULL AUTO_INCREMENT,
  name VARCHAR(255),
  PRIMARY KEY(artist_id)
) ENGINE = InnoDB;

CREATE TABLE Album (
  album_id INTEGER NOT NULL AUTO_INCREMENT,
  title VARCHAR(255),
  artist_id INTEGER,

  PRIMARY KEY(album_id),
  INDEX USING BTREE (title),

  CONSTRAINT FOREIGN KEY (artist_id)
    REFERENCES Artist (artist_id)
    ON DELETE CASCADE ON UPDATE CASCADE
) ENGINE = InnoDB;


CREATE TABLE Genre (
  genre_id INTEGER NOT NULL AUTO_INCREMENT,
  name VARCHAR(255),
  PRIMARY KEY(genre_id)
) ENGINE = InnoDB;

CREATE TABLE Track (
  track_id INTEGER NOT NULL AUTO_INCREMENT,
  title VARCHAR(255),
  len INTEGER,
  rating INTEGER,
  count INTEGER,
  album_id INTEGER,
  genre_id INTEGER,

  PRIMARY KEY(track_id),
  INDEX USING BTREE (title),

  CONSTRAINT FOREIGN KEY (album_id) REFERENCES Album (album_id)
    ON DELETE CASCADE ON UPDATE CASCADE,
  CONSTRAINT FOREIGN KEY (genre_id) REFERENCES Genre (genre_id)
    ON DELETE CASCADE ON UPDATE CASCADE
) ENGINE = InnoDB;
```

## JOIN

The JOIN operation links across several tables as part of a SELECT operation;

```sql
SELECT Album.title, Artist.name FROM Album JOIN Artist ON;
```

+ You must tell the JOIN how to use the keys that make the connection between the tables __using an ON clause__

```sql
SELECT Album.title, Album.artist_id, Artist.artist_id,Artist.name
FROM Album JOIN Artist ON Album.artist_id = Artist.artist_id
```

+ Joining two tables __without an ON clause__ gives all possible combinations of rows

```sql
SELECT Track.title, Track.genre_id, Genre.genre_id, Genre.name FROM Track JOIN Genre
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