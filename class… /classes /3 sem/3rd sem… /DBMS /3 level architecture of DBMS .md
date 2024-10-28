# 3 level architecture of DBMS

## Three-Level Architecture in DBMS

The three-level architecture in DBMS, also known as the ANSI/SPARC architecture, is a framework that separates the user's view of data from the physical storage of data. This separation provides several advantages, including data independence, security, and flexibility.

### The Three Levels

1. **External Level (View Level):**
    - Defines the part of the database that a particular user is concerned with.
    - consist of external schema or view schema which describes followings
        - creating different groups for different types of data visualization
        - providing different types of data visualization authorities
    - Involves creating different views for different user groups (e.g., managers, clerks, customers).
    - Provides a customized view of the database for each user.
    - Also known as the user view or subschema.
2. **Conceptual Level (Logical Level):**
    - Represents the overall logical structure of the database.
    - consist of conceptual schema which describes following
        - how data is stored in database (tables)
        - what relationship exist among the data
    - programmers and database administrators (DBA) work at this level using some specific DBMS software's / SQL
    - Describes the entities, attributes, and relationships within the database.
    - Hides the physical storage details from the users.
    - Also known as the schema.
3. **Internal Level (Physical Level):**
    - Defines how data is actually stored on the physical storage devices.
    - The internal level is the lowest level of the architecture, which deals with the physical storage of data on storage devices. It describes how the data is actually stored in the database.
        
        It consists of Internal Schema which describes the following.
        
        - Physical Data Model
        - Physical Storage Structure
        - Low level data structure in detail.
    - ex → storing the data such as queue, stack , linked list , B-trees , hashing
    - Deals with file organizations, indexing techniques, access methods, and storage structures.
    - Describes the low-level implementation details of the database.

![Untitled](3%20level%20architecture%20of%20DBMS%205428fae3d3c8459298d3476e92bf01e3/Untitled.jpeg)

the objective is to enable multiple users to access the same data with personalized experience

### Advantages of Three-Level Architecture

- **Data Independence:** Changes at one level do not affect other levels.
- **Security:** Different views can be provided to different users, protecting sensitive data.
- **Flexibility:** The database can be easily modified without affecting the user's view.
- **Efficiency:** Optimization can be performed at the physical level without affecting the logical or external levels.

![Untitled](3%20level%20architecture%20of%20DBMS%205428fae3d3c8459298d3476e92bf01e3/Untitled%201.jpeg)

according to the concept of data independence if we perform any changes on any level and due to those changes its next higher level is unaffected then this concept is termed as data independence , physical data independence and logical data independence

if we do any sort of changes such as change in low level data model or change inn data structure and due to that its next higher level that is logical level is unaffected then it is termed as physical data independence