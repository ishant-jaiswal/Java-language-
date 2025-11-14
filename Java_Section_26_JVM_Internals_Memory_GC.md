# Java Section 26 — JVM Internals, Memory Model & Garbage Collection

## 1. What is JVM?
JVM (Java Virtual Machine) is the engine that:
- Runs Java bytecode  
- Provides platform independence  
- Manages memory and execution  

JVM = Class Loader + Runtime Data Areas + Execution Engine + GC

---

# 2. JVM Architecture Diagram (Text Version)

```
                +-----------------------+
                |     Class Loader      |
                +----------+------------+
                           |
                           v
+---------------------------------------------------------------+
|                    Runtime Data Areas                         |
|                                                               |
|  +------------------+    +-----------------+                  |
|  | Method Area      |    | Heap            |                  |
|  | (Class metadata, |    | (Objects)       |                  |
|  |  bytecode)       |    |                 |                  |
|  +------------------+    +-----------------+                  |
|                                                               |
|  +------------------+    +-----------------+                  |
|  | JVM Stack        |    | Native Stack    |                  |
|  | (method frames)  |    | (C/C++ code)    |                  |
|  +------------------+    +-----------------+                  |
|                                                               |
|  +------------------+                                        |
|  | PC Register      |                                        |
|  +------------------+                                        |
+---------------------------------------------------------------+

                +-----------------------+
                |   Execution Engine    |
                | (Interpreter + JIT)   |
                +-----------------------+

                +-----------------------+
                |     GC (Garbage)      |
                |     Collector         |
                +-----------------------+
```

---

# 3. JVM Memory Areas

## 3.1 **Method Area**
Stores:
- Class bytecode  
- Field info  
- Method info  
- Static variables  
- Constant Pool  

## 3.2 **Heap**
Largest memory area; stores:
- Objects  
- Arrays  
- Instance variables  

Divided into:
- Young Generation  
- Old Generation  

## 3.3 **Stack**
Each thread has its own stack:
- Stores frames  
- Local variables  
- Method calls  

## 3.4 **PC Register**
Holds address of current instruction.

## 3.5 **Native Method Stack**
Used for JNI (C/C++ code).

---

# 4. JVM Execution Engine

## Interpreter
Executes bytecode line-by-line (slow).

## JIT (Just-In-Time Compiler)
Compiles frequently executed code → machine code (fast).

---

# 5. Java Memory Model (JMM)

Defines:
- How threads share variables  
- Happens-before relationship  
- Atomicity, visibility, ordering  

### Visibility problem example:
```java
boolean running = true;

void run() {
    while (running) {}  // may never stop without volatile
}
```

Fix:
```java
volatile boolean running = true;
```

---

# 6. Garbage Collection (GC)

GC automatically removes unused objects.

### Benefits:
- No manual memory free  
- Fewer memory leaks  

---

# 7. GC Generations

## Young Generation
- Newly created objects  
- Minor GC  

Divided into:
- Eden  
- Survivor S1  
- Survivor S2  

## Old Generation
- Long-lived objects  
- Major GC  

## Permanent Generation (Java 7 and below)
- Class metadata  

Java 8+ → **Metaspace**

---

# 8. Common Garbage Collectors

| GC | Description |
|----|-------------|
| Serial GC | Single-threaded, simple |
| Parallel GC | Multi-threaded, faster |
| CMS | Low pause, deprecated |
| G1 GC | Default GC (Java 9+), balanced |
| ZGC | Ultra-low pause |
| Shenandoah | Low pause, open-source |

---

# 9. Forcing GC (Not recommended)
```java
System.gc();
```

---

# 10. Memory Leaks in Java (Yes, they happen!)

Examples:
- Static collections holding objects  
- Unclosed streams  
- ThreadLocal misuse  

---

# 11. Tools for JVM Monitoring

## JDK tools:
- **jconsole**
- **jvisualvm**
- **jmap**
- **jstack**
- **jprofiler** (3rd‑party)

Example:
```
jmap -heap <pid>
```

---

# 12. Example: OutOfMemoryError

### Heap space error:
```java
List<Integer> list = new ArrayList<>();
while (true) list.add(1);  // Heap fills
```

### Fix:
Increase heap size:
```
java -Xmx1024m Main
```

---

# 13. JVM Parameters (Tuning)

### Heap sizing
```
-Xms512m   (initial heap)
-Xmx2g     (max heap)
```

### GC tuning
```
-XX:+UseG1GC
-XX:+UseZGC
```

### Enable GC logs
```
-Xlog:gc*
```

---

# End of Section 26
