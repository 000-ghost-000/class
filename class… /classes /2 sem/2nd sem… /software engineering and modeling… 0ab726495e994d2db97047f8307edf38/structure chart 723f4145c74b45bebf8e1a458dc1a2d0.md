# structure chart

### structure chart:

the aim of structure design is to transform the result of the structured analysis(DFD) into a structure chart , it represents the software architecture that is the various modules making up the system the dependency and the parameters that are passed among different modules , the symbols used are :

### Module

It represents the process or task of the system. It is of three types:

- **Control Module**: A control module branches to more than one submodule.
- **Sub Module:** Sub Module is a module which is the part (Child) of another module.
- **Library Module:** Library Module are reusable and invokable from any module.

![https://media.geeksforgeeks.org/wp-content/uploads/20190402150428/AMAN.jpeg](https://media.geeksforgeeks.org/wp-content/uploads/20190402150428/AMAN.jpeg)

### **2. Conditional Call**

It represents that control module can select any of the sub module on the basis of some condition.

![https://media.geeksforgeeks.org/wp-content/uploads/20190402151525/Aman1.jpeg](https://media.geeksforgeeks.org/wp-content/uploads/20190402151525/Aman1.jpeg)

### **3. Loop (Repetitive call of module)**

It represents the repetitive execution of module by the sub module. A curved arrow represents a loop in the module.

![https://media.geeksforgeeks.org/wp-content/uploads/20190402153748/aman2.jpeg](https://media.geeksforgeeks.org/wp-content/uploads/20190402153748/aman2.jpeg)

All the submodules cover by the loop repeat execution of module.

### **4. Data Flow**

It represents the flow of data between the modules. It is represented by a directed arrow with an empty circle at the end.

![https://media.geeksforgeeks.org/wp-content/uploads/20190402155409/aman3.jpeg](https://media.geeksforgeeks.org/wp-content/uploads/20190402155409/aman3.jpeg)

### **5. Control Flow**

![https://media.geeksforgeeks.org/wp-content/uploads/20190402155442/aman4.jpeg](https://media.geeksforgeeks.org/wp-content/uploads/20190402155442/aman4.jpeg)

It represents the flow of control between the modules. It is represented by a directed arrow with a filled circle at the end.

### 6. Physical Storage

![https://media.geeksforgeeks.org/wp-content/uploads/20190402155900/aman5.jpeg](https://media.geeksforgeeks.org/wp-content/uploads/20190402155900/aman5.jpeg)

It is that where all the information are to be stored.

# Example

**Structure chart for an Email server**

![https://media.geeksforgeeks.org/wp-content/uploads/20190402162652/email.jpeg](https://media.geeksforgeeks.org/wp-content/uploads/20190402162652/email.jpeg)

# Types of Structure Chart

1. **Transform Centered Structure:** These type of structure chart are designed for the systems that receives an input which is transformed by a sequence of operations being carried out by one module.
2. **Transaction Centered Structure:** These structure describes a system that processes a number of different types of transaction.

### what is structured chart:

- **Purpose:** They visually represent the hierarchical breakdown of a software system into its functional modules.
- **Structure:**
    - Modules are represented by boxes, containing the module's name or function.
    - Boxes are connected with arrows, indicating data flow between modules.
    - The chart follows a top-down approach, starting with the overall system function at the top and decomposing it into sub-functions (modules) at lower levels.
- **Benefits:**
    - Improve code readability and maintainability by clearly showing the relationships between modules.
    - Facilitate communication and collaboration among developers by providing a common understanding of the system's structure.
    - Aid in top-down design and structured programming by helping to break down complex problems into smaller, more manageable units.
- **Types:**
    - There are different types of structure charts used for different purposes, such as:
        - High-level structure charts: Provide a broad overview of the system's main components.
        - Detailed structure charts: Delve deeper into the functionality of individual modules.
        - Transaction structure charts: Focus on specific data flows within the system.
- **Limitations:**
    - Can become cumbersome for very large or complex systems.
    - May not capture all aspects of a system's design, such as control flow.
    
    ---