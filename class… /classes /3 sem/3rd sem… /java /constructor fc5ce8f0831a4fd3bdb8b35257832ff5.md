# constructor

**1. Definition:**

- A constructor in Java is a special method used to initialize objects.
- It is called when an object of a class is created.

**2. Characteristics:**

- **Name:** The constructor's name must be the same as the class name.
- **No Return Type:** Constructors do not have a return type, not even `void`.
- **Called Automatically:** When an object is created using `new`, the constructor is called automatically.

**3. Types of Constructors:**

- **Default Constructor:**
    - A constructor with no parameters.
    - If no constructor is defined in a class, Java provides a default constructor.
    - Example:
        
        ```java
        
        class Example {
            Example() {
                System.out.println("Default constructor called.");
            }
        }
        
        ```
        
- **Parameterized Constructor:**
    - A constructor that takes arguments to initialize the object with specific values.
    - Example:
        
        ```java
        
        class Example {
            int x;
            Example(int a) {
                x = a;
            }
        }
        
        ```
        

**4. Overloading Constructors:**

- Java allows you to have multiple constructors in a class, each with different parameter lists. This is known as constructor overloading.
- Example:
    
    ```java
    
    class Example {
        int x;
        Example() {
            x = 0;
        }
        Example(int a) {
            x = a;
        }
    }
    
    ```
    

**5. Use of `this()` Keyword:**

- The `this()` keyword is used to call one constructor from another constructor in the same class.
- It helps to avoid code duplication.
- Example:
    
    ```java
    
    class Example {
        int x;
        Example() {
            this(10);  // calls the parameterized constructor
        }
        Example(int a) {
            x = a;
        }
    }
    
    ```
    

**6. Important Points:**

- **Inheritance:** Constructors are not inherited by subclasses. However, a subclass constructor can call a superclass constructor using the `super()` keyword.
- **Constructor Chaining:** This refers to the process where one constructor calls another constructor in the same or parent class.

**7. Constructor vs. Method:**

- **Constructor:** Initializes an object; no return type; name is the same as the class.
- **Method:** Performs specific tasks; has a return type; name can be any valid identifier.