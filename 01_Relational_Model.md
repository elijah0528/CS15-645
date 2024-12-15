## Relational Languages
- Set of allowed values for the attribute is the domain
	- Attribute values are usually atomic – indivisible
	- Must have a null value
- Relations are unordered
- Database Schema: Logical structure of the database
- Database Instance: Snapshot of the data at a given time
- Superkey: K is a superkey of R if K is sufficient to identify a unique tuple of each possible relation
	- Candidate Key: A special type of superkey that is minimal – if any attributes of the key is removed, it doesn't work
	- One of the candidate keys is selected to be the primary key
- Foreign Key: Value in one relation must appear in another
### Relational Algebra
- Operators that will be used
	- $\sigma$: Select
	- $\Pi$: Project
	- $\cup$: Union
	- $-$: Set difference
	- $\times$: Cartesian Product
	- $\rho$: Rename
- Select Operation ($\sigma_p (r)$): Selects tuples that satisfy a given predicate
	- $p$ is the selection predicate

> **Example**
> 	- "Find the instructors in Physics with a salary greater $90,000"
> 		- $sigma_{dept\_name = Physics \land salary > \$90000} (instructor)$
> 	- "Find the departments whose name is the same as their building"
> 		- $sigma_{dept\_name = building} (department)$

- Project Operation($\Pi_{A_1, A_2, A_k} (r)$): Returns an argument relation with attributes left out
- Relational operators can be composed into a relational algebra expression
- Cartesian Product: Every possible tuple of any two relations
	- This produces a lot relations which may not be in the original relation
- Join operator:  Selecting from a cartesian product allows us to join two tables together
	- Example: $\sigma_{instructor|_id = teaches\_id} (instructor \times teaches)$
	- Syntax: $r \bowtie_\theta s = \sigma_{\theta} (r \times s)$
- Union operator allows us to combine two relations
	- Must have the same arity (same number of attributes)
	- Attributes must be compatible
- Set difference finds tuples that are in one relation but not the other
	- Must be with compatible relations
- Assignment operator($\gets$) assigns parts of a relational algebra expression to a variable
- Results of relational algebra expressions don't have names so use $\rho_x (E)$ to give E the name x

---------------------
- Document Data Model: Data is hierarchical and so data must be stored as such (via JSON) rather than relationally 
	- 
