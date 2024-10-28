# Inheritance in JAVA

In Java, an **interface** is a reference type, similar to a class, but it can only contain **abstract methods** (until Java 8). Interfaces are used to achieve **100% abstraction**, where only the method signatures are provided, and the implementing classes define the actual method bodies.

### **Key Characteristics of Interfaces**:

- **Abstract Methods**: All methods in an interface are abstract by default (i.e., they do not have a body), except for `default` and `static` methods introduced in Java 8.
- **Multiple Inheritance**: A class can implement multiple interfaces, which allows Java to support multiple inheritance.
- **Fields**: Variables declared in an interface are implicitly `public`, `static`, and `final` (i.e., constants).
- **Implementation**: A class must use the `implements` keyword to implement an interface and provide concrete implementations of its methods.

### **Syntax of an Interface**:

```java
interface InterfaceName {
    // Abstract method
    void method1();

    // Default method (from Java 8)
    default void method2() {
        System.out.println("This is a default method.");
    }

    // Static method (from Java 8)
    static void method3() {
        System.out.println("This is a static method.");
    }
}

```

### **Example of an Interface**:

```java
// Interface definition
interface Vehicle {
    // Abstract method
    void start();

    // Abstract method
    void stop();
}

// Implementing interface in Car class
class Car implements Vehicle {
    @Override
    public void start() {
        System.out.println("Car starts with a key.");
    }

    @Override
    public void stop() {
        System.out.println("Car stops with brakes.");
    }
}

// Implementing interface in Bicycle class
class Bicycle implements Vehicle {
    @Override
    public void start() {
        System.out.println("Bicycle starts by pedaling.");
    }

    @Override
    public void stop() {
        System.out.println("Bicycle stops by applying brakes.");
    }
}

public class Main {
    public static void main(String[] args) {
        Vehicle car = new Car();
        car.start();
        car.stop();

        Vehicle bicycle = new Bicycle();
        bicycle.start();
        bicycle.stop();
    }
}

```

### **Output**:

```
Car starts with a key.
Car stops with brakes.
Bicycle starts by pedaling.
Bicycle stops by applying brakes.

```

### **Key Points**:

1. **Abstract Methods**: Interfaces only declare method signatures (before Java 8); implementing classes must define the method bodies.
2. **Default Methods (Java 8)**: Interfaces can now have methods with bodies using the `default` keyword. These methods can be inherited by implementing classes but can be overridden.
3. **Static Methods (Java 8)**: Interfaces can also have `static` methods that belong to the interface itself, not the implementing class.
4. **Multiple Inheritance**: A class can implement multiple interfaces, providing flexibility for polymorphism.

---

### **Practical Example with User Input**

```java
import java.util.Scanner;

// Define an interface
interface Vehicle {
    void start();   // Abstract method
    void stop();    // Abstract method
}

// Car class implementing Vehicle interface
class Car implements Vehicle {
    String brand;
    int doors;

    // Constructor to get input from user
    Car(String brand, int doors) {
        this.brand = brand;
        this.doors = doors;
    }

    @Override
    public void start() {
        System.out.println("Car " + brand + " with " + doors + " doors starts with a key.");
    }

    @Override
    public void stop() {
        System.out.println("Car " + brand + " stops with brakes.");
    }
}

// ElectricCar class implementing Vehicle interface
class ElectricCar implements Vehicle {
    String brand;
    int batteryCapacity;

    // Constructor to get input from user
    ElectricCar(String brand, int batteryCapacity) {
        this.brand = brand;
        this.batteryCapacity = batteryCapacity;
    }

    @Override
    public void start() {
        System.out.println("Electric car " + brand + " starts with a button.");
    }

    @Override
    public void stop() {
        System.out.println("Electric car " + brand + " stops with regenerative braking.");
    }

    void displayBattery() {
        System.out.println("Battery Capacity: " + batteryCapacity + " kWh");
    }
}

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        // Get Car details
        System.out.println("Enter Car brand: ");
        String carBrand = sc.nextLine();
        System.out.println("Enter number of doors: ");
        int doors = sc.nextInt();
        Car car = new Car(carBrand, doors);

        // Get Electric Car details
        sc.nextLine();  // To consume the newline character left by nextInt()
        System.out.println("Enter Electric Car brand: ");
        String eCarBrand = sc.nextLine();
        System.out.println("Enter battery capacity (kWh): ");
        int batteryCapacity = sc.nextInt();
        ElectricCar eCar = new ElectricCar(eCarBrand, batteryCapacity);

        // Start and stop the car
        System.out.println("\\nCar Details:");
        car.start();
        car.stop();

        // Start and stop the electric car, and display battery
        System.out.println("\\nElectric Car Details:");
        eCar.start();
        eCar.stop();
        eCar.displayBattery();
    }
}

```

### **Output**:

```
Enter Car brand:
Toyota
Enter number of doors:
4

Enter Electric Car brand:
Tesla
Enter battery capacity (kWh):
100

Car Details:
Car Toyota with 4 doors starts with a key.
Car Toyota stops with brakes.

Electric Car Details:
Electric car Tesla starts with a button.
Electric car Tesla stops with regenerative braking.
Battery Capacity: 100 kWh

```

---

### **Key Features of the Practical Example**:

1. The `Vehicle` interface is implemented by both the `Car` and `ElectricCar` classes.
2. The `start()` and `stop()` methods are defined in each class based on their specific behavior.
3. The `Car` class takes user input for the brand and number of doors.
4. The `ElectricCar` class takes user input for the brand and battery capacity and adds a method `displayBattery()` to show the electric car's battery information.

This example demonstrates the flexibility and power of interfaces in Java, allowing you to define common behaviors for different types of objects while still allowing each class to implement the details as needed.