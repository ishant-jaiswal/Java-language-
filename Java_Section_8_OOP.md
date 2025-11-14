
# Section 8 — Object-Oriented Programming in Java  
Deep Explanation + Code Examples

---

## 1. What is OOP?

Object-Oriented Programming (OOP) is a programming paradigm based on the concept of **objects**, which contain:

- **Data** → variables (fields)
- **Behavior** → functions (methods)

Java is **fully object-oriented**, except for primitive data types.

---

## 2. Class and Object

### **Class**
A class is a blueprint/template.

### **Object**
An object is an instance of a class.

### Example:
```java
class Car {
    String brand;
    int year;

    void display() {
        System.out.println("Brand: " + brand);
        System.out.println("Year: " + year);
    }
}

public class Main {
    public static void main(String[] args) {
        Car c1 = new Car();      // object creation
        c1.brand = "Honda";
        c1.year = 2020;

        c1.display();
    }
}
```

---

## 3. Constructors

A constructor is a special method that:

- Has the same name as the class
- Has no return type
- Runs automatically when an object is created

### Types:
1. **Default Constructor**
2. **Parameterized Constructor**
3. **Copy Constructor (manually created)**

---

### **Default Constructor Example**
```java
class Student {
    Student() {
        System.out.println("Default Constructor Called");
    }
}

public class Main {
    public static void main(String[] args) {
        Student s = new Student();
    }
}
```

---

### **Parameterized Constructor Example**
```java
class Student {
    String name;
    int age;

    Student(String n, int a) {
        name = n;
        age = a;
    }

    void display() {
        System.out.println(name + " : " + age);
    }
}

public class Main {
    public static void main(String[] args) {
        Student s1 = new Student("John", 21);
        s1.display();
    }
}
```

---

### **Copy Constructor (Manual Implementation)**
```java
class Student {
    String name;

    Student(String n) {
        name = n;
    }

    // copy constructor
    Student(Student s) {
        this.name = s.name;
    }

    void show() {
        System.out.println("Name: " + name);
    }
}

public class Main {
    public static void main(String[] args) {
        Student s1 = new Student("Ram");
        Student s2 = new Student(s1);  // copy

        s2.show();
    }
}
```

---

## 4. this Keyword

`this` refers to the **current object**.

### Use cases:
- Resolve variable name conflicts
- Call constructors
- Return current object

---

### Example:
```java
class Box {
    int length;

    Box(int length) {
        this.length = length; // using this keyword
    }
}
```

---

## 5. Constructor Overloading

Multiple constructors with different parameters.

```java
class Person {
    Person() {
        System.out.println("No Data");
    }

    Person(String name) {
        System.out.println("Name: " + name);
    }

    Person(String name, int age) {
        System.out.println("Name: " + name + ", Age: " + age);
    }
}
```

---

## 6. Method Overloading

Same method name, different parameters.

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
```

---

## 7. Anonymous Objects

Objects created without storing a reference.

```java
new Car().display();
```

---

## 8. Final Notes

- Every Java program is based on classes and objects.
- Constructors initialize objects.
- `this` helps differentiate instance variables from local variables.
- Overloading provides flexibility.

---


