# Java Section 16 — Java Standard Library Essentials  
The Java Standard Library is a powerful collection of built‑in classes that help developers perform everyday tasks such as working with strings, numbers, math operations, date/time, and more.

This section covers the most important core classes every Java developer must know.

---

# **1. String Class**
Strings are immutable sequences of characters stored in `java.lang.String`.

---

## **1.1 Creating Strings**
```java
String s1 = "Hello";
String s2 = new String("World");
```

---

## **1.2 Common String Methods**

```java
String s = "Java Programming";

s.length();            // number of characters
s.toUpperCase();       // convert to upper case
s.toLowerCase();       // convert to lower case
s.charAt(2);           // index 2 character
s.substring(5);        // substring from index 5
s.substring(0, 4);     // "Java"
s.contains("Pro");     // true
s.equals("Java");      // false
s.replace("Java", "C++"); 
```

---

## **1.3 StringBuilder and StringBuffer**
Used when modifying text multiple times (mutable).

```java
StringBuilder sb = new StringBuilder("Hello");
sb.append(" World");
System.out.println(sb);   // Hello World
```

---

# **2. Math Class**
Provides mathematical operations.

---

## **2.1 Common Math Methods**
```java
Math.max(10, 20);      // 20
Math.min(5, 3);        // 3
Math.sqrt(25);         // 5
Math.pow(2, 3);        // 8
Math.abs(-10);         // 10
Math.random();         // 0.0 to 1.0
```

---

# **3. Wrapper Classes**
Primitive → Object types  
Located in `java.lang`

| Primitive | Wrapper |
|----------|----------|
| int      | Integer |
| float    | Float |
| double   | Double |
| char     | Character |
| boolean  | Boolean |

---

## **3.1 Autoboxing**
```java
int a = 10;
Integer obj = a;   // autoboxing
```

## **3.2 Unboxing**
```java
Integer x = 50;
int num = x;   // unboxing
```

---

# **4. Date & Time API (java.time package)**

## **4.1 LocalDate Example**
```java
import java.time.LocalDate;

LocalDate date = LocalDate.now();
System.out.println(date);
```

---

## **4.2 LocalTime Example**
```java
import java.time.LocalTime;

System.out.println(LocalTime.now());
```

---

## **4.3 LocalDateTime Example**
```java
import java.time.LocalDateTime;

System.out.println(LocalDateTime.now());
```

---

## **4.4 Formatting Dates**
```java
import java.time.*;
import java.time.format.*;

LocalDate date = LocalDate.now();
DateTimeFormatter fmt = DateTimeFormatter.ofPattern("dd-MM-yyyy");

System.out.println(date.format(fmt));
```

---

# **5. Random Class**

```java
import java.util.Random;

Random r = new Random();
int n = r.nextInt(100);   // 0–99
double d = r.nextDouble();
boolean b = r.nextBoolean();
```

---

# **6. Arrays Utility Class**

```java
import java.util.Arrays;

int[] arr = {5, 2, 9, 1};
Arrays.sort(arr);
System.out.println(Arrays.toString(arr));
```

---

# **7. Objects Class**
Useful for null‑safe operations.

```java
import java.util.Objects;

Objects.equals("A", "A");  // true
Objects.isNull(null);      // true
```

---

# **8. Key Points Summary**
- `String` is immutable; `StringBuilder` is mutable.  
- Wrapper classes allow primitives to behave like objects.  
- `Math` class gives useful mathematical utilities.  
- Modern date/time API (`java.time`) is far better than old Date.  
- `Arrays` helps with sorting and printing arrays.  
- `Objects` class helps avoid null pointer issues.

---

