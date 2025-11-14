
# Section 9 — Inheritance in Java  
Deep Explanation + Code Examples

---

## 1. What is Inheritance?

Inheritance is an OOP feature that allows one class (child) to acquire the properties and methods of another class (parent).

### Benefits:
- Code Reusability  
- Easy Maintenance  
- Method Overriding  
- Supports Polymorphism  

### Syntax:
```java
class Parent { }
class Child extends Parent { }
```

---

## 2. Types of Inheritance in Java

### ✔ Supported:
1. **Single Inheritance**
2. **Multilevel Inheritance**
3. **Hierarchical Inheritance**

### ❌ Not Supported:
- **Multiple Inheritance (Class Level)** — avoided to solve ambiguity (diamond problem)

---

## 3. Single Inheritance

```java
class Animal {
    void eat() {
        System.out.println("Eating...");
    }
}

class Dog extends Animal {
    void bark() {
        System.out.println("Barking...");
    }
}

public class Main {
    public static void main(String[] args) {
        Dog d = new Dog();
        d.eat();
        d.bark();
    }
}
```

---

## 4. Multilevel Inheritance

```java
class Animal {
    void eat() { System.out.println("Eating..."); }
}

class Dog extends Animal {
    void bark() { System.out.println("Barking..."); }
}

class BabyDog extends Dog {
    void weep() { System.out.println("Weeping..."); }
}

public class Main {
    public static void main(String[] args) {
        BabyDog b = new BabyDog();
        b.eat();
        b.bark();
        b.weep();
    }
}
```

---

## 5. Hierarchical Inheritance

```java
class Animal {
    void eat() { System.out.println("Eating"); }
}

class Dog extends Animal {
    void bark() { System.out.println("Bark"); }
}

class Cat extends Animal {
    void meow() { System.out.println("Meow"); }
}

public class Main {
    public static void main(String[] args) {
        Dog d = new Dog();
        d.eat();
        d.bark();

        Cat c = new Cat();
        c.eat();
        c.meow();
    }
}
```

---

## 6. The super Keyword

### Used for:
1. Accessing parent class variables  
2. Calling parent class methods  
3. Calling parent class constructor  

---

### **6.1 Access Parent Variables**
```java
class Parent {
    int x = 10;
}

class Child extends Parent {
    int x = 20;

    void show() {
        System.out.println(super.x); // 10
        System.out.println(x);       // 20
    }
}
```

---

### **6.2 Calling Parent Methods**
```java
class Parent {
    void message() {
        System.out.println("Parent message");
    }
}

class Child extends Parent {
    void message() {
        super.message();
        System.out.println("Child message");
    }
}
```

---

### **6.3 Calling Parent Constructor**
```java
class A {
    A() {
        System.out.println("Parent Constructor");
    }
}

class B extends A {
    B() {
        super();
        System.out.println("Child Constructor");
    }
}

public class Main {
    public static void main(String[] args) {
        B obj = new B();
    }
}
```

---

## 7. Method Overriding

A child class provides its own implementation of a parent class method.

### Rules:
- Same name  
- Same parameters  
- Same return type  
- Child class must extend parent class  

---

### **Example**
```java
class Bike {
    void run() {
        System.out.println("Bike is running");
    }
}

class Splendor extends Bike {
    @Override
    void run() {
        System.out.println("Splendor is running safely");
    }
}

public class Main {
    public static void main(String[] args) {
        Bike b = new Splendor();
        b.run();
    }
}
```

---

## 8. Why Java Does Not Support Multiple Inheritance?

To avoid **ambiguity** of parent methods.

### Example Problem in Multiple Inheritance (NOT allowed in Java):
```
Class A → show()
Class B → show()
Class C extends A, B  ❌ Problem! Which show()?
```

---

## 9. final Keyword in Inheritance

### final class → cannot be inherited
```java
final class A { }
class B extends A { } // Error
```

### final method → cannot be overridden
```java
class A {
    final void show() { }
}

class B extends A {
    void show() { } // Error
}
```

---

## 10. Key Points Summary

| Concept | Meaning |
|--------|---------|
| extends | keyword to inherit |
| super | access parent class |
| overriding | redefining parent methods |
| final | prevent inheritance/overriding |

---



