# data models and its types

## Data Models

A data model is an abstract representation of a database. It defines the structure and organization of data, relationships between data elements, and constraints that maintain data integrity.

data models are the concept to summarize the description of database it provide us the complete and transparent picture about the data and the relationship among the data 

there are different types of data models

### Types of Data Models

1. **Hierarchical Model:**
    - Represents data as a tree-like structure with a single root node.
    - first data model to conceptually visualize the data
    - Each node can have multiple child nodes.
    - Used in older systems like IBM's IMS.
    - **Example:** File system structure.
    
    ![Untitled](data%20models%20and%20its%20types%2094aabf62ef2a45e085ed4374ee282f3a/Untitled.jpeg)
    
    ![WhatsApp Image 2024-08-06 at 10.36.34_0b22897b.jpg](data%20models%20and%20its%20types%2094aabf62ef2a45e085ed4374ee282f3a/WhatsApp_Image_2024-08-06_at_10.36.34_0b22897b.jpg)
    
2. **Network Model:**
    - A more flexible version or extension of the hierarchical model.
    - represent data as graph
    - hierarchical data model was able to show only parent child relationship
    - other types of relationship existing on pear levels cannot be shown due to this reason the network data model came into existence
    - Allows a child node to have multiple parent nodes.
    - network data model can exabit different types of relationship other than parent child relationship but we do not know the name of relationship
    - Complex to implement and manage.
        
        ![WhatsApp Image 2024-08-06 at 10.55.19_7f82007d.jpg](data%20models%20and%20its%20types%2094aabf62ef2a45e085ed4374ee282f3a/WhatsApp_Image_2024-08-06_at_10.55.19_7f82007d.jpg)
        
3. **Relational Model:**
    - Represents data as tables with rows and columns.
    - the concept of RDBMS was proposed by E.F. Codd and according to this concept we can represent the data and the relationship among data using rows and columns , name of the table / relation is written on the top left corner of the table , column names are known as attributes , rows are known as tuples or records , set of all values contained by any attribute is known as domain of that attribute , logical structure of table is schema , view of table at any moment is known as instance , total number of records present in any table is known as cardinality, total number of attributes present in any table is known as degree
    
    [https://documents.lucid.app/documents/cee76dc4-25c6-4752-9711-484e7c50ee4e/pages/0_0?a=1578&x=591&y=308&w=348&h=420&store=1&accept=image%2F*&auth=LCA%209313d00b8f3e1a8c35aaff3d32fde9fbb2a215a222c33409e1a455a5556abf44-ts%3D1723089899](https://documents.lucid.app/documents/cee76dc4-25c6-4752-9711-484e7c50ee4e/pages/0_0?a=1578&x=591&y=308&w=348&h=420&store=1&accept=image%2F*&auth=LCA%209313d00b8f3e1a8c35aaff3d32fde9fbb2a215a222c33409e1a455a5556abf44-ts%3D1723089899)
    
    - Uses primary keys and foreign keys to establish relationships between tables.
    - Most widely used model in modern databases (e.g., MySQL, Oracle, SQL Server).
    - **Example:** A database for a library with tables for books, authors, and borrowers.
4. **Object-Oriented Data Model:**
    - Combines data and operations (methods) into objects.
    - Supports complex data structures and inheritance.
    - Used in object-oriented databases.
    - **Example:** Databases for CAD/CAM applications.
5. **Entity-Relationship (ER) Model:**
    - A high-level data model that represents entities (real-world objects) and relationships between them.
    - Used as a blueprint for designing relational databases.
    - to overcome the problem of network data model ER data model came into the existence it is a conceptual data model which uses different types of symbolic representations to show the data and the relationship among the data for this purpose we use some symbols to represent following objects
        
        [https://documents.lucid.app/documents/cee76dc4-25c6-4752-9711-484e7c50ee4e/pages/0_0?a=1149&x=568&y=456&w=1336&h=430&store=1&accept=image%2F*&auth=LCA%20945748151eef608e4d554e450193d218a92e3a99492da8962784bdfec2f0fccd-ts%3D1723089899](https://documents.lucid.app/documents/cee76dc4-25c6-4752-9711-484e7c50ee4e/pages/0_0?a=1149&x=568&y=456&w=1336&h=430&store=1&accept=image%2F*&auth=LCA%20945748151eef608e4d554e450193d218a92e3a99492da8962784bdfec2f0fccd-ts%3D1723089899)
        
    - **Example:** Modeling a university database with entities like students, courses, and professors.
    - design a er diagram to relate customer and product / do er modelling for customer and product
    
    [https://documents.lucid.app/documents/cee76dc4-25c6-4752-9711-484e7c50ee4e/pages/0_0?a=1400&x=137&y=172&w=1279&h=652&store=1&accept=image%2F*&auth=LCA%205908893aabc3138059db8a0babb13ce83deb869237cf42a1dfe292211ff5d16c-ts%3D1723089899](https://documents.lucid.app/documents/cee76dc4-25c6-4752-9711-484e7c50ee4e/pages/0_0?a=1400&x=137&y=172&w=1279&h=652&store=1&accept=image%2F*&auth=LCA%205908893aabc3138059db8a0babb13ce83deb869237cf42a1dfe292211ff5d16c-ts%3D1723089899)
    
    [https://documents.lucid.app/documents/cee76dc4-25c6-4752-9711-484e7c50ee4e/pages/0_0?a=1260&x=135&y=173&w=1251&h=633&store=1&accept=image%2F*&auth=LCA%206a2f47aeb305d649a22227a43beca1e2eae6bd2bc5ec7068b0f08bb45599951f-ts%3D1723089899](https://documents.lucid.app/documents/cee76dc4-25c6-4752-9711-484e7c50ee4e/pages/0_0?a=1260&x=135&y=173&w=1251&h=633&store=1&accept=image%2F*&auth=LCA%206a2f47aeb305d649a22227a43beca1e2eae6bd2bc5ec7068b0f08bb45599951f-ts%3D1723089899)
    

### Additional Data Models

- **Dimensional Model:** Used in data warehouses for OLAP (Online Analytical Processing).
- **Document Model:** Stores data in flexible, semi-structured format (e.g., JSON, XML).
- **Graph Model:** Represents data as nodes and edges for complex relationships.

**Choosing the Right Data Model:**

The choice of data model depends on the specific requirements of the application:

- **Hierarchical:** Suitable for simple, tree-like structures.
- **Network:** For complex data relationships with multiple parents.
- **Relational:** Most common for business applications due to its flexibility and scalability.
- **Object-Oriented:** For applications requiring complex data structures and operations.
- **Dimensional:** For data warehousing and analysis.
- **Document:** For unstructured or semi-structured data.
- **Graph:** For complex networks and relationships.