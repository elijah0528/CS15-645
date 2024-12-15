## SQL Pt. 1
- Data-definition language (DDL): Allows specifications relating
	- Schema of a relation
	- Type of values associated with each attribute
	- Integrity constants
	- Set of indices to be maintained for each relation
	- Security and authorization for each relation
	- Physical storage structure of each relation on disk
- Domain types in SQL
	- char(n): Fixed length string of length n
	- varchar: Variable length of character string
	- int: Integer
	- smallint: Small Integer
	- numeric(p, d): Fixed point number with user-specified precision, p, and d digits to the right of the decimal point
	- real, double precision: Floating and double floating point precision
	- float(n): Float with at least n digits
```SQL
create table r (
A1 D1, A2 D2, An Dn,
(integrity constant1),
(integrity constant2),
(integrity constantn)
)
```
- A is attribute name, D is domain type
```SQL
create table instructor ( 
	ID char(5), 
	name varchar(20), 
	dept_name varchar(20), 
	salary numeric(8,2),
	primary key(ID),
	foreign key(dept_name) references department
);
```
- Types of integrity constants are: primary key, foreign key references, not null
- Operations:
	- Insert: inserts entries
	- Delete: Removes tuples from the relation
	- Drop Table: Deletes an entire table
	- Alter: Adds or removes attributes from a table
- Select lists attributes desired in the query
	- Equivalent to a projection
	- SQL allows for duplicates so use distinct to eliminate this
```SQL
select distinct dept_name from instructor
select all dept_name from instructor
```
- Attribute can be selected with: 
	- \*: is used for all
	- Attribute can be selected with no from clause (select '427' as FOO)
	- Operations can be used as well (select salary/12 as monthly_salary)
- Where specifies predicates that must be satisfied
	- Equivalent to a select
	- Can use connectives and, not, or
```SQL
select name from instructor where dept_name = "Comp. Sci" and salary > 80000
```
- From specifies the relations in the query
	- Equivalent to the cartesian product
```
select * from instructor, teaches
```
	- Generates every possible combination of instructors and courses to be taught
- Renaming relations and attributes can be done with the as clause
---------
- Aggregates:  Functions that returns a single value for a list of tuples
	- AVG, MIN, MAX, SUM, COUNT
```SQL
SELECT AVG(gpa), COUNT(sid) FROM student WHERE login LIKE '%@cs'
```
	- Returns the number of students who's logic has @cs in it
	- Like is a wildcard and % is any number of characters
```SQL
SELECT AVG(gpa), ANY_VALUE(e.cid) FROM enrolled AS e JOIN student as s ON e.sid = s.sid
```
	- Gets average GPA of students enrolled in each course
```SQL
SELECT AVG(gpa), e.cid FROM enrolled AS e JOIN student AS s where e.sid = s.sid GROUP BY e.cid
```
- Anything that will be in the output has to be in the GROUP BY clause or else use ANY_VALUE
