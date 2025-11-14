# Java Section 18 — Generics  
Generics provide **type safety**, **compile-time checking**, and **reusability** in Java.  
They allow classes, methods, and interfaces to operate on a specific data type without losing flexibility.

---

# **1. Why Generics?**
### Without generics:
- Collections store `Object`
- Typecasting required
- Runtime errors common

### With generics:
- Type-safe code
- No typecasting needed
- Errors detected at **compile time**

---

# **2. Generic Class**

```java
class Box<T> {
    private T value;

    public void set(T value) {
        this.value = value;
    }

    public T get() {
        return value;
    }
}

public class Demo {
    public static void main(String[] args) {
        Box<String> b = new Box<>();
        b.set("Hello Java");
        System.out.println(b.get());
    }
}
```

### Output:
```
Hello Java
```

---

# **3. Generic Methods**

```java
public class Util {
    public <T> void show(T data) {
        System.out.println("Data: " + data);
    }
}

class Test {
    public static void main(String[] args) {
        Util u = new Util();
        u.show(100);        // Integer
        u.show("Java");     // String
        u.show(12.55);      // Double
    }
}
```

---

# **4. Generic Constructor**

```java
class Sample {
    <T> Sample(T data) {
        System.out.println("Data: " + data);
    }
}

public class Demo {
    public static void main(String[] args) {
        new Sample(100);
        new Sample("Hello");
    }
}
```

---

# **5. Bounded Type Parameters**

### Upper Bound  
Restrict to a specific class or its subclasses.

```java
class Calculator<T extends Number> {
    T num;

    Calculator(T num) { this.num = num; }

    double getDoubleValue() {
        return num.doubleValue();
    }
}
```

---

### Lower Bound  
Useful with wildcards.

```java
List<? super Integer> list;
```

---

# **6. Wildcards in Generics**

Wildcards provide flexibility in generics.

---

## **6.1 Unbounded Wildcard `<?>`**

```java
public void printList(List<?> list) {
    for (Object o : list)
        System.out.println(o);
}
```

---

## **6.2 Upper Bounded Wildcard `<? extends T>`**

```java
List<? extends Number> nums;
```

Accepts:
- Integer
- Double
- Float
- Number

---

## **6.3 Lower Bounded Wildcard `<? super T>`**

```java
List<? super Integer> numList;
```

Accepts:
- Integer
- Number
- Object

Used for writing values safely.

---

# **7. Generics with Collections**

```java
ArrayList<String> list = new ArrayList<>();
list.add("Java");      // safe
```

### Without Generics (Old Way)
```java
ArrayList list = new ArrayList();
list.add("Java");
list.add(10);   // allowed — risky
```

---

# **8. Generic Interface**

```java
interface Storage<T> {
    void store(T item);
}

class Data implements Storage<String> {
    public void store(String item) {
        System.out.println("Storing: " + item);
    }
}
```

---

# **9. Multiple Type Parameters**

```java
class Pair<K, V> {
    K key;
    V value;

    Pair(K key, V value) {
        this.key = key;
        this.value = value;
    }
}
```

---

# **10. Restrictions in Generics**
- Cannot use primitive types → `List<int>` ❌  
  Must use wrappers → `List<Integer>` ✔
- Cannot create objects → `T obj = new T();` ❌
- Cannot create arrays → `T[] arr = new T[10];` ❌

---

# **11. Best Practices**
- Use generics everywhere possible.
- Prefer upper/lower bounds only when needed.
- Avoid raw types completely.

---


