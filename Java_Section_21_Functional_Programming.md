# Java Section 21 — Functional Programming (Lambda, Streams, Functional Interfaces)

## 1. Introduction to Functional Programming in Java
Java 8 introduced functional programming features such as **lambda expressions**, **streams**, and **functional interfaces**.  
These features allow writing concise, expressive, and efficient code.

---

## 2. Functional Interfaces
A **functional interface** has exactly **one abstract method**.

Examples:
- Runnable
- Callable
- Comparator
- Function, Predicate, Consumer, Supplier

### Example: Custom Functional Interface
```java
@FunctionalInterface
interface Greeting {
    void sayHello(String name);
}

public class Main {
    public static void main(String[] args) {
        Greeting g = (name) -> System.out.println("Hello " + name);
        g.sayHello("Ishant");
    }
}
```

---

## 3. Lambda Expressions
Lambda expression syntax:
```
(parameters) -> expression
(parameters) -> { multiple statements }
```

### Example
```java
Runnable r = () -> System.out.println("Thread running...");
new Thread(r).start();
```

### Example: Comparator with Lambda
```java
List<Integer> list = Arrays.asList(5, 2, 8, 1);
Collections.sort(list, (a, b) -> a - b);
System.out.println(list);
```

---

## 4. Method References
Shorthand for lambda calling an existing method.

Types:
- Object::instanceMethod
- Class::staticMethod
- Class::instanceMethod

### Example
```java
list.forEach(System.out::println);
```

---

## 5. Streams API
A Stream processes data in a **pipeline** of operations:
- Intermediate: map(), filter(), sorted()
- Terminal: collect(), forEach(), reduce()

### Example: Filtering & Mapping
```java
List<String> names = Arrays.asList("Ram", "Shyam", "Aman");

names.stream()
    .filter(n -> n.startsWith("A"))
    .map(String::toUpperCase)
    .forEach(System.out::println);
```

---

## 6. Collectors
Collectors convert stream results into lists, sets, maps, etc.

### Example
```java
List<Integer> nums = Arrays.asList(1,2,3,4,5);

List<Integer> even = nums.stream()
    .filter(n -> n % 2 == 0)
    .collect(Collectors.toList());
```

---

## 7. Reduce Operation
Used to accumulate values.

### Example
```java
int sum = nums.stream()
              .reduce(0, (a, b) -> a + b);
```

---

## 8. Parallel Streams
Automatically parallelize stream operations.

### Example
```java
nums.parallelStream()
    .forEach(System.out::println);
```

---

## 9. Built-in Functional Interfaces

### Predicate (returns boolean)
```java
Predicate<Integer> isEven = num -> num % 2 == 0;
```

### Function (input → output)
```java
Function<String, Integer> len = str -> str.length();
```

### Consumer (accepts, returns nothing)
```java
Consumer<String> c = s -> System.out.println(s);
```

### Supplier (provides value)
```java
Supplier<Double> random = () -> Math.random();
```

---

## 10. Full Example: Lambda + Streams + Functional Interfaces

```java
import java.util.*;
import java.util.stream.*;

public class Main {
    public static void main(String[] args) {
        List<Integer> nums = Arrays.asList(10, 3, 7, 8, 2, 6);

        // Filter even numbers, square them, sort and collect
        List<Integer> result = nums.stream()
            .filter(n -> n % 2 == 0)
            .map(n -> n * n)
            .sorted()
            .collect(Collectors.toList());

        System.out.println(result);
    }
}
```

---

## 11. Advantages of Functional Programming
- More concise code
- Easy parallelization
- Less boilerplate
- Fewer bugs (stateless functions)

---

## 12. When to Use
- Data transformation  
- Filtering, mapping, sorting  
- Event-handling with functional interfaces  
- When concise callback logic is needed  

---

## End of Section 21
