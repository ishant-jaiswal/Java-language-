# Java Section 25 — Modules (JPMS) & Classpath

## 1. Introduction to JPMS (Java Platform Module System)
JPMS was introduced in **Java 9** to provide:
- Better encapsulation  
- Reliable configuration  
- Faster startup  
- Strong dependencies between modules  

A **module** is a group of packages with a `module-info.java` descriptor.

---

## 2. Basic Module Structure

A module contains:
```
src/
 └── mymodule/
      ├── module-info.java
      └── mypkg/
           └── Main.java
```

### module-info.java
```java
module mymodule {
    exports mypkg;
}
```

---

## 3. Creating a Simple Java Module

### module-info.java
```java
module greetings {
    exports com.greet;
}
```

### Main class
```java
package com.greet;

public class Hello {
    public static void sayHi() {
        System.out.println("Hello from module!");
    }
}
```

---

## 4. Requiring Another Module

```java
module consumer {
    requires greetings;
}
```

---

## 5. Compiling a Module (Command Line)

### Compile:
```
javac -d out --module-source-path src $(find src -name "*.java")
```

### Run:
```
java --module-path out -m mymodule/mypkg.Main
```

---

## 6. Exporting & Opening Packages

### exports
Allows other modules to use classes inside the package.

### opens
Allows reflection access (used by Hibernate, Spring).

```java
module mymodule {
    exports com.api;
    opens com.internal to spring.core;
}
```

---

## 7. Services in JPMS

### Providing a Service
```java
module provider {
    provides my.api.Service with my.impl.MyServiceImpl;
}
```

### Consuming a Service
```java
module consumer {
    uses my.api.Service;
}
```

---

# CLASS LOADING & CLASSPATH

## 8. What is the Classpath?
Classpath tells JVM **where to look** for classes or packages.

### Set classpath manually:
```
java -cp .:lib/mysql.jar Main
```

Windows:
```
java -cp .;lib/mysql.jar Main
```

---

## 9. Loading Classes Dynamically
```java
Class<?> cls = Class.forName("com.test.Demo");
Object obj = cls.getDeclaredConstructor().newInstance();
```

---

## 10. Types of Class Loaders

| Loader | Description |
|--------|-------------|
| Bootstrap ClassLoader | Loads core Java classes |
| Extension (Platform) CL | Loads extension libs |
| Application CL | Loads classes from classpath |

---

## 11. Difference: Classpath vs Module-path

| Feature | Classpath | Module-path |
|---------|-----------|--------------|
| Introduced | Java 1 | Java 9 |
| Dependency check | No | Yes |
| Encapsulation | None | Strong |
| Performance | Slower | Faster |
| IDE Use | Common | Modern projects |

---

## 12. When to Use Modules
Use JPMS when:
- Building large applications  
- Need strong encapsulation  
- Building libraries for distribution  

Avoid modules when:
- Using Spring or Hibernate (complex module configs)  
- Small projects  

---

## End of Section 25
