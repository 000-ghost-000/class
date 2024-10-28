# coupling & cohesion

## coupling:

the measure of interdependency between the modules 

the module should be highly cohesive and least coupled

### Types of coupling:

the listed types are from low to high coupling 

**Data Coupling:**

- Modules interact by exchanging data, but the data itself is not tightly coupled.
- two modules are data coupled if they communicate through a parameter
- e.g. - char , int
- This is considered a **good** type of coupling as it allows modules to communicate without excessive dependence.
- Example: Passing specific data elements needed for a function as arguments.

**2. Stamp Coupling:**

- Entire data structures are passed between modules, potentially including irrelevant information.
- This is considered a **bad** type of coupling as it increases the dependency between modules and makes changes more complex.
- Example: Passing an entire object containing various fields, even if only a few are needed.
- two modules are stamp coupled if they communicate using a composite data item such as aa record or a data structure

**3. Control Coupling:**

- One module controls the flow of execution in another, leading to tight dependence.
- This is considered a **bad** type of coupling as it reduces modularity and makes changes in one module potentially impact others.
- Example: Using conditional statements that depend on the state of another module.
- two modules are control coupled if data from one module is used to direct the order of instruction execution in another

**4. Common Coupling:**

- Modules share global data or resources, increasing their interdependence.
- This is considered a **bad** type of coupling as it makes the code difficult to understand, maintain, and test.
- Example: Using global variables that can be accessed and modified by any part of the program.
- two modules are common coupled if they share data through some global data items

**5. Content Coupling:**

- The code of one module directly references the code of another module.
- This is considered a **bad** type of coupling as it creates a strong dependency and makes changes in one module potentially break the other.
- Example: Directly modifying variables or calling internal functions within another module.
- exist between two modules if they share code

**6. External Coupling:**

- Modules rely on external entities like libraries, frameworks, or hardware for their functionality.
- While not inherently bad, it's important to manage external dependencies carefully to avoid issues like compatibility problems or version conflicts.

### Cohesion:

measure of functional strength of module , a cohesive module perform a single task or function , 

### Types:(low to high)

- coincidental
    - if a module contains random collection of functions , the functions are stored out of pure coincidence without thought or design
- logical
    - if all elements of the module perform similar operations
- temporal
    - when a module contains functions that must be executed in the same timespan
    ex- initialization, startup, shutdown etc.
- procedural
    - if set of functions of module is part of procedure(Algo.) in which a certain sequence of steps have to be carried out for achieving an objective
- communicational
    - if all functions of module refer to or update the same data structure
- sequential
    - output of one function taken as input for another function
- functional
    - different element of module cooperate to achieve a single function