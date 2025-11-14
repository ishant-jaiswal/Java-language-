# Java Section 27 — Performance Tips & Profiling

## 1. Introduction
Performance optimization in Java focuses on writing efficient code, reducing memory usage, minimizing unnecessary computations, and using JVM tools to diagnose bottlenecks. This section provides best practices and real profiling examples.

---

## 2. General Performance Tips

### ✔ Avoid Creating Unnecessary Objects
```java
String s = new String("hello"); // Bad
String s2 = "hello";            // Good
```

### ✔ Use StringBuilder for heavy string operations
```java
StringBuilder sb = new StringBuilder();
for(int i = 0; i < 1000; i++) sb.append(i);
```

### ✔ Prefer primitives over wrapper types
Primitives avoid boxing/unboxing overhead.

### ✔ Use efficient collections
- `ArrayList` for indexed access  
- `LinkedList` for frequent insert/delete  
- `HashMap` for fast lookup  
- `ConcurrentHashMap` for thread-safety  

### ✔ Avoid synchronized blocks unless required

### ✔ Minimize I/O operations  
Prefer buffered streams:
```java
BufferedReader br = new BufferedReader(new FileReader("data.txt"));
```

---

## 3. JVM & Garbage Collection Related Tips

### ✔ Choose the right GC
Common choices:
- **G1GC** (default)
- **ZGC** (low latency)
- **Shenandoah GC**

### ✔ Avoid memory leaks
Common causes:
- Static collections holding objects
- Unclosed resources
- Caches without eviction logic

### ✔ Use try-with-resources
```java
try(FileInputStream fis = new FileInputStream("a.txt")) { }
```

---

## 4. Profiling Tools

### ✔ Java Flight Recorder (JFR)
Use:
```
java -XX:StartFlightRecording=name=TestRecording,filename=recording.jfr
```

View using:
- Java Mission Control (JMC)

### ✔ VisualVM
Monitors:
- CPU usage  
- Heap dump  
- Thread activity  
- GC events  

### ✔ JProfiler / YourKit  
Commercial, powerful profilers.

---

## 5. Profiling Example (CPU Hotspot)

Suppose this code is slow:
```java
public static int slowSum() {
    int sum = 0;
    for(int i = 0; i < 1_000_000; i++) {
        sum += expensiveOperation(i);
    }
    return sum;
}

public static int expensiveOperation(int x) {
    return (int)Math.pow(x, 2); // slow!
}
```

### Optimization:
Replace Math.pow (expensive) with multiplication:
```java
return x * x;
```

---

## 6. Memory Profiling Example

### Problem: Memory leak
```java
static List<String> cache = new ArrayList<>();

public void addData() {
    cache.add(new String(new byte[1024 * 1024])); // 1 MB
}
```

### Fix:
Use WeakReference or proper cache eviction:
```java
cache.clear();
```

---

## 7. Microbenchmarking with JMH (Java Microbenchmark Harness)

Add dependency:
```xml
<dependency>
  <groupId>org.openjdk.jmh</groupId>
  <artifactId>jmh-core</artifactId>
  <version>1.37</version>
</dependency>
```

### Sample Benchmark
```java
@Benchmark
public void testListAdd() {
    List<Integer> list = new ArrayList<>();
    for(int i = 0; i < 1000; i++) list.add(i);
}
```

Run:
```
mvn clean install
java -jar target/benchmarks.jar
```

---

## 8. Best Practices Summary

- Use proper data structures.
- Prefer primitives.
- Avoid unnecessary object creation.
- Profile before optimizing.
- Use the right GC for your use-case.
- Avoid blocking synchronization.
- Use JMH for benchmarking.
- Monitor memory leaks via heap dumps.

---

## End of Section 27
Next section will cover **Testing with JUnit**.
