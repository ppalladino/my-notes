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

## Basic Operations

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
