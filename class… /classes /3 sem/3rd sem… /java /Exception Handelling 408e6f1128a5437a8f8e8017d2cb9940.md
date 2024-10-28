# Exception Handelling

Exception handling is one of the most powerful mechanisms in Java to handle runtime errors and maintain normal application flow. Java uses a special object called an **exception** to signal when an error occurs. Exception handling in Java is achieved through **try**, **catch**, **finally**, **throw**, and **throws** keywords.

---

### **What is an Exception?**

An **exception** is an event that disrupts the normal flow of the program's execution. When an exception occurs, an object representing that exception is thrown.

There are two types of exceptions in Java:

1. **Checked Exceptions**: Checked at compile time. For example, `IOException`, `SQLException`.
2. **Unchecked Exceptions**: Checked at runtime (subclasses of `RuntimeException`). For example, `ArithmeticException`, `NullPointerException`.

---

### **Hierarchy of Exception Classes**

In Java, all exceptions are descendants of the `java.lang.Throwable` class. It has two subclasses:

- **Exception**: Represents conditions that a program should catch (like `IOException`, `FileNotFoundException`).
- **Error**: Represents serious problems that are not typically caught by programs (like `OutOfMemoryError`, `StackOverflowError`).

---

### **Key Keywords in Java Exception Handling**

### **1. `try` Block:**

The `try` block contains the code that might throw an exception.

```java
try {
    // Code that may throw an exception
}

```

### **2. `catch` Block:**

The `catch` block catches and handles exceptions thrown by the `try` block.

```java
try {
    // Code that may throw an exception
} catch (ExceptionType e) {
    // Code to handle the exception
}

```

### **3. `finally` Block:**

The `finally` block is always executed whether an exception is handled or not. It is often used for clean-up operations like closing files or releasing resources.

```java
try {
    // Code that may throw an exception
} catch (ExceptionType e) {
    // Handle the exception
} finally {
    // Code that will always execute
}

```

### **4. `throw` Keyword:**

The `throw` keyword is used to explicitly throw an exception.

```java
throw new ArithmeticException("Cannot divide by zero");

```

### **5. `throws` Keyword:**

The `throws` keyword is used in method signatures to declare that a method may throw exceptions.

```java
public void readFile() throws IOException {
    // Code that may throw IOException
}

```

---

### **Types of Exceptions in Java**

1. **Checked Exceptions**: Exceptions that are checked at compile time.
    - **Examples**: `IOException`, `FileNotFoundException`.
2. **Unchecked Exceptions**: Exceptions that are checked at runtime.
    - **Examples**: `ArithmeticException`, `NullPointerException`.
3. **Errors**: Serious issues that usually cannot be handled.
    - **Examples**: `OutOfMemoryError`, `StackOverflowError`.

---

### **Java Exception Handling Mechanism**

### **1. Multiple `catch` Blocks**

Java allows multiple `catch` blocks to handle different exceptions separately.

```java
try {
    // Code that may throw exceptions
} catch (IOException e) {
    System.out.println("Caught IOException");
} catch (ArithmeticException e) {
    System.out.println("Caught ArithmeticException");
} finally {
    System.out.println("Finally block executed");
}

```

### **2. Nested `try-catch` Blocks**

You can have nested `try-catch` blocks, i.e., a `try` block inside another `try` block.

```java
try {
    try {
        // Nested try block
    } catch (Exception e) {
        // Handle exception from inner try block
    }
} catch (Exception e) {
    // Handle exception from outer try block
}

```

### **3. Using `finally` Block**

The `finally` block is used for resource cleanup. It executes even if no exception occurs.

```java
try {
    // Code that may throw an exception
} catch (Exception e) {
    System.out.println("Caught Exception");
} finally {
    System.out.println("Finally block executed");
}

```

### **4. `throw` and `throws`**

- **`throw`**: Used to explicitly throw an exception. For example:
    
    ```java
    throw new ArithmeticException("Cannot divide by zero");
    
    ```
    
- **`throws`**: Used in method declarations to specify that a method may throw one or more exceptions. For example:
    
    ```java
    public void readFile() throws IOException {
        // Code
    }
    
    ```
    

---

### **Exception Propagation**

When an exception occurs in a method, it can propagate up the call stack until it is caught by a corresponding `catch` block. If the exception is not caught anywhere, it will terminate the program.

Example:

```java
class Example {
    void method1() {
        int result = 10 / 0; // This will cause ArithmeticException
    }

    void method2() {
        method1();
    }

    public static void main(String[] args) {
        Example obj = new Example();
        obj.method2(); // Exception will propagate here
    }
}

```

---

### **Custom Exceptions**

Java allows you to create your own exceptions by extending the `Exception` class.

```java
class MyException extends Exception {
    public MyException(String message) {
        super(message);
    }
}

class Test {
    public static void main(String[] args) {
        try {
            throw new MyException("Custom exception occurred");
        } catch (MyException e) {
            System.out.println(e.getMessage());
        }
    }
}

```

---

### **Best Practices in Exception Handling**

1. **Use specific exceptions**: Catch specific exceptions rather than catching generic exceptions like `Exception` or `Throwable`.
2. **Don't ignore exceptions**: Always handle exceptions in some way.
3. **Clean-up resources**: Use the `finally` block or try-with-resources to clean up resources like file handles, database connections, etc.
4. **Use custom exceptions for meaningful error messages**: Create custom exceptions to make your error handling more meaningful.

---

### **Practical Example:**

```java
import java.io.*;

class Example {
    public static void main(String[] args) {
        BufferedReader reader = null;
        try {
            reader = new BufferedReader(new FileReader("test.txt"));
            String line;
            while ((line = reader.readLine()) != null) {
                System.out.println(line);
            }
        } catch (FileNotFoundException e) {
            System.out.println("File not found: " + e.getMessage());
        } catch (IOException e) {
            System.out.println("I/O Error: " + e.getMessage());
        } finally {
            try {
                if (reader != null) reader.close();
            } catch (IOException e) {
                System.out.println("Failed to close reader: " + e.getMessage());
            }
        }
    }
}

```

---

### **Conclusion**

Exception handling in Java provides a robust framework to deal with runtime errors gracefully, ensuring the program's flow is not abruptly interrupted. Using a structured approach with `try`, `catch`, `finally`, `throw`, and `throws` helps in creating more reliable and maintainable code.

### Write a Program to handle arrayIndexOutofBoundException ()

```java
public class ArrayExceptionHandling {

    public static void main(String[] args) {
        int[] arr = {1, 2, 3, 4, 5};
        
        try {
            // Trying to access an invalid index
            System.out.println("Accessing element at index 5: " + arr[5]);
        } catch (ArrayIndexOutOfBoundsException e) {
            System.out.println("Error: Array index out of bounds! " + e.getMessage());
        }
        
        // Rest of the program
        System.out.println("Program continues after handling exception.");
    }
}
```

### User-Defined and Custom Exceptions in Java

In Java, **exceptions** are events that disrupt the normal flow of a program. Java provides built-in exceptions (e.g., `ArithmeticException`, `NullPointerException`), but sometimes you need to create your own exceptions to handle specific cases in your application. These are called **user-defined or custom exceptions**.

### 1. **Why Create Custom Exceptions?**

- To handle specific errors in a meaningful way, related to your application logic.
- It improves code readability and debugging, making it easier to understand the root cause of problems.
- Custom exceptions allow for cleaner separation of error handling and make your application more robust.

### 2. **How to Create a Custom Exception**

To create a custom exception, you need to:

1. **Extend** the `Exception` class (for checked exceptions) or `RuntimeException` class (for unchecked exceptions).
2. Add constructors and other methods if necessary.

**Example:**

```java
// Custom checked exception
public class MyCustomException extends Exception {
    // Default constructor
    public MyCustomException() {
        super();
    }

    // Constructor with a custom message
    public MyCustomException(String message) {
        super(message);
    }
}

// Custom unchecked exception
public class MyUncheckedException extends RuntimeException {
    public MyUncheckedException(String message) {
        super(message);
    }
}

```

### 3. **Checked vs. Unchecked Exceptions**

- **Checked Exceptions** (extend `Exception`): These must be either caught or declared to be thrown in the method signature. They represent recoverable conditions, like file not found or database connection issues.
    - Example: `IOException`, `SQLException`
- **Unchecked Exceptions** (extend `RuntimeException`): These can be ignored by the compiler and are not required to be caught or declared. They represent programming errors, like `NullPointerException` or `ArrayIndexOutOfBoundsException`.
    - Example: `IllegalArgumentException`, `NullPointerException`

### 4. **Throwing a Custom Exception**

To **throw** a custom exception, use the `throw` keyword.

**Example:**

```java
public class TestCustomException {
    public static void validateAge(int age) throws MyCustomException {
        if (age < 18) {
            throw new MyCustomException("Age must be 18 or above");
        }
    }

    public static void main(String[] args) {
        try {
            validateAge(15);  // This will throw MyCustomException
        } catch (MyCustomException e) {
            System.out.println("Caught exception: " + e.getMessage());
        }
    }
}

```

### 5. **Catching a Custom Exception**

Custom exceptions are handled just like any other exception using `try-catch` blocks.

**Example:**

```java
try {
    // Some code that may throw a custom exception
    validateAge(15);
} catch (MyCustomException e) {
    // Handle custom exception
    System.out.println("Exception caught: " + e.getMessage());
}

```

### 6. **Best Practices**

- Custom exceptions should only be used for meaningful, domain-specific error handling.
- Always provide detailed, helpful messages in custom exceptions.
- For simple cases, consider whether an existing Java exception class can be reused rather than creating a custom one.
- Custom exceptions should follow naming conventions, ending with `Exception` (e.g., `UserNotFoundException`, `InvalidInputException`).

### 7. **When to Use Custom Exceptions**

- When an application encounters a situation that cannot be represented by standard Java exceptions.
- For example, in a banking application, you may want to throw a `InsufficientFundsException` when the balance is insufficient for a withdrawal.

### 8. **Custom Exceptions in Real Projects**

In large applications like your ClothingShopApp project, you might create exceptions like:

- `ProductNotFoundException`
- `InvalidOrderException`
- `CustomerNotEligibleException`

### 9. **Chained Exceptions**

Java allows **chaining exceptions** so that one exception can wrap another. This can be useful for custom exceptions to preserve the original stack trace.

**Example:**

```java
try {
    // Some operation that might throw an exception
} catch (Exception e) {
    throw new MyCustomException("An error occurred", e);
}

```

In this way, custom exceptions can add context to the original exception.

---

### differentiate between check and uncheck exceptions

### give a list of built-in exceptions

### WAP to handle negative array size exception

### WAP to create multiple catch blocks explain following call stack trace , get message method , print stack trace , also create finally block

### WAP create user define exception throw user define exception on the basis of some condition