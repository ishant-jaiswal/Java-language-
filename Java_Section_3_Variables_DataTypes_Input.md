# Java – Section 3  
## Variables, Data Types & User Input (Deep Explanation)

---

# 📌 1. What Are Variables?

A **variable** is a container in memory used to store data that can change during program execution.

### ✔ Key Rules for Naming Variables
- Must start with a **letter**, `$`, or `_`
- Cannot start with a number  
- Cannot use reserved Java keywords (like `class`, `int`, etc.)
- Use camelCase for naming → `studentName`

### ✔ Example:
```java
int age = 22;
String name = "Ishant";
double salary = 35000.50;
```

---

# 📌 2. Data Types in Java

Java has **two types** of data types:

---

# 🔹 A. Primitive Data Types (8 Types)

| Type      | Size     | Example       | Description |
|-----------|----------|----------------|-------------|
| byte      | 1 byte   | 127            | Small integers |
| short     | 2 bytes  | 32767          | Medium integers |
| int       | 4 bytes  | 1,000,000      | Default integer |
| long      | 8 bytes  | 922337...      | Very large integers |
| float     | 4 bytes  | 3.14f          | Decimal values |
| double    | 8 bytes  | 99.99          | More precise decimals |
| char      | 2 bytes  | 'A'            | Single character |
| boolean   | 1 bit    | true/false     | Logical values |

---

## ✔ Example: Using All Primitive Types

```java
public class PrimitiveExample {
    public static void main(String[] args) {
        byte b = 100;
        short s = 20000;
        int i = 500000;
        long l = 999999999L;
        float f = 5.75f;
        double d = 19.99;
        char c = 'A';
        boolean isJavaFun = true;

        System.out.println(b);
        System.out.println(s);
        System.out.println(i);
        System.out.println(l);
        System.out.println(f);
        System.out.println(d);
        System.out.println(c);
        System.out.println(isJavaFun);
    }
}
```

---

# 🔹 B. Non‑Primitive Data Types

| Type | Example | Description |
|------|---------|-------------|
| String | `"Hello"` | Sequence of characters |
| Arrays | `{1,2,3}` | Stores multiple values |
| Classes | `new Student()` | User-defined type |
| Interfaces | `Runnable` | Abstract type |

## Example:

```java
String name = "ChatGPT";
int[] marks = {90, 85, 88};
```

---

# 📌 3. Type Casting (Converting One Type to Another)

## 🔹 Widening Casting (Automatic)
`byte → short → int → long → float → double`

```java
int num = 10;
double converted = num;  // Automatic
System.out.println(converted);
```

---

## 🔹 Narrowing Casting (Manual)
Requires explicit conversion.

```java
double val = 12.99;
int num = (int) val;  // Manual
System.out.println(num);  // Output: 12
```

---

# 📌 4. Constants (`final` keyword)

Variables whose value **cannot be changed**.

```java
final int SPEED_LIMIT = 80;
```

---

# 📌 5. Taking User Input in Java

Java uses the **Scanner** class to take input.

### 🔹 Step 1: Import Scanner
```java
import java.util.Scanner;
```

### 🔹 Step 2: Create Scanner Object
```java
Scanner sc = new Scanner(System.in);
```

---

## ✔ Example 1: Taking String & Integer Input

```java
import java.util.Scanner;

public class InputExample {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.print("Enter your name: ");
        String name = sc.nextLine();

        System.out.print("Enter your age: ");
        int age = sc.nextInt();

        System.out.println("Name: " + name);
        System.out.println("Age: " + age);
    }
}
```

---

## ✔ Example 2: Taking Float & Double Input

```java
Scanner sc = new Scanner(System.in);

System.out.print("Enter height: ");
float height = sc.nextFloat();

System.out.print("Enter salary: ");
double salary = sc.nextDouble();

System.out.println("Height: " + height);
System.out.println("Salary: " + salary);
```

---

# 📌 6. ASCII Values in Java

Every character has a numeric ASCII value.

### ✔ Example:
```java
char ch = 'A';
int ascii = (int) ch;

System.out.println("ASCII of A = " + ascii);
```

---

# 📌 7. Summary (Easy Revision)

- Java has **variables** to store data  
- **8 primitive types** are basic data  
- **Strings & Arrays** are non‑primitive  
- **Scanner** is used for input  
- **Type casting** helps convert data  
- **final** keyword is used for constants  
- **Characters have ASCII values**

---

# 🎉 What's Next?

When you say **Next Section**, I will generate:

## **Section 4 — Operators in Java (Full Deep Explanation + Examples)**

