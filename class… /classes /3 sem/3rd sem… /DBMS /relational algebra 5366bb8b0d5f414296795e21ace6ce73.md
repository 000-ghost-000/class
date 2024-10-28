# relational algebra

is a procedural query language and it is foundation for relational data model 

it consist of 2 types of operators 

- unary
    - are those operators which require only one operand to operate
    - 2 unary operators
        - selection operator - represented by sigma (𝛔) and is used to select the complete record from table without any condition
            - lets consider a table emp if we want to select the employee who are from knp then SQL is
            
            ![image.png](relational%20algebra%205366bb8b0d5f414296795e21ace6ce73/image.png)
            
            ```sql
            select * from emp where city = 'knp'
            ```
            
            - 𝛔 (city = ‘ knp ’)emp
        - projection - retrieves the required columns or attributes of the table and it uses the symbol pi (𝝿)
        - 𝝿(name , age)emp
        - in general the query are in combination of selection and projection
            - if we want to find the name and age of emp who live in knp then SQL will be
            
            ```sql
            select name , age from emp where city = 'knp'
            ```
            
        
- binary
    - those operations which require 2 operators to work with and relational algebra has following binary
        - union(U)
            - the syntax Relation1 ∪ Relation2, the result is the combination of all records from both tables without duplication
        - intersection(⋂)
            - Relation1 ∩ Relation2, result is the common record between both the table
        - difference(-)
            - Relation1 − Relation2, Finds tuples in one relation that are not present in the other relation, all records of r1 after removing record of r2
            - emp1 - emp2 ≠ emp2 - emp1
        - Cartesian product(x)
            - also known as product operation which is represented by multiplication symbol
            - every record of first table connects with every record of second table
            - the total number of record in final output is number of record in first table x number of record in second table
            - total number of attribute in output is number of attribute in first table + number of attribute in second table
        - join(⋈)
            - lets consider two table emp1 and emp2
        
        ![image.png](relational%20algebra%205366bb8b0d5f414296795e21ace6ce73/image.png)
        
        ![image.png](relational%20algebra%205366bb8b0d5f414296795e21ace6ce73/image%201.png)
        
        - we can perform first three operations union intersection difference when following conditions are present
            - no of attributes in first table must be equal to the no of attributes in second table
            - the sequence of attribute from their data type point of view must be same in both tables

### 1. **Basic Concepts**

- **Relation**: A relation is a table with rows and columns. A relation schema defines the structure of the relation, i.e., the name of the relation and its attributes (columns).
- **Tuple**: A tuple is a single row in a relation, representing a record.
- **Attribute**: An attribute is a column in a relation. Each attribute has a specific domain (data type).
- **Degree**: The number of attributes in a relation is called its degree.
- **Cardinality**: The number of tuples in a relation is called its cardinality.

---

### 2. **Fundamental Operations of Relational Algebra**

The basic operations form the foundation for building complex queries. These operations are:

- **Selection (σ)**: Used to select tuples that satisfy a given condition.
    - **Syntax**: σ<sub>condition</sub>(Relation)
    - **Example**: σ<sub>age > 30</sub>(Employee) returns all employees whose age is greater than 30.
- **Projection (π)**: Used to select specific columns (attributes) from a relation.
    - **Syntax**: π<sub>attribute1, attribute2,…</sub>(Relation)
    - **Example**: π<sub>name, age</sub>(Employee) returns only the `name` and `age` columns of the Employee relation.
- **Union (∪)**: Combines tuples from two relations, eliminating duplicates. Both relations must have the same number of attributes and corresponding data types.
    - **Syntax**: Relation1 ∪ Relation2
    - **Example**: Employee ∪ Manager returns a relation containing tuples that are in either Employee or Manager.
- **Set Difference (−)**: Finds tuples in one relation that are not present in the other relation.
    - **Syntax**: Relation1 − Relation2
    - **Example**: Employee − Manager returns tuples in Employee that are not in Manager.
- **Cartesian Product (×)**: Combines tuples from two relations to form a new relation with all possible pairs of tuples.
    - **Syntax**: Relation1 × Relation2
    - **Example**: Employee × Department combines each employee with each department.
- **Rename (ρ)**: Renames the attributes of a relation for readability or compatibility.
    - **Syntax**: ρ<sub>new_relation(new_attributes)</sub>(Relation)
    - **Example**: ρ<sub>Emp(name, salary)</sub>(Employee) renames the `Employee` relation to `Emp` with attributes `name` and `salary`.

---

### 3. **Derived Operations in Relational Algebra**

Derived operations are built using the basic operations to express more complex queries.

- **Intersection (∩)**: Returns tuples that are common to both relations.
    - **Syntax**: Relation1 ∩ Relation2
    - **Example**: Employee ∩ Manager returns tuples present in both Employee and Manager.
- **Natural Join (⋈)**: Combines tuples from two relations based on a common attribute, eliminating duplicate attributes in the result.
    - **Syntax**: Relation1 ⋈ (condition) Relation2
    - **Example**: Employee ⋈ Department combines each employee with their respective department, where the `dept_id` attribute is common in both relations.
    - represented by bow tie and the joining condition is mentioned in the subscript of operation
    - it gives the result only for the matching records as per the joining condition
    - lets consider two tables emp and dept with primary key eid and did , primary key of dept (did) is working as foreign key in emp table snapshot of both tables are given below
    - for joining these two tables are
    
    | eid | name | city | did |
    | --- | --- | --- | --- |
    |  |  |  |  |
    |  |  |  |  |
    |  |  |  |  |
    
    | eid | name | city | did | loc |
    | --- | --- | --- | --- | --- |
    |  |  |  |  |  |
    |  |  |  |  |  |
    |  |  |  |  |  |
    - 
    - emp ⋈ (eid = did) dept
    - find the name and city of emp who live in lko , find data of emp who live in lko , find the name and city of all emp
    - find the name of emp who work from building ab4
    
    ```sql
    SELECT e.name, e.city
    FROM emp e
    WHERE e.city = 'lko';
    
    ```
    
    ```sql
    SELECT *
    FROM emp e
    WHERE e.city = 'lko';
    
    ```
    
    ```sql
    SELECT e.name, e.city
    FROM emp e;
    
    ```
    
    ```sql
    SELECT e.name
    FROM emp e
    JOIN dept d ON e.did = d.did
    WHERE d.loc = 'ab4';
    /*πname(emp⋈emp.did=dept.didσloc=′ab4′(dept))*/
    ```
    
- **Theta Join (⋈<sub>θ</sub>)**: A general form of join that uses a condition (θ) to combine relations.
    - **Syntax**: Relation1 ⋈<sub>condition</sub> Relation2
    - **Example**: Employee ⋈<sub>Employee.dept_id = Department.dept_id</sub> Department joins based on a matching `dept_id`.
- **Division (÷)**: Divides one relation by another to find tuples in the first relation that are related to all tuples in the second relation.
    - **Syntax**: Relation1 ÷ Relation2
    - **Example**: Consider `A(x, y)` and `B(y)`, `A ÷ B` will return all `x` values from `A` that relate to every `y` value in `B`.

---

### 4. **Properties of Relational Algebra**

Relational Algebra has several important properties that make it useful for query optimization:

- **Commutativity**: The order of applying some operations (like selection and projection) can be interchanged.
    - Example: σ<sub>condition</sub>(π<sub>attributes</sub>(Relation)) = π<sub>attributes</sub>(σ<sub>condition</sub>(Relation))
- **Associativity**: Multiple operations can be grouped without changing the result.
    - Example: (Relation1 ⋈ Relation2) ⋈ Relation3 = Relation1 ⋈ (Relation2 ⋈ Relation3)
- **Idempotency**: Some operations (like selection) can be applied multiple times without changing the result.
    - Example: σ<sub>condition</sub>(σ<sub>condition</sub>(Relation)) = σ<sub>condition</sub>(Relation)

---

### 5. **Relational Algebra vs. SQL**

Relational Algebra provides the foundation for SQL, but the two are not exactly the same:

- **Relational Algebra** is a procedural query language, meaning you describe how to get the result.
- **SQL** is a declarative query language, meaning you describe what you want, and the DBMS decides how to get it.

For example:

- In **Relational Algebra**: you might use a sequence of selection, projection, and join operations to get the result.
- In **SQL**: you would write a `SELECT` statement with a `WHERE` clause to express the same thing.

---

### 6. **Examples of Queries Using Relational Algebra**

Let’s look at a few example queries using relational algebra:

1. **Get names of all employees who work in the HR department**:
    - **Relational Algebra**:
        - `π<sub>name</sub>(σ<sub>department = 'HR'</sub>(Employee ⋈ Department))`
2. **Find the names of employees who earn more than $50,000**:
    - **Relational Algebra**:
        - `π<sub>name</sub>(σ<sub>salary > 50000</sub>(Employee))`
3. **Get the list of all employees who do not manage anyone**:
    - **Relational Algebra**:
        - `π<sub>name</sub>(Employee) − π<sub>name</sub>(Manager)`

---

### 7. **Practical Uses of Relational Algebra**

Relational algebra is mostly theoretical but plays an important role in:

- **Query Optimization**: Modern DBMS systems use relational algebra internally to break down SQL queries into efficient execution plans.
- **Query Processing**: DBMS uses relational algebra to represent and manipulate queries during query processing.
- **Foundation for Query Languages**: It serves as the underlying basis for SQL and other relational query languages.