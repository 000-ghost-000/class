# inheritance

creating a new class from an existing class or old class is inheritance 

a class that is inherited is called parent class or super class or base class

the class that does the inheriting is called sub class or child class 

to inherit a class we use the extends keyword

Inheritance is one of the four fundamental principles of Object-Oriented Programming (OOP) in Java, alongside Encapsulation, Polymorphism, and Abstraction. It allows a class (called the subclass or derived class) to inherit properties and behaviors (methods) from another class (called the superclass or base class).

### 1. **Basic Concepts**

- **Superclass (Parent Class):** The class whose features are inherited is known as the superclass.
- **Subclass (Child Class):** The class that inherits the features of another class is known as the subclass.
- **`extends` Keyword:** In Java, inheritance is implemented using the `extends` keyword. A subclass extends a superclass to inherit its properties and methods.

**Syntax:**

```java

class Superclass {
    // properties and methods
}

class Subclass extends Superclass {
    // additional properties and methods
}

```

Example:

```java

class Animal {
    void eat() {
        System.out.println("This animal eats food.");
    }
}

class Dog extends Animal {
    void bark() {
        System.out.println("The dog barks.");
    }
}

public class Main {
    public static void main(String[] args) {
        Dog dog = new Dog();
        dog.eat();  // Inherited method
        dog.bark(); // Subclass-specific method
    }
}

```

### 2. **Types of Inheritance in Java**

- **Single Inheritance:** A subclass inherits from a single superclass.
- **Multilevel Inheritance:** A class is derived from another derived class, creating a chain of inheritance.
- **Hierarchical Inheritance:** Multiple subclasses inherit from a single superclass.

**Example of Multilevel Inheritance:**

```java

class Animal {
    void eat() {
        System.out.println("This animal eats food.");
    }
}

class Mammal extends Animal {
    void run() {
        System.out.println("Mammals can run.");
    }
}

class Dog extends Mammal {
    void bark() {
        System.out.println("The dog barks.");
    }
}

public class Main {
    public static void main(String[] args) {
        Dog dog = new Dog();
        dog.eat();  // Animal class method
        dog.run();  // Mammal class method
        dog.bark(); // Dog class method
    }
}

```

**Note:** Java **does not** support multiple inheritance (i.e., a class cannot inherit from more than one superclass) to avoid complexity and ambiguity (the "diamond problem"). However, multiple inheritance can be achieved using **interfaces**.

### 3. **Advantages of Inheritance**

- **Code Reusability:** By inheriting from existing classes, new classes can reuse the methods and properties, reducing redundancy and improving maintainability.
- **Method Overriding:** Subclasses can modify or extend the behavior of methods inherited from the superclass.
- **Extensibility:** Inheritance allows the creation of a new class by building upon the existing codebase, making it easier to extend functionalities.
- **Code Organization:** It provides a logical framework to organize and structure code in a hierarchical manner.

### 4. **Method Overriding**

- **Definition:** Overriding occurs when a subclass provides a specific implementation for a method that is already defined in its superclass.
- **Rules for Overriding:**
    - The method in the subclass must have the same name, return type, and parameters as the method in the superclass.
    - The overridden method must be accessible (e.g., it cannot have a stricter access level than the superclass method).
    - The overriding method can use the `super` keyword to call the superclass method.

**Example:**

```java

class Animal {
    void sound() {
        System.out.println("This animal makes a sound.");
    }
}

class Dog extends Animal {
    @Override
    void sound() {
        System.out.println("The dog barks.");
    }
}

public class Main {
    public static void main(String[] args) {
        Dog dog = new Dog();
        dog.sound();  // This will call the overridden method in Dog class
    }
}

```

### 5. **`super` Keyword**

- **Definition:** The `super` keyword is used to refer to the immediate superclass object. It can be used to:
    - Call the superclass constructor.
    - Access the superclass's methods and fields.

**Example:**

```java

class Animal {
    String name = "Animal";

    void sound() {
        System.out.println("This animal makes a sound.");
    }
}

class Dog extends Animal {
    String name = "Dog";

    void sound() {
        super.sound();  // Call superclass method
        System.out.println("The dog barks.");
    }

    void printName() {
        System.out.println("Name: " + super.name);  // Access superclass field
    }
}

public class Main {
    public static void main(String[] args) {
        Dog dog = new Dog();
        dog.sound();
        dog.printName();
    }
}

```

### 6. **Constructors in Inheritance**

- **Calling Superclass Constructors:** When a subclass object is created, the constructor of the superclass is called first (implicitly or explicitly) to initialize the superclass part of the object.
- **Using `super()`:** You can explicitly call the superclass constructor using `super()` within the subclass constructor.

**Example:**

```java

class Animal {
    Animal() {
        System.out.println("Animal constructor");
    }
}

class Dog extends Animal {
    Dog() {
        super();  // Call to superclass constructor
        System.out.println("Dog constructor");
    }
}

public class Main {
    public static void main(String[] args) {
        Dog dog = new Dog();  // This will invoke both Animal and Dog constructors
    }
}

```

### 7. **Final Keyword and Inheritance**

- **Final Class:** If a class is declared as `final`, it cannot be subclassed. This prevents inheritance.
    - **Example:**
    
    ```java
    
    final class Animal {
        // properties and methods
    }
    
    // This will cause an error
    // class Dog extends Animal { }
    
    ```
    
- **Final Method:** A method marked as `final` cannot be overridden by subclasses.
    - **Example:**
    
    ```java
    
    class Animal {
        final void sound() {
            System.out.println("This animal makes a sound.");
        }
    }
    
    class Dog extends Animal {
        // This will cause an error
        // void sound() { System.out.println("The dog barks."); }
    }
    
    ```
    

### 8. **Abstract Classes and Inheritance**

- **Abstract Class:** An abstract class cannot be instantiated directly and may contain abstract methods (methods without implementation). Subclasses are required to provide implementations for these abstract methods.
- **Use of Inheritance:** Abstract classes serve as base classes, defining a common interface for subclasses.

**Example:**

```java

abstract class Animal {
    abstract void sound();  // Abstract method

    void eat() {
        System.out.println("This animal eats food.");
    }
}

class Dog extends Animal {
    void sound() {
        System.out.println("The dog barks.");
    }
}

public class Main {
    public static void main(String[] args) {
        Animal dog = new Dog();  // Polymorphism
        dog.sound();  // Calls the Dog class implementation
        dog.eat();    // Calls the Animal class method
    }
}

```

### 9. **Interface Inheritance**

- **Interfaces in Java:** Interfaces provide a way to achieve multiple inheritance. A class can implement multiple interfaces, inheriting the abstract methods from all of them.

**Example:**

```java

interface CanRun {
    void run();
}

interface CanBark {
    void bark();
}

class Dog implements CanRun, CanBark {
    public void run() {
        System.out.println("The dog runs.");
    }

    public void bark() {
        System.out.println("The dog barks.");
    }
}

public class Main {
    public static void main(String[] args) {
        Dog dog = new Dog();
        dog.run();
        dog.bark();
    }
}

```

### 10. **Best Practices with Inheritance**

- **Use Inheritance Judiciously:** Inheritance should be used when there is a true "is-a" relationship between the classes. If the relationship is more of a "has-a" relationship, composition may be a better option.
- **Avoid Deep Inheritance Hierarchies:** Deep inheritance hierarchies can make code difficult to understand and maintain. Prefer composition over inheritance when possible.
- **Use `super` Carefully:** When overriding methods, be cautious about using `super` to ensure you are not unintentionally bypassing the subclass's functionality.
- **Final and Abstract Classes:** Use `final` and `abstract` keywords effectively to control the inheritance structure and ensure that your code cannot be misused or extended in unintended ways.

### 11. **Real-World Example**

Consider a scenario where you have different types of vehicles, and you want to model them using inheritance.

```java

class Vehicle {
    void startEngine() {
        System.out.println("Starting the engine...");
    }
}

class Car extends Vehicle {
    void openDoors() {
        System.out.println("Opening the car doors

```