# Package

### **Today We Will Learn About Packages in Java**

In Java, **packages** are like folders that help you organize and group related classes, interfaces, and sub-packages together. They allow you to structure your programs in a way that makes the code easier to maintain, avoid name conflicts, and provide better access control.

### **Why Use Packages?**

1. **Code Organization**: It makes your codebase neat and easy to manage by grouping similar classes.
2. **Name Collision Prevention**: Packages prevent conflicts between classes with the same name by putting them in different namespaces.
3. **Access Control**: Packages help in controlling access to classes, methods, and variables (through access modifiers).
4. **Reusability**: You can easily reuse classes from different packages by importing them into other programs.

### **Types of Packages in Java**

1. **Built-in Packages**: These are provided by Java (e.g., `java.util`, `java.io`, `java.lang`) and contain useful pre-defined classes.
2. **User-defined Packages**: These are custom packages that you create to organize your own classes.

### **How to Create a Package in Java**

To create a package, you simply use the `package` keyword followed by the package name at the beginning of your Java file.

### **Example**:

```java
package mypackage;

public class MyClass {
    public void display() {
        System.out.println("Hello from MyClass in mypackage!");
    }
}

```

### **How to Use Packages**

To use a class from a package in another program, you need to **import** it using the `import` keyword.

### **Example**:

```java
import mypackage.MyClass;

public class Main {
    public static void main(String[] args) {
        MyClass obj = new MyClass();
        obj.display();
    }
}

```

### **Java Built-in Packages**

Some commonly used built-in packages include:

- `java.lang`: Contains fundamental classes like `String`, `Math`, etc. (Automatically imported).
- `java.util`: Contains utility classes like `ArrayList`, `HashMap`, etc.
- `java.io`: Handles input/output operations.

### **Access Control in Packages**

Access modifiers determine the visibility of classes and their members within and across packages:

1. **Public**: Accessible from anywhere.
2. **Protected**: Accessible within the same package and subclasses.
3. **Default (no modifier)**: Accessible only within the same package.
4. **Private**: Accessible only within the same class.

### **Practical Example of Using Packages**

Let’s create a simple example using custom packages:

### **Step 1: Create a package with a class**

```java
package library;

public class Book {
    String title;
    String author;

    public Book(String title, String author) {
        this.title = title;
        this.author = author;
    }

    public void displayInfo() {
        System.out.println("Title: " + title);
        System.out.println("Author: " + author);
    }
}

```

### **Step 2: Create a program that imports and uses the package**

```java
import library.Book;

public class Main {
    public static void main(String[] args) {
        Book book = new Book("1984", "George Orwell");
        book.displayInfo();
    }
}

```

### **Step 3: Compile and Run**

First, compile the class with the package:

```
javac -d . Book.java

```

Then compile and run the `Main` class:

```
javac Main.java
java Main

```

**Output**:

```
Title: 1984
Author: George Orwell

```

### **Conclusion**

Packages are a powerful way to organize Java code, manage access control, and prevent name collisions. They are essential for structuring large-scale applications in a clean and modular fashion.