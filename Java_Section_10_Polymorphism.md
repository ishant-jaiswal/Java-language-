
# Section 10 — Polymorphism in Java  
Deep Explanation + Code Examples

---

## 1. What is Polymorphism?

Polymorphism = **One name, many forms**

It allows the same method name or object reference to behave differently based on the context.

### Types of Polymorphism:
1. **Compile-Time Polymorphism** → Method Overloading  
2. **Run-Time Polymorphism** → Method Overriding  

---

## 2. Compile-Time Polymorphism (Method Overloading)

Occurs when multiple methods have:

- Same name  
- Different parameters (type or count)  

### Example:
```java
class Calculator {
    int add(int a, int b) {
        return a + b;
    }

    double add(double a, double b) {
        return a + b;
    }

    int add(int a, int b, int c) {
        return a + b + c;
    }
}

public class Main {
    public static void main(String[] args) {
        Calculator c = new Calculator();
        System.out.println(c.add(2, 3));
        System.out.println(c.add(2.5, 3.5));
        System.out.println(c.add(1, 2, 3));
    }
}
```

---

## 3. Run-Time Polymorphism (Method Overriding)

Occurs when a subclass provides its own version of a method inherited from the parent class.

### Key Features:
- Uses **dynamic method dispatch**
- Object type decides which method executes at runtime
- Achieved using **inheritance**

---

### Example:
```java
class Animal {
    void sound() {
        System.out.println("Animal makes a sound");
    }
}

class Dog extends Animal {
    @Override
    void sound() {
        System.out.println("Dog barks");
    }
}

class Cat extends Animal {
    @Override
    void sound() {
        System.out.println("Cat meows");
    }
}

public class Main {
    public static void main(String[] args) {
        Animal a;            // Reference variable

        a = new Dog();
        a.sound();          // Dog barks

        a = new Cat();
        a.sound();          // Cat meows
    }
}
```

---

## 4. Dynamic Method Dispatch

A mechanism where:

- Superclass reference
- Refers to subclass object
- Method executed depends on object (runtime)

### Example:
```java
Animal a = new Dog(); // Animal reference, Dog object
a.sound();            // Dog version runs
```

---

## 5. Method Overloading vs Method Overriding

| Feature | Overloading | Overriding |
|--------|-------------|------------|
| Type | Compile-Time | Run-Time |
| Parameters | Must differ | Must be same |
| Class Relation | Same class | Parent-child |
| Return Type | Can differ | Must match |
| Keyword Used | — | @Override |

---

## 6. Covariant Return Types

In overriding, child class can return a **subtype** of the parent's return type.

### Example:
```java
class Animal {}
class Dog extends Animal {}

class Parent {
    Animal getAnimal() {
        return new Animal();
    }
}

class Child extends Parent {
    @Override
    Dog getAnimal() {
        return new Dog();
    }
}
```

---

## 7. Polymorphism with Arrays / Collections

You can store multiple subclasses in a parent-type array.

```java
Animal[] arr = { new Dog(), new Cat(), new Dog() };

for (Animal a : arr) {
    a.sound();
}
```

---

## 8. Polymorphism with Interfaces

Interfaces naturally support runtime polymorphism.

```java
interface Shape {
    void draw();
}

class Circle implements Shape {
    public void draw() { System.out.println("Drawing Circle"); }
}

class Square implements Shape {
    public void draw() { System.out.println("Drawing Square"); }
}

public class Main {
    public static void main(String[] args) {
        Shape s = new Circle();
        s.draw();

        s = new Square();
        s.draw();
    }
}
```

---

## 9. Final Notes

- Overloading = early binding  
- Overriding = late binding  
- Polymorphism increases flexibility & code scalability  
- Used heavily in frameworks like Spring, Hibernate  

---

**Next Section:**  
### **Section 11 — Abstraction (Abstract Classes, Interfaces)**  
