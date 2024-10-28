# Keys in DBMS

In a Database Management System (DBMS), keys play a crucial role in defining the relationships between tables, ensuring data integrity, and optimizing data retrieval. Keys are attributes or sets of attributes that can uniquely identify a tuple (row) in a table. Below are the different types of keys in DBMS:

uniquely identify record and stablish relationship with another table , keys can be formed by 2 ways single attribute key (formed by using one attribute of table)
composite key : if the key is formed with the composition multiple attributes of table

- e_id is the single attributed key

| e_id | e_name | e_city | e_age |
| --- | --- | --- | --- |
| 1 | x | lko | 21 |
| 2 | y | lko | 32 |
| 3 | x | banglore | 21 |
- here if we create a key while combine the attributes (  institute +course_code+ year_reg+ roll ) then it frames a composite primary key
    - key of first record A73482022061 where name is abhishek and roll is 061

| roll | name | course_code | year_reg | institute | age | mobile | city |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 061 | abhishek | 48 | 2022 | A73 | 18 | 1234567890 | lko |
| 157 | anshika | 48 | 2023 | A73 | 17 | 0987654321 | lko |
| 061 | x | 49 | 2023 | A73 | 21 | 9555561026 | delhi |

### 1. **Primary Key**

- **Definition:** A primary key is a unique identifier for a record in a table. It ensures that no duplicate records exist and that every entry is unique.
- attribute or set of attribute to uniquely identify a record or row or tuple
- we choose 1 primary key from existing candidate key set according to our need , primary key can be implemented using SQL

| enroll | name | age | mob | aadhar | pan |
| --- | --- | --- | --- | --- | --- |
|  |  |  |  |  |  |
|  |  |  |  |  |  |
|  |  |  |  |  |  |
- pk = enroll
- after choosing primary key the remaining keys of candidate key are termed as alternate key
- **Characteristics:**
    - Uniqueness: No two rows can have the same primary key value.
    - Non-null: A primary key column cannot contain null values.
    - Single or Composite: A primary key can consist of a single column (simple key) or multiple columns (composite key).
- **Example:**
    - In a table `Student`, the `StudentID` could be the primary key because each student has a unique ID.

### 2. **Candidate Key**

- **Definition:** A candidate key is a set of attributes that can uniquely identify a row in a table. A table can have multiple candidate keys, but one of them is chosen as the primary key.

| enroll | name | age | mob | aadhar | pan |
| --- | --- | --- | --- | --- | --- |
|  |  |  |  |  |  |
|  |  |  |  |  |  |
|  |  |  |  |  |  |
- minimal of super key , if we fix any attribute as candidate key i.e. they have capability to work as a primary key
- in table employee minimal of super key is candidate key
- ck = {enroll , mob , aadhar , pan}
- **Characteristics:**
    - Unique: Each candidate key must uniquely identify records.
    - Non-null: Candidate keys cannot have null values.
    - Minimal: A candidate key is a minimal super key, meaning no subset of its attributes can uniquely identify a record.
- **Example:**
    - In a `Student` table, both `StudentID` and `Email` could be candidate keys as both can uniquely identify a student.

### 3. **Super Key**

- **Definition:** A super key is a set of one or more attributes that, together, can uniquely identify a record in a table. A super key is a superset of a candidate key.
- lets consider table student

| enroll | name | age | mob | aadhar | pan |
| --- | --- | --- | --- | --- | --- |
|  |  |  |  |  |  |
|  |  |  |  |  |  |
|  |  |  |  |  |  |
- key which uniquely identify record/ tuple , super key is a superset of all keys
- here keys can be enroll , mob , Aadhar , pan moreover combination of key and non key can also work as a key
- sk = {(enroll + name)(mob + name)(Aadhar + age)…}
- **Characteristics:**
    - A super key can have additional attributes that are not necessary for unique identification.
    - All candidate keys are super keys, but not all super keys are candidate keys.
- **Example:**
    - In a `Student` table, the combination of `StudentID` and `Email` is a super key. However, since `StudentID` alone can uniquely identify a student, the additional `Email` attribute is redundant.

### 4. **Alternate Key**

- **Definition:** An alternate key is any candidate key that is not chosen as the primary key.
- after choosing primary key the remaining keys of candidate key are termed as alternate key

| enroll | name | age | mob | aadhar | pan |
| --- | --- | --- | --- | --- | --- |
|  |  |  |  |  |  |
|  |  |  |  |  |  |
|  |  |  |  |  |  |
- ak = {mob , aadhar , pan}
- always have one key less than candidate key
- **Characteristics:**
    - Like candidate keys, alternate keys are unique and non-null.
    - They act as a backup for the primary key.
- **Example:**
    - If `StudentID` is chosen as the primary key, then `Email` would be an alternate key.

### 5. **Foreign Key**

- **Definition:** A foreign key is an attribute or set of attributes in one table that refers to the primary key in another table. It creates a relationship between the two tables.
- fk also known as reference key and it is used to connect two tables this key can be implemented using SQL lets consider 2 tables department and student
- DID primary key of dept table , dept table becomes the parent table

[https://documents.lucid.app/documents/cee76dc4-25c6-4752-9711-484e7c50ee4e/pages/0_0?a=1771&x=326&y=130&w=765&h=675&store=1&accept=image%2F*&auth=LCA%20b6b7271a30b28e2426fb5e55634c01dbe8337238f0325d8711d5e6a8b4e7574a-ts%3D1724903488](https://documents.lucid.app/documents/cee76dc4-25c6-4752-9711-484e7c50ee4e/pages/0_0?a=1771&x=326&y=130&w=765&h=675&store=1&accept=image%2F*&auth=LCA%20b6b7271a30b28e2426fb5e55634c01dbe8337238f0325d8711d5e6a8b4e7574a-ts%3D1724903488)

- sid is primary key of student table by using these table we are now able to know which student is studying in which dept

[https://documents.lucid.app/documents/cee76dc4-25c6-4752-9711-484e7c50ee4e/pages/0_0?a=1834&x=326&y=130&w=765&h=675&store=1&accept=image%2F*&auth=LCA%209e5dec1b00f43082a9c06f27ce778ccf703e7f7d94c53c140f5c52004ded8795-ts%3D1724903488](https://documents.lucid.app/documents/cee76dc4-25c6-4752-9711-484e7c50ee4e/pages/0_0?a=1834&x=326&y=130&w=765&h=675&store=1&accept=image%2F*&auth=LCA%209e5dec1b00f43082a9c06f27ce778ccf703e7f7d94c53c140f5c52004ded8795-ts%3D1724903488)

[https://documents.lucid.app/documents/cee76dc4-25c6-4752-9711-484e7c50ee4e/pages/0_0?a=1910&x=317&y=130&w=961&h=675&store=1&accept=image%2F*&auth=LCA%20b9bb5ae2aa4ab65f754bd1c62d8e1080d2e7d6298713f56d962ecd010e1be528-ts%3D1724903488](https://documents.lucid.app/documents/cee76dc4-25c6-4752-9711-484e7c50ee4e/pages/0_0?a=1910&x=317&y=130&w=961&h=675&store=1&accept=image%2F*&auth=LCA%20b9bb5ae2aa4ab65f754bd1c62d8e1080d2e7d6298713f56d962ecd010e1be528-ts%3D1724903488)

```sql
create table dept
(
did int primary key,
dname varchar2(20),
dloc varchar2(5)
);
```

```sql
create table student
(
sid varchar2(5) primary key,
sname varchar2(30),
smob numeric(10),
did int references dept(did)
);
```

- **Characteristics:**
    - A foreign key can have duplicate values.
    - It can contain null values, except when it's part of a composite key.
    - The foreign key establishes a referential link between two tables, ensuring data consistency.
- **Example:**
    - In a `Course` table, `StudentID` could be a foreign key that references the `StudentID` in the `Student` table. This ensures that every course is associated with a valid student.

### 6. **Composite Key**

- **Definition:** A composite key is a key that consists of two or more columns that, together, uniquely identify a row in a table.
- **Characteristics:**
    - Individually, the columns in a composite key do not guarantee uniqueness, but when combined, they do.
    - Composite keys are often used in junction tables for many-to-many relationships.
- **Example:**
    - In a `StudentCourse` table, the combination of `StudentID` and `CourseID` could form a composite key, as each student may enroll in multiple courses, and each course may have multiple students.

### 7. **Unique Key**

- **Definition:** A unique key is similar to a primary key in that it ensures uniqueness of records, but unlike a primary key, a unique key can contain null values (but only one null).
- **Characteristics:**
    - Uniqueness: Ensures that no two records can have the same value in the unique key column.
    - Can be null: Allows null values but only one null value is allowed.
    - Used to enforce uniqueness in columns that are not part of the primary key.
- **Example:**
    - In a `User` table, `Email` might be a unique key to ensure that no two users can have the same email address.

### 8. **Surrogate Key**

- **Definition:** A surrogate key is an artificially generated key, often an auto-incrementing number, that serves as a unique identifier for a record in a table. It has no business meaning and is used purely for identification purposes.
- **Characteristics:**
    - Automatically generated by the database.
    - No business logic or meaning associated with the surrogate key.
    - Typically used when no suitable natural primary key is available.
- **Example:**
    - In a `Customer` table, a column `CustomerID` might be a surrogate key, generated automatically by the database system.

### Importance of Keys in DBMS

1. **Ensuring Data Integrity:**
    - Keys help maintain the uniqueness of records in a table, ensuring data integrity and consistency.
2. **Establishing Relationships:**
    - Foreign keys are essential for establishing relationships between tables, enabling the creation of a relational database structure.
3. **Optimizing Data Retrieval:**
    - Keys, especially primary keys, are often indexed by the database, which speeds up data retrieval operations.
4. **Avoiding Redundancy:**
    - Proper use of keys helps avoid data redundancy by ensuring that each piece of data is stored in only one place.
5. **Enforcing Business Rules:**
    - Keys help enforce business rules, such as uniqueness constraints, which ensure that no duplicate records are created.

### Summary of Key Concepts

for smoothly handling data we have different types of keys

- **Primary Key:** Uniquely identifies each record in a table; cannot be null.
- **Candidate Key:** Potential keys that can uniquely identify records; one is chosen as the primary key.
- **Super Key:** A set of attributes that can uniquely identify records; includes candidate keys.
- **Alternate Key:** Candidate keys that are not chosen as the primary key.
- **Foreign Key:** Links one table to another, establishing relationships between them.
- **Composite Key:** A key made up of multiple columns that together uniquely identify a record.
- **Unique Key:** Ensures uniqueness of records but can allow one null value.
- **Surrogate Key:** An artificial key with no business meaning, used purely for identification.

### Best Practices

- **Choose Primary Keys Wisely:** Ensure that the primary key is stable and unlikely to change over time.
- **Use Foreign Keys to Maintain Relationships:** Always use foreign keys to maintain referential integrity between related tables.
- **Avoid Using Business Logic in Keys:** Business logic can change over time, making surrogate keys a safer choice for primary keys.
- **Ensure Uniqueness with Unique Keys:** Use unique keys to prevent duplicates in columns that are not part of the primary key.

Understanding and implementing the appropriate keys in a DBMS is fundamental for maintaining a well-structured, efficient, and reliable database.

### sequence of keys:

1. super key - uniquely identify key
2. candidate key - uniquely identify key
3. primary key - uniquely identify key
4. alternate key- uniquely identify key
5. foreign key- relationship between 2 or more tables