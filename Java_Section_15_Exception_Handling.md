# Java Section 15 — Exception Handling

Exception Handling in Java allows programs to manage runtime errors gracefully without crashing.  
It ensures smooth flow even when unexpected events occur.

---

# **1. What is an Exception?**
An **exception** is an event that disrupts normal program execution.

Examples:
- Dividing by zero  
- Accessing array out of bounds  
- File not found  
- Null reference  

---

# **2. Types of Exceptions**
Java categorizes exceptions into:

### **a) Checked Exceptions**  
Checked at compile-time.  
Examples:
- `IOException`
- `SQLException`
- `FileNotFoundException`

You must handle them using **try-catch** or `throws`.

---

### **b) Unchecked Exceptions (Runtime Exceptions)**  
Not checked at compile-time.  
Examples:
- `ArithmeticException`
- `NullPointerException`
- `ArrayIndexOutOfBoundsException`

---

### **c) Errors (Not Exceptions)**  
Critical problems — should not be handled.  
Examples:
- `StackOverflowError`
- `OutOfMemoryError`

---

# **3. Exception Handling Keywords**

| Keyword | Use |
|--------|-----|
| `try` | Wraps code that might throw exception |
| `catch` | Handles exception |
| `finally` | Always executes (cleanup code) |
| `throw` | Manually throw exception |
| `throws` | Declare exceptions in method signature |

---

# **4. try–catch Example**

```java
public class Demo {
    public static void main(String[] args) {
        try {
            int a = 10 / 0;
        } catch (ArithmeticException e) {
            System.out.println("Error: " + e.getMessage());
        }
    }
}
```

**Output:**
```
Error: / by zero
```

---

# **5. Multiple Catch Blocks**

```java
try {
    int[] arr = new int[3];
    System.out.println(arr[5]);
} catch (ArithmeticException e) {
    System.out.println("Math error");
} catch (ArrayIndexOutOfBoundsException e) {
    System.out.println("Index error");
}
```

---

# **6. finally Block**

```java
try {
    System.out.println("Opening file...");
} finally {
    System.out.println("Closing file...");
}
```

Even if an exception occurs, `finally` executes.

---

# **7. throw Keyword Example**

```java
public class Vote {
    static void checkAge(int age) {
        if (age < 18) {
            throw new ArithmeticException("Not eligible to vote");
        }
        System.out.println("Eligible to vote");
    }

    public static void main(String[] args) {
        checkAge(15);
    }
}
```

---

# **8. throws Keyword Example**

```java
import java.io.*;

class Test {
    static void readFile() throws IOException {
        FileReader fr = new FileReader("data.txt");
        fr.read();
    }

    public static void main(String[] args) {
        try {
            readFile();
        } catch (IOException e) {
            System.out.println("File error");
        }
    }
}
```

---

# **9. Custom Exceptions**

You can create your own exception class.

```java
class MyException extends Exception {
    MyException(String message) {
        super(message);
    }
}

public class Test {
    public static void main(String[] args) {
        try {
            throw new MyException("Custom error occurred");
        } catch (MyException e) {
            System.out.println(e.getMessage());
        }
    }
}
```

---

# **10. Best Practices**
- Always catch specific exceptions, not generic ones.
- Use `finally` to release resources (files, DB connections).
- Do NOT swallow exceptions silently.
- Custom exceptions should provide meaningful messages.

---

