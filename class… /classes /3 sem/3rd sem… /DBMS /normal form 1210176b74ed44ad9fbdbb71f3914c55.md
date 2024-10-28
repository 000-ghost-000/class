# normal form

a table / relation is said to be in first normal form if 

- all the values in the table are atomic
- consider a table customer with data
- 

| id | name | age |
| --- | --- | --- |
| 1 | xx | 19 |
| 2 | yy | 20 |
| 3 | zz | 23 |

not in first normal form because name is non atomic 

atomic values are those values which cannot be broken further and if broken there significance is lost 

**Normalization** in Database Management Systems (DBMS) is the process of organizing data in a database to reduce redundancy and improve data integrity. It involves decomposing a database into smaller tables and establishing relationships between them according to specific rules or "normal forms" (NFs). The goal is to ensure that the data is logically stored and can be efficiently retrieved and maintained.

Here are the key **normal forms** and their significance:

### 1. **First Normal Form (1NF)**:

- **Definition**: A table is in **1NF** if:
    1. All the values in the columns are atomic, i.e., indivisible.
    2. There are no repeating groups or arrays (each record should be unique in terms of the primary key).
- **Characteristics**:
    - Each column contains only atomic values (no lists or sets).
    - Each column has a unique name.
    - Each entry in a column must be of the same data type.
    - Rows are uniquely identified by a primary key.
- **Example** (Before 1NF):
    
    
    | StudentID | Name | Subjects |
    | --- | --- | --- |
    | 1 | John | Math, Physics |
    | 2 | Alice | Chemistry, Biology |
    
    **After applying 1NF**:
    
    | StudentID | Name | Subject |
    | --- | --- | --- |
    | 1 | John | Math |
    | 1 | John | Physics |
    | 2 | Alice | Chemistry |
    | 2 | Alice | Biology |

### 2. **Second Normal Form (2NF)**:

- **Definition**: A table is in **2NF** if:
    1. It is in 1NF.
    2. All non-key attributes are **fully functionally dependent** on the primary key (i.e., no partial dependency).
- **Characteristics**:
    - Partial dependencies are removed (a non-key attribute cannot depend on just part of a composite primary key).
    - Helps eliminate redundant data across multiple records.
- **Example** (Before 2NF):
    
    
    | StudentID | CourseID | StudentName | CourseName |
    | --- | --- | --- | --- |
    | 1 | 101 | John | Math |
    | 1 | 102 | John | Physics |
    
    Here, `StudentName` depends only on `StudentID` and `CourseName` depends only on `CourseID`. This violates 2NF.
    
    **After applying 2NF** (splitting into two tables):
    
    - **Student Table**:
        
        
        | StudentID | StudentName |
        | --- | --- |
        | 1 | John |
        | 2 | Alice |
    - **Course Table**:
        
        
        | CourseID | CourseName |
        | --- | --- |
        | 101 | Math |
        | 102 | Physics |

### 3. **Third Normal Form (3NF)**:

- **Definition**: A table is in **3NF** if:
    1. It is in 2NF.
    2. It contains no **transitive dependencies** (i.e., no non-prime attribute depends on another non-prime attribute).
- **Characteristics**:
    - No transitive dependencies between non-key attributes.
    - The primary focus is to eliminate redundant data and dependencies.
- **Example** (Before 3NF):
    
    
    | StudentID | StudentName | DepartmentID | DepartmentName |
    | --- | --- | --- | --- |
    | 1 | John | 10 | Science |
    | 2 | Alice | 20 | Arts |
    
    Here, `DepartmentName` depends on `DepartmentID`, which is a transitive dependency because `DepartmentID` is not a primary key.
    
    **After applying 3NF** (splitting into two tables):
    
    - **Student Table**:
        
        
        | StudentID | StudentName | DepartmentID |
        | --- | --- | --- |
        | 1 | John | 10 |
        | 2 | Alice | 20 |
    - **Department Table**:
        
        
        | DepartmentID | DepartmentName |
        | --- | --- |
        | 10 | Science |
        | 20 | Arts |

### 4. **Boyce-Codd Normal Form (BCNF)**:

- **Definition**: A table is in **BCNF** if:
    1. It is in 3NF.
    2. For every functional dependency (A → B), A must be a superkey (meaning, no non-prime attributes can determine key attributes).
    3. no duplicate candidate key exist
- **Characteristics**:
    - BCNF is a stricter version of 3NF, where even if a non-key attribute can uniquely determine other attributes, the table is not in BCNF.
    
    ![image.png](normal%20form%201210176b74ed44ad9fbdbb71f3914c55/image.png)
    
- consider a table employee , according to functional dependency of this table the candidate of this table is emp_id , emp_dept they alone cannot work as a key
- we have to decompose this table as emp and dept and they are mapping also

![image.png](normal%20form%201210176b74ed44ad9fbdbb71f3914c55/image%201.png)

| emp id | emp dept no |
| --- | --- |
|  |  |
|  |  |
|  |  |
- after decomposing the table in 3 table , they are in bcnf
- **Example** (Before BCNF):
    
    
    | ProfessorID | Subject | Department |
    | --- | --- | --- |
    | 1 | Math | Science |
    | 1 | Physics | Science |
    
    In this case, `ProfessorID` and `Subject` form the primary key, but `Department` can be determined by `Subject`, violating BCNF.
    
    **After applying BCNF**:
    
    - **Subject Table**:
        
        
        | Subject | Department |
        | --- | --- |
        | Math | Science |
        | Physics | Science |
    - **Professor Table**:
        
        
        | ProfessorID | Subject |
        | --- | --- |
        | 1 | Math |
        | 1 | Physics |

### 5. **Fourth Normal Form (4NF)**:

- **Definition**: A table is in **4NF** if:
    1. It is in BCNF.
    2. It has no **multi-valued dependencies** (i.e., a single attribute should not have multiple independent relationships with another set of attributes).
- **Characteristics**:
    - Useful when handling complex relationships where a single attribute might be associated with multiple values independently.
    
    ![image.png](normal%20form%201210176b74ed44ad9fbdbb71f3914c55/image%202.png)
    
    - sid → sname
    - sname is dependent on sid
    - A →> B
    - multivalued dependency (b is multivalued dependent on A)
    - sid →> cid
    - sid →> cname
    - decompose them as student and course
    
    | sid | sname |
    | --- | --- |
    |  |  |
    |  |  |
    |  |  |
    
    | cid | cname |
    | --- | --- |
    |  |  |
    |  |  |
    |  |  |
    - 
- **Example** (Before 4NF):
    
    
    | EmployeeID | Skill | Language |
    | --- | --- | --- |
    | 1 | Java | English |
    | 1 | Python | French |
    
    Here, `Skill` and `Language` are multi-valued dependencies of `EmployeeID`.
    
    **After applying 4NF**:
    
    - **Skill Table**:
        
        
        | EmployeeID | Skill |
        | --- | --- |
        | 1 | Java |
        | 1 | Python |
    - **Language Table**:
        
        
        | EmployeeID | Language |
        | --- | --- |
        | 1 | English |
        | 1 | French |

### 6. **Fifth Normal Form (5NF)(join based NF)**:

- **Definition**: A table is in **5NF** if:
    1. It is in 4NF.
    2. It cannot be decomposed into smaller tables without losing data (i.e., no **join dependency** exists).
- **Characteristics**:
    - Primarily used when dealing with complex relationships and decompositions where tables are broken down into smaller components and rejoined without loss of data.
- **Example**: Situations in complex many-to-many relationships.
    
    ![image.png](normal%20form%201210176b74ed44ad9fbdbb71f3914c55/image%203.png)
    

lets decompose this table as (sub,class)(class , teacher)(sub , teacher)

| sub | class |
| --- | --- |
| math | 10 |
| math | 9 |
| science | 10 |

| class  | teacher |
| --- | --- |
| 10 | kartik |
| 9 | yash |
| 10 | yash |

| sub  | teacher |
| --- | --- |
| math | kartik |
| math | yash |
| science | yash |

for the check of lossless join after joining sc and ct table

| sub | class | teacher |
| --- | --- | --- |
| math | 9 | yash |
| math | 10 | kartik |
| science | 10 | yash |
| math | 10 | yash |

verifying the data of joined table using st table

### Benefits of Normalization:

- **Reduces data redundancy**: By organizing data into tables and eliminating repetition, normalization ensures that the same piece of information is stored only once.
- **Improves data integrity**: By ensuring data dependencies make sense, normalization helps maintain data accuracy.
- **Efficient database design**: Proper normalization leads to a more efficient database that can handle queries more effectively.
- **Ease of maintenance**: It’s easier to modify, delete, or insert data without unintended side effects.

### Drawbacks of Normalization:

- **Complex queries**: Too many tables might lead to complex queries with multiple joins, which can be harder to understand and optimize.
- **Performance impact**: In some cases, especially when performance is a top priority, normalization may need to be balanced with denormalization techniques to avoid too many joins or complex relationships.

These normal forms provide a structured approach to designing databases with fewer anomalies and ensure data consistency and integrity.