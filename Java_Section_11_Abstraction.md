
# Section 11 — Abstraction in Java  
Deep Explanation + Code Examples

---

## 1. What is Abstraction?

Abstraction is the process of hiding internal implementation details and showing only essential features to the user.

Example in real life:  
- When you drive a car, you use the steering, accelerator, and brake, but you don’t know the engine implementation.

In Java, abstraction is achieved using:

1. **Abstract Classes (0–100% abstraction)**
2. **Interfaces (100% abstraction)**

---

# 2. Abstract Classes

An abstract class:
- Cannot be instantiated
- Can have abstract + non-abstract methods
- Can have constructors, variables, and normal methods
- Must be extended by a subclass

### Syntax:
```java
abstract class ClassName {
    abstract void method1();
    void method2() { }
}
```

---

## 2.1 Example of Abstract Class

```java
abstract class Animal {
    abstract void sound();         // abstract method

    void eat() {                   // concrete method
        System.out.println("Animal eats food");
    }
}

class Dog extends Animal {
    @Override
    void sound() {
        System.out.println("Dog barks");
    }
}

public class Main {
    public static void main(String[] args) {
        Animal a = new Dog();
        a.sound();
        a.eat();
    }
}
```

---

## 2.2 Why Use Abstract Classes?

- To provide a **common base** for all subclasses
- To force subclasses to implement certain methods
- To provide **partial abstraction**

---

# 3. Interfaces

An interface:
- Contains abstract methods (Java 7)
- Can contain default, static, and private methods (Java 8+)
- Cannot have constructors
- Supports **multiple inheritance**
- Achieves **100% abstraction**

### Syntax:
```java
interface Animal {
    void sound(); // public and abstract by default
}
```

---

## 3.1 Example of Interface

```java
interface Animal {
    void sound();
}

class Dog implements Animal {
    public void sound() {
        System.out.println("Dog barks");
    }
}

public class Main {
    public static void main(String[] args) {
        Animal a = new Dog();
        a.sound();
    }
}
```

---

# 4. Interface with Multiple Inheritance

```java
interface A {
    void show();
}

interface B {
    void display();
}

class C implements A, B {
    public void show() {
        System.out.println("Show from A");
    }

    public void display() {
        System.out.println("Display from B");
    }
}

public class Main {
    public static void main(String[] args) {
        C obj = new C();
        obj.show();
        obj.display();
    }
}
```

---

# 5. Default and Static Methods in Interfaces (Java 8+)

## 5.1 Default Method
```java
interface Vehicle {
    default void start() {
        System.out.println("Vehicle is starting");
    }
}
```

## 5.2 Static Method
```java
interface Car {
    static void horn() {
        System.out.println("Car horn: Beep Beep");
    }
}
```

---

# 6. Difference Between Abstract Class and Interface

| Feature | Abstract Class | Interface |
|--------|----------------|-----------|
| Methods | Abstract + Normal | Abstract + default + static |
| Variables | Any type | public static final only |
| Constructor | Allowed | Not allowed |
| Multiple Inheritance | Not supported | Supported |
| Abstraction | 0–100% | 100% |
| Use Case | Base class | Pure abstraction |

---

# 7. Real-Life Example: Payment System

### Abstract Class Example:
```java
abstract class Payment {
    abstract void pay();
}

class UPI extends Payment {
    void pay() { System.out.println("Paid using UPI"); }
}

class Card extends Payment {
    void pay() { System.out.println("Paid using Card"); }
}
```

### Interface Example:
```java
interface Transaction {
    void process();
}

class UPITransaction implements Transaction {
    public void process() {
        System.out.println("Processing UPI Transaction");
    }
}
```

---

# 8. Key Points Summary

- Abstraction hides implementation details.
- **Abstract classes** allow both abstract and concrete methods.
- **Interfaces** provide 100% abstraction and support multiple inheritance.
- Java 8 allowed default and static methods in interfaces.

---

