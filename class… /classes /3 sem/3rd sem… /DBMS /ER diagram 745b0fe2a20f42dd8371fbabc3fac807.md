# ER diagram

ER diagram is used in ER modeling it is a high-level representation of data  and relationships among data this diagram is used for conceptual designing of a database 

the symbols used in ER diagram are rectangle (entity), diamond (relation), oval (attributes), connecting lines (lines)

in ERD different types of attributes are represented using different types of representations 

working as primary key , key attribute

![image.png](ER%20diagram%20745b0fe2a20f42dd8371fbabc3fac807/image.png)

composite

![image.png](ER%20diagram%20745b0fe2a20f42dd8371fbabc3fac807/image%201.png)

types of relationship 

in ERD entities can be connected with each other in following manner 

- one to one (1:1)
- many to one (m:1)
- one to many (1:m)
- many to many (m:n)
    
    ![image.png](ER%20diagram%20745b0fe2a20f42dd8371fbabc3fac807/image%202.png)
    

### degree of relationship

it represents the number of entity types that are connected or associated with the relationship , it is of types

- unary , if only one entity is connected with the relationship
- eg - employee report to another employee
    
    [https://documents.lucid.app/documents/cee76dc4-25c6-4752-9711-484e7c50ee4e/pages/0_0?a=2014&x=305&y=-655&w=522&h=326&store=1&accept=image%2F*&auth=LCA%203d2b176ac513f9aef8c3d38f3762e5dcd9468e5ad6b7bbbd38b3af7aa5a9c7d4-ts%3D1725509058](https://documents.lucid.app/documents/cee76dc4-25c6-4752-9711-484e7c50ee4e/pages/0_0?a=2014&x=305&y=-655&w=522&h=326&store=1&accept=image%2F*&auth=LCA%203d2b176ac513f9aef8c3d38f3762e5dcd9468e5ad6b7bbbd38b3af7aa5a9c7d4-ts%3D1725509058)
    
- binary , if 2 entity are connected with relationship symbol
- eg - student taught by faculty

[https://documents.lucid.app/documents/cee76dc4-25c6-4752-9711-484e7c50ee4e/pages/0_0?a=2017&x=319&y=-661&w=756&h=232&store=1&accept=image%2F*&auth=LCA%205f20777deca9397e7ce2432a44503f9254d4bb89d68d41ec86ca9cc62fc566f9-ts%3D1725509058](https://documents.lucid.app/documents/cee76dc4-25c6-4752-9711-484e7c50ee4e/pages/0_0?a=2017&x=319&y=-661&w=756&h=232&store=1&accept=image%2F*&auth=LCA%205f20777deca9397e7ce2432a44503f9254d4bb89d68d41ec86ca9cc62fc566f9-ts%3D1725509058)

- ternary ,  if 3 entity are connected with relationship symbol
- eg - doctor writes prescription , doctor checks patient / student faculty course manages

[https://documents.lucid.app/documents/cee76dc4-25c6-4752-9711-484e7c50ee4e/pages/0_0?a=2028&x=319&y=-672&w=756&h=465&store=1&accept=image%2F*&auth=LCA%2090d0570295af2e9a52d694d14130c54a6a3400b631d5bc1da935cd5e83460806-ts%3D1725509058](https://documents.lucid.app/documents/cee76dc4-25c6-4752-9711-484e7c50ee4e/pages/0_0?a=2028&x=319&y=-672&w=756&h=465&store=1&accept=image%2F*&auth=LCA%2090d0570295af2e9a52d694d14130c54a6a3400b631d5bc1da935cd5e83460806-ts%3D1725509058)

- nary , if more than 3 entity are connected with relationship symbol
- eg- project employee department client

### strong and weak entity

![image.png](ER%20diagram%20745b0fe2a20f42dd8371fbabc3fac807/image%203.png)

### 1. **Strong Entity**

- **Definition**: A strong entity, also known as an independent entity, is an entity that can exist on its own in the database. It does not rely on any other entity for its existence, and it has its own primary key that uniquely identifies each instance of the entity.

[https://documents.lucid.app/documents/cee76dc4-25c6-4752-9711-484e7c50ee4e/pages/0_0?a=2062&x=434&y=-621&w=892&h=248&store=1&accept=image%2F*&auth=LCA%20fa76edd201b610b52fe5ae18230f7c3ac51a0b5719b8c2ed8b49ced361d120ba-ts%3D1725942174](https://documents.lucid.app/documents/cee76dc4-25c6-4752-9711-484e7c50ee4e/pages/0_0?a=2062&x=434&y=-621&w=892&h=248&store=1&accept=image%2F*&auth=LCA%20fa76edd201b610b52fe5ae18230f7c3ac51a0b5719b8c2ed8b49ced361d120ba-ts%3D1725942174)

- **Characteristics**:
    - **Independent Existence**: It does not need any other entity to define its existence.
    - **Primary Key**: It has a primary key that is unique to each entity instance and does not depend on any other entity.
    - **Examples**: Common strong entities include `Customer`, `Employee`, `Product`, etc.
- **Example**:
    - **Customer**: In a retail system, a "Customer" is a strong entity. It has its own unique identifier, such as `Customer_ID`, which distinguishes each customer.
    - **ERD Representation**:
        - The entity is represented by a rectangle, and the primary key attribute is underlined.

### 2. **Weak Entity**

- **Definition**: A weak entity is an entity that cannot exist independently and relies on a strong entity for its existence. It does not have a primary key of its own and instead uses a partial key (also known as a discriminator) combined with a foreign key from the strong entity to create a composite key.
- **Characteristics**:
    - **Dependent Existence**: It cannot exist without being associated with a strong entity.
    - **Partial Key**: A weak entity has a partial key that only uniquely identifies instances of the weak entity when combined with the key of the strong entity.
    - **Foreign Key Relationship**: It always has a foreign key that links it to the strong entity.
    - **Examples**: Common weak entities include `Order_Item`, `Dependent`, etc.
- **Example**:
    - **Order_Item**: In an order management system, "Order" might be a strong entity, and "Order_Item" could be a weak entity. "Order_Item" relies on "Order" for its existence, as it cannot exist without an associated order.
    - **ERD Representation**:
        - The weak entity is represented by a rectangle with a double border.
        - The relationship between the strong and weak entity is represented by a diamond with a double border.

### 3. **Difference between Strong and Weak Entities**

- **Primary Key**:
    - **Strong Entity**: Has its own primary key that uniquely identifies each instance.
    - **Weak Entity**: Does not have its own primary key. Instead, it has a partial key that, combined with the foreign key from the strong entity, creates a composite key.
- **Existence**:
    - **Strong Entity**: Exists independently and does not depend on any other entity.
    - **Weak Entity**: Depends on a strong entity for its existence.
- **ERD Notation**:
    - **Strong Entity**: Represented by a single rectangle.
    - **Weak Entity**: Represented by a double rectangle, and its identifying relationship is represented by a double diamond.