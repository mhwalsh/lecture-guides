## postgreSQL Joins and Relational Databases

### Types of Table Relationships
1. **One to One**
	* Ex. States to capitals. A state has one capital. A capital is in one state.  
	* Diagramed with a Entity Relational Diagram (ERD):
	
	```
	[] -- []
	```
2. **One to Many**
	* Cohort to students (at Prime). A Cohort has many students. A student has only one cohort. 
	* Diagramed with a Entity Relational Diagram (ERD):
	
	```
	[] --< []
	```
3. **Many to Many**
	* Ex. Books to authors. A book can have many authors. An author can have written many books.
	* Requires a join or junction table.
	* Diagramed with a Entity Relational Diagram (ERD):
	
	```
	[] >--< []
	```

#### Types of Joins
* **Inner** - Gives all records that exist in both tables.
* **Left** - Gives all records that exist in the left table. Fills in blanks from the right table with NULL.
* **Right** - Gives all records that exist in the right table. Fills in blanks from the left table with NULL.
* **Full Outer** - Gives all records that exist in both tables. Fills in blanks from both tables with NULL.

### Base Syntax

```
SELECT * from <left_table> <join type> JOIN <right_table> ON <left_table>.<field> = <right_table>.<field>;
```
* < join type > - INNER, LEFT, RIGHT, FULL OUTER
* < field > - an id from both tables that is the same and that you want to equate.

### Examples of Join Syntax
These examples are from lecture. Come see me if you want to see the database.

##### One to Many Join
Requires one join statement.

```
SELECT * FROM staff
INNER JOIN lectures ON staff.id = lectures.staff_id
WHERE staff.id = 6;
```
Note you can tack on clauses like 'WHERE' just like any other SELECT statement we have worked with.

##### Many to Many Join
Requires at least two join statements because you have to join through the join/junction table. 

```
SELECT * FROM staff
JOIN staff_department ON staff.id = staff_department.staff_id
JOIN department ON staff_department.department_id = department.id
WHERE department.name = 'instruction';
```

