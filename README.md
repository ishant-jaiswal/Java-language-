# Java --- From Scratch to Advanced

> A single-file guide covering Java concepts (definitions, explanations,
> and runnable examples) from beginner to advanced. Use this as a study
> reference or a starter template for projects.

------------------------------------------------------------------------

## Table of Contents

1.  Introduction & Setup
2.  Basic Syntax
3.  Primitive Types & Variables
4.  Operators & Expressions
5.  Control Flow (if, switch, loops)
6.  Methods & Recursion
7.  Object-Oriented Programming (Classes, Objects, Inheritance,
    Polymorphism, Abstraction, Encapsulation)
8.  Access Modifiers & Packages
9.  Exception Handling
10. Java Standard Library Essentials (String, Math, Wrapper classes)
11. Collections Framework (List, Set, Map, Queue) + Iteration
12. Generics
13. Java I/O (Streams, Readers/Writers, Files, NIO)
14. Concurrency (Threads, Executors, Synchronization, Locks,
    CompletableFuture)
15. Functional Programming (Lambda, Streams, Functional Interfaces)
16. Annotations & Reflection
17. JDBC (Database access example)
18. Serialization & Deserialization
19. Modules (JPMS) & Classpath
20. JVM Internals, Memory Model & GC basics
21. Performance Tips & Profiling
22. Testing (JUnit example)
23. Build Tools (Maven/Gradle basics)
24. Popular Frameworks Overview (Spring, Hibernate) --- short intro
25. Design Patterns --- Common ones with code sketches
26. Resources & Next Steps

------------------------------------------------------------------------

## 1. Introduction & Setup

Java is a high-level, object-oriented, platform-independent programming
language that runs on the Java Virtual Machine (JVM).

**Hello World**

``` java
public class Hello {
    public static void main(String[] args) {
        System.out.println("Hello, Java!");
    }
}
```

------------------------------------------------------------------------

## 2. Basic Syntax

``` java
class SyntaxExample {
    int x = 10;

    void printX() {
        System.out.println(x);
    }

    public static void main(String[] args) {
        SyntaxExample s = new SyntaxExample();
        s.printX();
    }
}
```

------------------------------------------------------------------------

## 3. Primitive Types & Variables

``` java
public class Primitives {
    public static void main(String[] args) {
        int i = 42;
        long l = 1L;
        double d = 3.14;
        boolean b = true;
        char c = 'J';
        System.out.println(i + ", " + l + ", " + d + ", " + b + ", " + c);
    }
}
```

------------------------------------------------------------------------

## 4. Operators & Expressions

``` java
int a = 5;
int b = 3;
int sum = a + b;
boolean test = (a > b) && (b < 10);
```

------------------------------------------------------------------------

## 5. Control Flow

``` java
for (int i = 0; i < 5; i++) {
    if (i % 2 == 0) continue;
    System.out.println(i);
}

switch ("A") {
    case "A": System.out.println("A"); break;
    default: System.out.println("other");
}
```

------------------------------------------------------------------------

## 6. Methods & Recursion

``` java
public class Factorial {
    static long fact(int n) {
        if (n <= 1) return 1;
        return n * fact(n - 1);
    }
    public static void main(String[] args) {
        System.out.println(fact(5));
    }
}
```

------------------------------------------------------------------------

## 7. Object-Oriented Programming

### Classes & Objects

``` java
class Person {
    String name;
    int age;
    Person(String name, int age) {
        this.name = name;
        this.age = age;
    }
    void greet() {
        System.out.println("Hi, I'm " + name);
    }
}
```

### Inheritance & Polymorphism

``` java
class Animal { void speak(){ System.out.println("... "); } }
class Dog extends Animal { void speak(){ System.out.println("Woof"); } }
```

### Interfaces

``` java
interface Shape { double area(); }
class Circle implements Shape {
    double r;
    Circle(double r){this.r=r;}
    public double area(){return Math.PI*r*r;}
}
```

------------------------------------------------------------------------

## 8. Access Modifiers & Packages

``` java
package com.example.utils;
public class Utils { }
```

------------------------------------------------------------------------

## 9. Exception Handling

``` java
try (BufferedReader br = new BufferedReader(new FileReader("nofile.txt"))) {
    System.out.println(br.readLine());
} catch (IOException e) {
    System.err.println("IO error: " + e.getMessage());
}
```

------------------------------------------------------------------------

## 10. Java Standard Library Essentials

### String

``` java
String s = "Hello";
s.length();
s.toUpperCase();
```

------------------------------------------------------------------------

## 11. Collections Framework

``` java
List<String> list = new ArrayList<>();
list.add("a");

Set<Integer> set = new HashSet<>();
Map<String, Integer> map = new HashMap<>();
map.put("k", 1);
```

------------------------------------------------------------------------

## 12. Generics

``` java
class Box<T> {
    private T value;
    public void set(T v){value=v;}
    public T get(){return value;}
}
```

------------------------------------------------------------------------

## 13. Java I/O & NIO

``` java
Files.writeString(Path.of("out2.txt"), "hello nio");
```

------------------------------------------------------------------------

## 14. Concurrency

``` java
ExecutorService ex = Executors.newFixedThreadPool(2);
ex.submit(() -> System.out.println("task"));
ex.shutdown();
```

------------------------------------------------------------------------

## 15. Functional Programming

``` java
List<Integer> nums = List.of(1,2,3,4,5);
int sum = nums.stream().filter(n -> n%2==0).mapToInt(Integer::intValue).sum();
```

------------------------------------------------------------------------

## 16. Reflection

``` java
Class<?> c = Class.forName("java.lang.String");
System.out.println(c.getMethods().length);
```

------------------------------------------------------------------------

## 17. JDBC

``` java
Connection conn = DriverManager.getConnection(url, "user", "pass");
```

------------------------------------------------------------------------

## 18. Serialization

``` java
class Person implements Serializable { String name; }
```

------------------------------------------------------------------------

## 19. Modules

    module com.example.app {
        requires java.sql;
        exports com.example.app.api;
    }

------------------------------------------------------------------------

## 20. JVM Internals & GC Basics

Stack, Heap, Classloader, JIT, GC.

------------------------------------------------------------------------

## 21. Performance Tips

Use StringBuilder, avoid unnecessary objects, profiling tools.

------------------------------------------------------------------------

## 22. Testing (JUnit)

``` java
@Test
void testAdd() {
    assertEquals(5, 2+3);
}
```

------------------------------------------------------------------------

## 23. Build Tools

Maven and Gradle basics.

------------------------------------------------------------------------

## 24. Frameworks

Spring, Hibernate, Microservices frameworks.

------------------------------------------------------------------------

## 25. Design Patterns

Singleton, Factory, Strategy, Observer.

------------------------------------------------------------------------

## 26. Resources

Effective Java, Javadocs, Oracle Tutorials.
