## postgreSQL Syntax
Keywords can be in all caps. It is not required, but it can improve readability as you get used to the syntax and in code.

### CREATE TABLE

```
CREATE TABLE users (
    id SERIAL PRIMARY KEY NOT NULL,
    username VARCHAR(12) UNIQUE,
    active BOOLEAN,
    created TIMESTAMP DEFAULT current_timestamp
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
UPDATE users set username='millie' where username='millie11';

UPDATE users set active=true where id=2;
```

### DELETE
_delete_ existing rows

```
DELETE from users where id=1;

DELETE from users where username='bob1';
```

### Aggregate Functions
https://www.postgresql.org/docs/9.4/static/functions-aggregate.html

#### COUNT

```
SELECT COUNT(*) FROM users;

SELECT COUNT(username) FROM users;
```

#### MAX

```
SELECT MAX(created) FROM users;
```
