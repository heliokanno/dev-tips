# SOLID


SOLID is an acronym that represents a set of five design principles for writing maintainable and scalable software. These principles were introduced by Robert C. Martin and are widely used in object-oriented programming to create more robust and flexible codebases. 

Following these SOLID principles leads to more maintainable, flexible, and testable code. While applying these principles might add some complexity in the short term, they ultimately result in a codebase that is easier to maintain and adapt as requirements change over time.

Let's dive into each principle:

1. S - Single Responsibility Principle:
This principle states that a class should have only one reason to change. In other words, a class should have a single responsibility or concern. It promotes modular and focused code. If a class has multiple responsibilities, changes in one area might inadvertently affect other areas.

2. O - Open/Closed Principle:
The Open/Closed Principle suggests that software entities (classes, modules, functions) should be open for extension but closed for modification. This means that you should be able to add new functionality to a system without changing existing code. This is typically achieved through the use of interfaces, abstract classes, and inheritance.

3. L - Liskov Substitution Principle:
The Liskov Substitution Principle states that objects of a superclass should be replaceable with objects of a subclass without affecting the correctness of the program. In other words, if a class is a subclass of another class, it should be able to be used wherever the parent class is used without causing unexpected behavior.

4. I - Interface Segregation Principle:
This principle suggests that a class should not be forced to implement interfaces it does not use. Instead of having large and monolithic interfaces, interfaces should be segregated into smaller, more specific ones. This prevents classes from implementing unnecessary methods and leads to cleaner code.

5. D - Dependency Inversion Principle:
The Dependency Inversion Principle emphasizes that high-level modules should not depend on low-level modules. Both should depend on abstractions. Additionally, abstractions should not depend on details; details should depend on abstractions. This principle encourages the use of dependency injection, interfaces, and inversion of control containers to decouple components and improve flexibility.

# Examples

These simplified examples demonstrate the core concepts of each SOLID principle using Java.

## Single Responsibility Principle (SRP)

```java
// Before SRP
class Report {
    public void generateReport() {
        // Generate report logic
    }
    public void saveToFile() {
        // Save report to file logic
    }
}

// After SRP
class ReportGenerator {
    public void generateReport() {
        // Generate report logic
    }
}

class ReportSaver {
    public void saveToFile() {
        // Save report to file logic
    }
}
```

## Open/Closed Principle (OCP)

```java
// Before OCP
class Shape {
    public void draw() {
        // Draw shape logic
    }
}

// Adding a new shape requires modifying the existing class
class Circle extends Shape {
    @Override
    public void draw() {
        // Draw circle logic
    }
}

// After OCP
interface Drawable {
    void draw();
}

class Shape implements Drawable {
    @Override
    public void draw() {
        // Draw shape logic
    }
}

class Circle implements Drawable {
    @Override
    public void draw() {
        // Draw circle logic
    }
}
```

## Liskov Substitution Principle (LSP)

```java
// Violating LSP
class Bird {
    void fly() {
        // Fly logic
    }
}

class Ostrich extends Bird {
    // Ostriches can't fly, so this subclass violates LSP
}

// Following LSP
interface Bird {
    void move();
}

class FlyingBird implements Bird {
    @Override
    public void move() {
        // Fly logic
    }
}

class Ostrich implements Bird {
    @Override
    public void move() {
        // Ostrich move logic (e.g., running)
    }
}
```

## Interface Segregation Principle (ISP)

```java
// Violating ISP
interface Worker {
    void work();
    void eat();
}

class Programmer implements Worker {
    // Programmer may not need the eat() method
}

// Following ISP
interface Workable {
    void work();
}

interface Feedable {
    void eat();
}

class Programmer implements Workable {
    // Programmer only implements work() method
}
```

## Dependency Inversion Principle (DIP)

```java
// Without DIP
class LightBulb {
    public void turnOn() {
        // Turn on logic
    }
}

class Switch {
    private LightBulb bulb;
    
    public Switch(LightBulb bulb) {
        this.bulb = bulb;
    }
    
    public void operate() {
        bulb.turnOn();
    }
}

// With DIP
interface Switchable {
    void turnOn();
}

class LightBulb implements Switchable {
    @Override
    public void turnOn() {
        // Turn on logic
    }
}

class Switch {
    private Switchable device;
    
    public Switch(Switchable device) {
        this.device = device;
    }
    
    public void operate() {
        device.turnOn();
    }
}
```