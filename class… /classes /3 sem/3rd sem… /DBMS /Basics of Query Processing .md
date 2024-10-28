# Basics of Query Processing

query processing is the process of expression high level query into the low level to get the final output

- parsing/translation
    - syntax check
    - semantic check
    - shared pool check
    - SQL to relational algebra (RA) translation
- optimization
    - optimizing the query from space and time complexity POV, the optimizer is the component responsible for it
- raw source generation
    - this step chooses the best execution plan and converse it into low-level expressions
- 

---

### **Basics of Query Processing**

1. **Definition:**
    - Query processing involves transforming a high-level declarative query, typically written in a language such as SQL, into a form that can be executed efficiently at the physical level of the database. It includes several stages such as translation, optimization, and execution to retrieve the requested data. The process ensures that the query is not only syntactically and semantically correct but is also executed in the most efficient way possible.
2. **Basic Steps in Query Processing:**
    - The process of query processing generally consists of three main steps:
        1. **Parsing and Translation:**
            - The first stage, where the high-level query (written in SQL) is parsed to ensure that it is syntactically and semantically correct. The query is then translated into an internal representation, typically in the form of a relational algebra expression, which can be used for further processing.
        2. **Optimization:**
            - In this step, various strategies or execution plans are considered to find the most efficient way to execute the query. It involves evaluating different methods for accessing data (such as index scans or full table scans) and estimating their costs in terms of I/O, CPU usage, and memory consumption.
        3. **Evaluation:**
            - The final step involves executing the query according to the chosen execution plan. The database engine retrieves the data based on the plan and processes it to produce the final results.
3. **Block and Detailed Diagrams of Query Processing:**
    - The block diagram illustrates the major stages of query processing: Parsing, Optimization, and Evaluation.
    - The detailed diagram delves deeper into the individual components and activities within each stage, such as parsing steps (syntax, semantic, shared pool checks), optimization processes (plan selection), and evaluation (execution engine operations).
4. **Step-1: Parser**
    - The parser is responsible for verifying the structure and meaning of the query:
        - **Syntax Check:**
            - Ensures that the SQL statement adheres to the language’s grammatical rules. For instance, detecting mistakes such as "SELECT * FORM employee" instead of "SELECT * FROM employee."
        - **Semantic Check:**
            - Evaluates the logical correctness of the query. It checks whether the referenced tables, columns, or database objects exist and whether the operations are meaningful. For example, if a table mentioned in the query does not exist, the semantic check will identify this issue.
        - **Shared Pool Check:**
            - Each query generates a unique hash code during execution. This check determines whether the hash code for the current query already exists in the shared pool:
                - **Soft Parse:** If the hash code exists, the database skips additional parsing and optimization steps, directly proceeding to execution.
                - **Hard Parse:** If the hash code does not exist, the query must undergo full parsing, optimization, and execution planning.
5. **Step-2: Optimizer**
    - The optimizer is a critical component that decides the best strategy to execute a query. It considers different execution plans and chooses the one with the lowest estimated cost. Key aspects of query optimization include:
        - **Query Plan Evaluation:**
            - The optimizer generates multiple potential plans for executing a query, each with a different sequence of operations such as joins, selections, or projections.
        - **Cost Estimation:**
            - The optimizer estimates the cost of each plan based on factors like disk I/O, CPU cycles, and memory usage.
        - **Plan Selection:**
            - The plan with the lowest estimated cost is chosen for execution. The optimizer may utilize various techniques, such as heuristic-based approaches (rule-based optimization) or cost-based approaches (evaluating the cost of different plans).
6. **Aim of Query Optimization:**
    - The primary goals of query optimization include:
        - **Minimization of Response Time:**
            - Reducing the time taken to produce results from the user’s query.
        - **Maximization of System Throughput:**
            - Enhancing the number of queries processed by the system within a given time frame.
        - **Reduction of Memory and Storage Requirements:**
            - Efficiently managing resources to reduce the data’s footprint in memory and on disk.
        - **Increased Parallelism:**
            - Leveraging multiple processors and cores to execute different parts of the query simultaneously for faster performance.
7. **Step-3: Execution Engine**
    - The execution engine is responsible for carrying out the chosen query-evaluation plan. It interacts with the storage system to access data, performs necessary operations (e.g., filtering, sorting, joining), and generates the result set. The main tasks include:
        - **Accessing Data:**
            - The execution engine retrieves data from the database storage according to the plan, using methods like index scans, full table scans, or fetching data from memory.
        - **Processing Operations:**
            - It executes operations like joins, aggregations, and filtering as defined in the execution plan.
        - **Returning Results:**
            - After processing, the execution engine returns the final results to the user or application.

[ADBMS 11. Q-II Basics of Query Processing.ppt](Basics%20of%20Query%20Processing%201297927502b680f99fc9d512916585c1/ADBMS_11._Q-II_Basics_of_Query_Processing.ppt)