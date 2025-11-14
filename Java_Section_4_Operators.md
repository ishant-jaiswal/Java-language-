# Java – Section 4  
## Operators in Java (Deep Explanation + Examples)

---

# 📌 1. What Are Operators?

Operators are special symbols used to perform operations on variables and values.

Example:
```java
int a = 10 + 20;  // "+" is an operator
```

Java Operators are divided into these categories:

1. Arithmetic Operators  
2. Assignment Operators  
3. Relational (Comparison) Operators  
4. Logical Operators  
5. Unary Operators  
6. Bitwise Operators  
7. Ternary Operator  
8. Shift Operators  

---

# 📌 2. Arithmetic Operators

These operators perform mathematical operations.

| Operator | Meaning | Example |
|----------|----------|----------|
| + | Addition | a + b |
| - | Subtraction | a - b |
| * | Multiplication | a * b |
| / | Division | a / b |
| % | Modulus (remainder) | a % b |

### ✔ Example:
```java
public class ArithmeticDemo {
    public static void main(String[] args) {
        int a = 20, b = 6;

        System.out.println(a + b); // 26
        System.out.println(a - b); // 14
        System.out.println(a * b); // 120
        System.out.println(a / b); // 3
        System.out.println(a % b); // 2
    }
}
```

---

# 📌 3. Assignment Operators

Used to assign values to variables.

| Operator | Meaning | Example |
|----------|----------|----------|
| = | Assign | x = 10 |
| += | Add and assign | x += 5 |
| -= | Subtract and assign | x -= 5 |
| *= | Multiply and assign | x *= 4 |
| /= | Divide and assign | x /= 2 |
| %= | Modulus and assign | x %= 3 |

### ✔ Example:
```java
int x = 10;
x += 5;  // x = 15
x *= 2;  // x = 30
```

---

# 📌 4. Relational (Comparison) Operators

Used to compare values. Always returns **true** or **false**.

| Operator | Meaning |
|----------|----------|
| == | Equal to |
| != | Not equal to |
| > | Greater than |
| < | Less than |
| >= | Greater than or equal |
| <= | Less than or equal |

### ✔ Example:
```java
int a = 10, b = 20;
System.out.println(a > b);   // false
System.out.println(a < b);   // true
System.out.println(a == 10); // true
```

---

# 📌 5. Logical Operators

Used for combining conditions.

| Operator | Meaning | Description |
|----------|----------|-------------|
| && | Logical AND | true if both true |
| \|\| | Logical OR | true if one is true |
| ! | Logical NOT | Inverts boolean value |

### ✔ Example:
```java
int age = 25;
boolean hasID = true;

if(age > 18 && hasID){
    System.out.println("Allowed");
}
```

---

# 📌 6. Unary Operators

Unary operators work on a single variable.

| Operator | Meaning |
|----------|----------|
| ++ | Increment |
| -- | Decrement |
| + | Unary plus |
| - | Unary minus |
| ! | Logical NOT |

### ✔ Example:
```java
int x = 5;
System.out.println(++x); // 6 (pre-increment)
System.out.println(x++); // 6 printed, then x becomes 7
```

---

# 📌 7. Bitwise Operators

Works at the bit level.

| Operator | Meaning |
|----------|----------|
| & | AND |
| \| | OR |
| ^ | XOR |
| ~ | NOT |

### ✔ Example:
```java
int a = 5;   // 0101
int b = 3;   // 0011

System.out.println(a & b); // 1 (0001)
System.out.println(a | b); // 7 (0111)
System.out.println(a ^ b); // 6 (0110)
```

---

# 📌 8. Shift Operators

| Operator | Meaning |
|----------|----------|
| << | Left shift |
| >> | Right shift |
| >>> | Unsigned right shift |

### ✔ Example:
```java
int x = 8; // 1000
System.out.println(x << 1); // 16 (10000)
System.out.println(x >> 1); // 4 (0100)
```

---

# 📌 9. Ternary Operator

Shortcut for `if-else`.

### Syntax:
```java
variable = (condition) ? value_if_true : value_if_false;
```

### ✔ Example:
```java
int age = 20;
String result = (age >= 18) ? "Adult" : "Minor";

System.out.println(result);
```

---

# 📌 10. Summary

- Arithmetic → +, -, *, /, %  
- Assignment → =, +=, -=, etc.  
- Relational → ==, !=, >, < …  
- Logical → &&, ||, !  
- Unary → ++, --, !  
- Bitwise → &, |, ^, ~  
- Shift → <<, >>, >>>  
- Ternary → (condition ? value1 : value2)

---

# 🎉 Next Step

When you say **Next Section**, I will generate:

## **Section 5 — Control Flow Statements (if, else, switch, loops) in a new `.md` file**  
