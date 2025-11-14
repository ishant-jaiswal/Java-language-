# Java Section 22 — Annotations & Reflection

## 1. Introduction
Annotations and Reflection are powerful features in Java used for:
- Metadata
- Framework development (Spring, Hibernate)
- Runtime inspection of classes, methods, fields
- Custom behaviors using custom annotations

---

# 2. Annotations in Java

Annotations provide metadata that does not affect program logic but is used by compilers and frameworks.

### Built-in Annotations
- `@Override`
- `@Deprecated`
- `@SuppressWarnings`

### Example:
```java
class Parent {
    void show() {}
}

class Child extends Parent {
    @Override
    void show() {  // Ensures correct method override
        System.out.println("Child show");
    }
}
```

---

# 3. Creating Custom Annotations

### Define Annotation
```java
@interface MyAnnotation {
    String value();
    int count() default 1;
}
```

### Use Annotation
```java
@MyAnnotation(value = "Test", count = 5)
class Demo {}
```

---

# 4. Meta-Annotations
Annotations used to describe other annotations.

| Meta-Annotation | Purpose |
|----------------|----------|
| `@Retention` | How long annotation is retained |
| `@Target` | Where annotation can be used |
| `@Inherited` | Inherited by subclasses |
| `@Documented` | Included in Javadoc |

### Example:
```java
import java.lang.annotation.*;

@Retention(RetentionPolicy.RUNTIME)
@Target(ElementType.METHOD)
@interface RunTest {}
```

---

# 5. Reflection API

Java Reflection allows inspection of:
- Classes
- Methods
- Fields
- Constructors
- Annotations

### Getting Class Object
```java
Class<?> cls = Class.forName("java.util.ArrayList");
```

### List all methods
```java
for (var m : cls.getDeclaredMethods()) {
    System.out.println(m.getName());
}
```

---

# 6. Accessing Fields via Reflection
```java
class Person {
    private String name = "Ishant";
}

public class Main {
    public static void main(String[] args) throws Exception {
        Person p = new Person();
        Class<?> cls = p.getClass();

        var field = cls.getDeclaredField("name");
        field.setAccessible(true);

        System.out.println(field.get(p)); // Ishant
    }
}
```

---

# 7. Invoking Methods Dynamically
```java
class Demo {
    public void greet() {
        System.out.println("Hello!");
    }
}

public class Main {
    public static void main(String[] args) throws Exception {
        Demo d = new Demo();
        Method m = d.getClass().getMethod("greet");
        m.invoke(d);
    }
}
```

---

# 8. Reading Annotation Values Using Reflection

```java
@Retention(RetentionPolicy.RUNTIME)
@Target(ElementType.TYPE)
@interface Info {
    String author();
    String version();
}

@Info(author="Ishant", version="1.0")
class Product {}

public class Main {
    public static void main(String[] args) {
        Class<Product> obj = Product.class;

        Info info = obj.getAnnotation(Info.class);
        System.out.println(info.author());
        System.out.println(info.version());
    }
}
```

---

# 9. Real-World Use Cases

### 1. **Spring Framework**
- `@Autowired`
- `@Component`
- Uses reflection for dependency injection.

### 2. **Hibernate**
- `@Entity`, `@Id`
- Reflection maps Java classes to database tables.

### 3. **JUnit**
- `@Test`
- Reflection detects and runs test methods.

---

# 10. Advantages of Annotations & Reflection
- Flexible metadata
- Enables framework creation
- Reduces boilerplate
- Runtime dynamic behavior

---

# 11. Disadvantages
- Reflection is slow compared to direct access
- Can break encapsulation
- Harder to debug

---

# End of Section 22
