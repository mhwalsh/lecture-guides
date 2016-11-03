## Create Table

```
CREATE TABLE staff (
	id SERIAL PRIMARY KEY,
	name VARCHAR(200)
);

CREATE TABLE department (
	id SERIAL PRIMARY KEY,
	name VARCHAR(200)
);

CREATE TABLE staff_department (
	staff_id INT REFERENCES staff(id) ON DELETE CASCADE,
	department_id INT REFERENCES department(id) ON DELETE CASCADE
);

CREATE TABLE lecture (
	id SERIAL PRIMARY KEY,
	name VARCHAR(100), 
	staff_id INT REFERENCES staff(id) ON DELETE CASCADE
);
```

## create
#### New department
- INSERT into department when a new department is created, could be linked to a UI

```
INSERT INTO department (name) VALUES ('billing');
```
##### New staff
- INSERT into staff, when a new staff member is hired

```
INSERT INTO staff (id, name) VALUES (9, 'some') RETURNING id;
```
##### Inserting into the join table
- Add a staff member to a department, depending on the scenario any combination of these first three queries could happen together. 
- transaction - "highlevel" 

```
INSERT INTO staff_department (staff_id, department_id) VALUES (8,10);
```
##### Don't know the id
- What happens when you don't know the id? What do you know? Depending on what the UI knows you can do a SELECT first to find the id

```
SELECT * FROM staff WHERE name='Luke'; 
```
- ^ may need to use 'like' here.
- ^This is going to be case sensitive, so how does that affect the UI

##### RETURNING id

```
INSERT INTO staff (id, name) VALUES (9, 'some') RETURNING id;
```

## read
- JOINS! many to many and one to many

## update 
- very similarly to INSERTS, shouldn't have to change relationships unless someone moves or adds a department.

```
UPDATE staff SET name='taylor' where name='Taylor';
```

## delete
- redo the create sql syntax w/cascading
with ON DELETE CASCADE delete syntax looks the same, but see what happens

```
DELETE FROM staff WHERE id=5;
```

## Dynamic queries vs start up code
- our db is local, what happens when we deploy?
	- what happens when you turn it in and someone needs to grade it, check it out or run it?
- how to save things - for now .sql file in the root 
- future: db migration tools - think about your db as a living document, you can't whip it every time you make a new feature etc.