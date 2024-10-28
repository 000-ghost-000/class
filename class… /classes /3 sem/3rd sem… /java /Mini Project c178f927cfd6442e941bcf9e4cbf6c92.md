# Mini Project

SELF WORK							Submission Date :08 Oct.’2024
Q1. Explain following :
1.⁠ ⁠Static members and methods
2.⁠ ⁠Finalize()
3.⁠ ⁠Accessors and Mutator Methods
4.⁠ ⁠Cloning Objects(Shallow and deep cloning)
5.⁠ ⁠Generic class
Q2. Discuss recent trends and developments in Java
Q3. Explain the concept of JDBC. Also explain JDBC drivers.
Q4. Mini Project
Online Clothing Store Database

Develop a Java application for an online clothing store aligned with the “Viksit Bharat@2047” vision, which emphasizes innovation, inclusivity, and efficient technology solutions. The database schema is designed to manage products, customers, and orders while ensuring data security, scalability, and sustainability.

Database Schema:
1.⁠ ⁠Products
o	product_id (INT, Primary Key, Auto Increment)
o	name (VARCHAR(255), Not Null)
o	category (VARCHAR(100), Not Null)
o	price (DECIMAL(10, 2), Not Null)
o	stock_quantity (INT, Not Null)

2.⁠ ⁠Customers

o	customer_id (INT, Primary Key, Auto Increment)
o	name (VARCHAR(255), Not Null)
o	email (VARCHAR(255), Unique, Not Null)
o	phone (VARCHAR(15), Not Null)

3.⁠ ⁠Orders
o	order_id (INT, Primary Key, Auto Increment)
o	customer_id (INT, Foreign Key referencing Customers, Not Null)
o	order_date (DATE, Not Null)

4.⁠ ⁠Order_Items
o	order_item_id (INT, Primary Key, Auto Increment)
o	order_id (INT, Foreign Key referencing Orders, Not Null)
o	product_id (INT, Foreign Key referencing Products, Not Null)
o	quantity (INT, Not Null)
o	price (DECIMAL(10, 2), Not Null)

Objective:
Design a JDBC-based Java application that reflects the “Viksit Bharat@2047” principles by implementing the following functionalities with a focus on modern practices such as security, efficiency, and user-centric design:

1.⁠ ⁠Add a New Product: Implement a method to insert a new product into the Products table. Ensure input validation and exception handling to maintain data integrity.
2.⁠ ⁠Update Product Stock: Implement a method to update the stock quantity of a product. The method should validate input parameters and handle scenarios where the product might not exist.
3.⁠ ⁠Place an Order: Implement a method to process a new order which includes:
o	Adding a record to the Orders table.
o	Adding multiple records to the Order_Items table.
o	Automatically updating the stock quantity of each product ordered.
o	Ensuring transactional integrity to handle scenarios where errors might occur during the process.
4.⁠ ⁠Fetch Customer Orders: Implement a method to retrieve and display all orders for a specific customer, including:
o	Order details such as order date and items.
o	Efficient querying to handle large datasets and maintain performance.
5.⁠ ⁠Implement Exception Handling: Use robust exception handling to manage SQL and other potential exceptions. Ensure proper resource management (closing connections, statements, and result sets) to avoid leaks and maintain application stability.

[breakdown](Mini%20Project%20c178f927cfd6442e941bcf9e4cbf6c92/breakdown%20fff7927502b681de8b9bf0e8abbc41f9.md)

[Run&Compile](Mini%20Project%20c178f927cfd6442e941bcf9e4cbf6c92/Run&Compile%20fff7927502b6810bb846df5338f54d45.md)