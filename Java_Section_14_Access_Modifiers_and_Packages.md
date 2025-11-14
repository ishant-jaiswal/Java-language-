# Java Section 14 — Access Modifiers & Packages

## 1. Introduction
Access modifiers in Java define the visibility and accessibility of classes, methods, and variables. They help enforce encapsulation and maintain clean architecture.

Java also organizes code using **packages**, which group related classes and interfaces.

---

## 2. Access Modifiers Overview

| Modifier       | Class | Package | Subclass | World |
|----------------|-------|---------|----------|--------|
| public         | ✔     | ✔       | ✔        | ✔      |
| protected      | ✔     | ✔       | ✔        | ✖      |
| default (no keyword) | ✔ | ✔ | ✖ | ✖ |
| private        | ✔     | ✖       | ✖        | ✖      |

---

## 3. Examples  
### 3.1 Public
```java
public class Car {
    public void start() {
        System.out.println("Car starting...");
    }
}
```

---

### 3.2 Private
```java
class BankAccount {
    private double balance;

    private void showBalance() {
        System.out.println(balance);
    }
}
```

---

### 3.3 Protected
```java
class Animal {
    protected void sound() {
        System.out.println("Animal sound");
    }
}

class Dog extends Animal {
    void bark() {
        sound(); // allowed
    }
}
```

---

### 3.4 Default (Package-Private)
```java
class Person {
    void speak() {
        System.out.println("Hello");
    }
}
```

---

## 4. Packages

### 4.1 Creating a Package
```java
package myapp.utils;

public class Calculator {
    public int add(int a, int b) {
        return a + b;
    }
}
```

---

### 4.2 Importing a Package
```java
import myapp.utils.Calculator;

public class Main {
    public static void main(String[] args) {
        Calculator c = new Calculator();
        System.out.println(c.add(5, 3));
    }
}
```

---

## 5. Folder Structure
```
src/
 └── myapp/
      └── utils/
           └── Calculator.java
```

---

## 6. Best Practices
- Use **private** for fields; expose through getters/setters.
- Use **packages** to logically group features.
- Use **public** APIs carefully—think long-term design.
