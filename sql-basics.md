## postgreSQL Syntax
Keywords can be in all caps. It is not required, but it can improve readability as you get used to the syntax and in code.

### CREATE TABLE

```
CREATE TABLE users (
    id SERIAL PRIMARY KEY NOT NULL,
    username VARCHAR(12) UNIQUE,
    active BOOLEAN,
    created TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

```
#### Column Types
https://www.postgresql.org/docs/9.5/static/datatype.html
* varchar - varying character
* int - integer
* boolean
* timestamp - other date/time
* serial

#### Constraints on Columns
* primary key
* unique
* not null
* foreign key

#### Other Column Modifiers
* default current_timestamp

## CRUD OPERATIONS
### Insert
_create_ new row ("instance of entity" or record)

```
INSERT INTO users (username, active) VALUES ('millie11', true );
```
Must meet constraints and other modifiers for query to succeed. If a column is not included it must have a default or an auto increment.

### Select
_read_ from the table

```
SELECT * FROM users;
```
* wildcard is the * (splat) and means select all columns

#### WHERE clause
Allows you to limit search by column values.

```
SELECT * FROM users WHERE active=true;

SELECT * FROM users WHERE username='millie11';
```

##### AND or OR
```
SELECT * FROM users WHERE active=true AND username='millie11';
```

##### IN
```
SELECT * FROM users WHERE username IN ('millie', 'lisa');
```

#### Select certain columns

```
SELECT username FROM users;
```

#### Alias
alias column and table names with 'AS'

```
SELECT username AS "User Name" FROM users;
```

#### ORDER BY

```
SELECT * FROM users ORDER BY username;

SELECT * FROM users ORDER BY id DESC;
```

#### LIMIT
```
SELECT * FROM users LIMIT 2;
```

#### LIKE

```
SELECT * FROM users WHERE username LIKE '%millie%';
```

### UPDATE
_update_ existing rows

```
UPDATE users SET username='millie' WHERE username='millie11';

UPDATE users SET active=true WHERE id=2;
```

### DELETE
_delete_ existing rows

```
DELETE FROM users WHERE id=1;

DELETE FROM users WHERE username='bob1';
```

### Aggregate Functions
[https://www.postgresql.org/docs/9.4/static/functions-aggregate.html
](https://www.postgresql.org/docs/9.4/static/functions-aggregate.html)
#### COUNT

```
SELECT COUNT(*) FROM users;

SELECT COUNT(username) FROM users;
```

Other useful aggregate functions exist. SUM can be used to add up all rows in a column. This could be good for money. Or MAX which can find the MAX value of a given column

### Alter Table 
You can change the table columns, types, or even drop a column. Do this carefully, because it could conflict with records that are currently stored. Below is an example of dropping a column from users table called column5. 

```	
ALTER TABLE users DROP COLUMN column5;
```

A good tutorial with examples of alter table statements: [http://www.tutorialspoint.com/postgresql/postgresql_alter_command.htm](http://www.tutorialspoint.com/postgresql/postgresql_alter_command.htm)

### Drop Table
To completely delete a table from your database. 

```
DROP TABLE users;
```