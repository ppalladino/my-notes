# SQL

```
// Some code

// return all records from a table
SELECT * FROM <TABLE NAME>;
```

## Common Types

|           |                                     |
| --------- | ----------------------------------- |
| `INTEGER` | a positive or negative whole number |
| `TEXT`    | a text string                       |
| `REAL`    | a decimal value                     |
| `DATE`    | the date formatted as YYYY-MM-DD    |

## Table Operations

```sql
// Create table
// Docs for constraints: https://www.w3schools.com/sql/sql_constraints.asp

CREATE TABLE celebs (
   id INTEGER PRIMARY KEY, 
   name TEXT UNIQUE,
   date_of_birth TEXT NOT NULL,
   date_of_death TEXT DEFAULT 'Not Applicable'
);

// Insert record

INSERT INTO celebs (id, name, age) 
VALUES (1, 'Justin Bieber', 22);

// Add new column to existing table

ALTER TABLE celebs 
ADD COLUMN twitter_handle TEXT;

// Edit an exiting row in a table

UPDATE celebs 
SET twitter_handle = '@taylorswift13' 
WHERE id = 4; 

// Delete a record

DELETE FROM celebs 
WHERE twitter_handle IS NULL;
```

## Selecting

```sql
// Single character wildcard '_'
// Will return 'Seven', 'Se7ven', etc...

SELECT * 
FROM movies
WHERE name LIKE 'Se_en';

// Zero or more missing characters use '%'

SELECT * 
FROM movies 
WHERE name LIKE '%man%';

// Selecting a numerical range
// Will return all values between 1990 and (including) 1999

SELECT *
FROM movies
WHERE year BETWEEN 1990 AND 1999;

// Note: alphabetical values are a little tricky
// Will return values: 'A', 'Apples', 'J', but not 'Jake' b/c 'Jake' is after 'J'

SELECT *
FROM movies
WHERE year BETWEEN 'A' AND 'J';

// Use AND for set intersction

SELECT *
FROM movies
WHERE year BETWEEN 1970 AND 1979
  AND imdb_rating > 8;
  
SELECT *
FROM movies
WHERE year < 1985
  AND genre = 'horror';
  
// Use OR for set union

SELECT *
FROM movies
WHERE genre = 'romance'
   OR genre = 'comedy';
   
// Create new field and give value using if/else logic 
SELECT name,
 CASE
  WHEN imdb_rating > 8 THEN 'Fantastic'
  WHEN imdb_rating > 6 THEN 'Poorly Received'
  ELSE 'Avoid at All Costs'
 END AS 'review'
FROM movies;

```
