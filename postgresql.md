# PostgreSQL

## PostgreSQL Install <a href="#ea3c" id="ea3c"></a>

from [https://medium.com/@viviennediegoencarnacion/getting-started-with-postgresql-on-mac-e6a5f48ee399](https://medium.com/@viviennediegoencarnacion/getting-started-with-postgresql-on-mac-e6a5f48ee399)

## Starting and stopping PostgreSQL <a href="#e02c" id="e02c"></a>

```
# Start the service
> brew services start postgresql

# enter psql terminal
> psql postgres

# enter psql terminal as a user
> psql postgres -U <user>

# exit psql terminal
> \q

# stop the service
> brew services start postgresql
```

## Common Commands

```
> # DATABASES

> # create
> CREATE DATABASE <db name> OWNER <owner name>;

> # list databases
> \list

> # connect to a database
> \connect <db name>

> # list tables in the connected db
> \dt

> # create table in the connected db
> CREATE TABLE <table name> (id INTEGER PRIMARY KEY, title VARCHAR);
```

## POC

```
> # created a user
> CREATE ROLE paul WITH LOGIN PASSWORD 'asdfasdf';
> ALTER ROLE paul CREATEDB;

> # enter psql terminal
> psql postgres -U paul

> CREATE DATABASE mathtastic OWNER paul;
> \connect mathtastic

> # create tables
> CREATE TABLE tags (id INTEGER PRIMARY KEY, content_id INTEGER, title VARCHAR);
> CREATE TABLE limiters (id INTEGER PRIMARY KEY, skill_id INTEGER, regex VARCHAR);

> # add tags data
> INSERT INTO tags(id, content_id, title) VALUES (1, 1, '1+2=3');
> INSERT INTO tags(id, content_id, title) VALUES (2, 1, '3+4=5');
> INSERT INTO tags(id, content_id, title) VALUES (3, 2, '1-2=1');

> # add limters data
> INSERT INTO limiters(id, skill_id, regex) VALUES (101, 101, '^(10|[1-9])\+(10|[1-9])\=?(0|[1-9]\d*)$');
> INSERT INTO limiters(id, skill_id, regex) VALUES (102, 102, '^(10|[1-9])\-(10|[1-9])\=?(0|[1-9]\d*)$');

> # get the addition
> SELECT * FROM tags WHERE title ~ '^(10|[1-9])\+(10|[1-9])\=?(0|[1-9]\d*)$';

> # match from content perspective
> SELECT title, regex
> FROM tags
> INNER JOIN limiters
>    ON title ~ regex
>    AND content_id = 1;
>
> # above query returns
> 1+2=3 | ^(10|[1-9])\+(10|[1-9])\=?(0|[1-9]\d*)$
> 3+4=5 | ^(10|[1-9])\+(10|[1-9])\=?(0|[1-9]\d*)$
>
> # match from skill perspective
> SELECT title, regex
> FROM tags
> INNER JOIN limiters
>    ON title ~ regex
>    AND skill_id = 101;
>
> # above query returns
> 1+2=3 | ^(10|[1-9])\+(10|[1-9])\=?(0|[1-9]\d*)$
> 3+4=5 | ^(10|[1-9])\+(10|[1-9])\=?(0|[1-9]\d*)$

```
