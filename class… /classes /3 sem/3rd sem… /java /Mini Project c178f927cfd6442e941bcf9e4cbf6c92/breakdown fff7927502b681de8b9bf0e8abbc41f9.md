# breakdown

Let's break down the steps for creating the project, writing code, and running it, including setting up a front end.

### **Step 1: Project Structure**

You will create a folder named `ZipperClothingStore` where you’ll store different classes. The project will consist of the following components:

- **DatabaseConnection.java**: For handling the connection to MySQL.
- **Product.java**: A class for Product entities.
- **Customer.java**: A class for Customer entities.
- **Order.java**: A class for Orders.
- **OrderItem.java**: A class for Order Items.
- **ProductDAO.java**: Handles product-related database operations.
- **OrderDAO.java**: Handles order-related database operations.
- **Main.java**: The main class to run the project.
- **Frontend**: We will later integrate a basic HTML/JSP frontend to make the project interactive.

### **Step 2: Setting Up the Database**

First, you need to create the MySQL database and tables.

### MySQL Queries

```sql
CREATE DATABASE zipper_clothing_store;

USE zipper_clothing_store;

CREATE TABLE Products (
    product_id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(255) NOT NULL,
    category VARCHAR(100) NOT NULL,
    price DECIMAL(10, 2) NOT NULL,
    stock_quantity INT NOT NULL
);

CREATE TABLE Customers (
    customer_id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(255) NOT NULL,
    email VARCHAR(255) UNIQUE NOT NULL,
    phone VARCHAR(15) NOT NULL
);

CREATE TABLE Orders (
    order_id INT AUTO_INCREMENT PRIMARY KEY,
    customer_id INT NOT NULL,
    order_date DATE NOT NULL,
    FOREIGN KEY (customer_id) REFERENCES Customers(customer_id)
);

CREATE TABLE Order_Items (
    order_item_id INT AUTO_INCREMENT PRIMARY KEY,
    order_id INT NOT NULL,
    product_id INT NOT NULL,
    quantity INT NOT NULL,
    price DECIMAL(10, 2) NOT NULL,
    FOREIGN KEY (order_id) REFERENCES Orders(order_id),
    FOREIGN KEY (product_id) REFERENCES Products(product_id)
);

```

### **Step 3: Write Java Code**

### **DatabaseConnection.java**

This class handles connecting to the MySQL database.

```java
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.SQLException;

public class DatabaseConnection {
    private static final String URL = "jdbc:mysql://localhost:3306/zipper_clothing_store";
    private static final String USER = "root";
    private static final String PASSWORD = "your_password";

    public static Connection getConnection() throws SQLException {
        return DriverManager.getConnection(URL, USER, PASSWORD);
    }
}

```

### **Product.java**

Represents a product.

```java
public class Product {
    private int productId;
    private String name;
    private String category;
    private double price;
    private int stockQuantity;

    public Product(String name, String category, double price, int stockQuantity) {
        this.name = name;
        this.category = category;
        this.price = price;
        this.stockQuantity = stockQuantity;
    }

    // Getters and setters
}

```

### **Customer.java**

Represents a customer.

```java
public class Customer {
    private int customerId;
    private String name;
    private String email;
    private String phone;

    public Customer(String name, String email, String phone) {
        this.name = name;
        this.email = email;
        this.phone = phone;
    }

    // Getters and setters
}

```

### **Order.java**

Represents an order.

```java
import java.sql.Date;

public class Order {
    private int orderId;
    private int customerId;
    private Date orderDate;

    public Order(int customerId, Date orderDate) {
        this.customerId = customerId;
        this.orderDate = orderDate;
    }

    // Getters and setters
}

```

### **OrderItem.java**

Represents an order item.

```java
public class OrderItem {
    private int orderItemId;
    private int orderId;
    private int productId;
    private int quantity;
    private double price;

    public OrderItem(int orderId, int productId, int quantity, double price) {
        this.orderId = orderId;
        this.productId = productId;
        this.quantity = quantity;
        this.price = price;
    }

    // Getters and setters
}

```

### **ProductDAO.java**

Handles database operations for products.

```java
import java.sql.Connection;
import java.sql.PreparedStatement;
import java.sql.ResultSet;
import java.sql.SQLException;

public class ProductDAO {
    public void addProduct(Product product) throws SQLException {
        String query = "INSERT INTO Products (name, category, price, stock_quantity) VALUES (?, ?, ?, ?)";
        try (Connection conn = DatabaseConnection.getConnection();
             PreparedStatement stmt = conn.prepareStatement(query)) {
            stmt.setString(1, product.getName());
            stmt.setString(2, product.getCategory());
            stmt.setDouble(3, product.getPrice());
            stmt.setInt(4, product.getStockQuantity());
            stmt.executeUpdate();
        }
    }

    public void updateStock(int productId, int stockQuantity) throws SQLException {
        String query = "UPDATE Products SET stock_quantity = ? WHERE product_id = ?";
        try (Connection conn = DatabaseConnection.getConnection();
             PreparedStatement stmt = conn.prepareStatement(query)) {
            stmt.setInt(1, stockQuantity);
            stmt.setInt(2, productId);
            stmt.executeUpdate();
        }
    }

    // More methods can be added for querying products
}

```

### **OrderDAO.java**

Handles order-related operations.

```java
import java.sql.Connection;
import java.sql.PreparedStatement;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Date;
import java.util.List;

public class OrderDAO {
    public void placeOrder(Order order, List<OrderItem> orderItems) throws SQLException {
        String insertOrderQuery = "INSERT INTO Orders (customer_id, order_date) VALUES (?, ?)";
        String insertOrderItemQuery = "INSERT INTO Order_Items (order_id, product_id, quantity, price) VALUES (?, ?, ?, ?)";
        String updateStockQuery = "UPDATE Products SET stock_quantity = stock_quantity - ? WHERE product_id = ?";

        try (Connection conn = DatabaseConnection.getConnection()) {
            conn.setAutoCommit(false);

            try (PreparedStatement orderStmt = conn.prepareStatement(insertOrderQuery, PreparedStatement.RETURN_GENERATED_KEYS);
                 PreparedStatement itemStmt = conn.prepareStatement(insertOrderItemQuery);
                 PreparedStatement stockStmt = conn.prepareStatement(updateStockQuery)) {

                orderStmt.setInt(1, order.getCustomerId());
                orderStmt.setDate(2, order.getOrderDate());
                orderStmt.executeUpdate();

                ResultSet rs = orderStmt.getGeneratedKeys();
                if (rs.next()) {
                    int orderId = rs.getInt(1);
                    for (OrderItem item : orderItems) {
                        itemStmt.setInt(1, orderId);
                        itemStmt.setInt(2, item.getProductId());
                        itemStmt.setInt(3, item.getQuantity());
                        itemStmt.setDouble(4, item.getPrice());
                        itemStmt.executeUpdate();

                        stockStmt.setInt(1, item.getQuantity());
                        stockStmt.setInt(2, item.getProductId());
                        stockStmt.executeUpdate();
                    }
                }
                conn.commit();
            } catch (SQLException e) {
                conn.rollback();
                throw new SQLException("Failed to place order. Transaction rolled back.");
            }
        }
    }
}

```

### **Step 4: Running the Program**

1. **Compile the Classes**:
    - Use VS Code’s Java extension or the terminal to compile the classes. In the terminal, navigate to the `ZipperClothingStore` directory and run:
    
    ```bash
    javac *.java
    
    ```
    
2. **Run the Main Class**:
    - Create a `Main.java` class to test adding products, placing orders, and fetching customer orders.
    
    ```bash
    java Main
    
    ```
    

### **Step 5: Frontend**

For the front end, we can create a basic HTML and JSP/Servlets structure for a web-based interface. I will guide you through that once the backend is functioning.

Let me know when you are ready for the frontend part, or if you need any further adjustments!