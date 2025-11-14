# Java – Section 7  
## Strings in Java (Deep Explanation + Examples)

---

# 📌 1. What Is a String?

A **String** in Java is a sequence of characters enclosed in double quotes.

Example:
```java
String name = "Ishant";
```

In Java, **String is a class** in `java.lang` package.

---

# 📌 2. Strings Are Immutable

In Java:

- **Once a String is created, it cannot be changed.**
- Any modification creates a **new object** in memory.

### ✔ Example:
```java
String s1 = "Hello";
s1 = s1 + " World";  // Creates new String object
```

---

# 📌 3. Creating Strings

### ✔ Method 1 — String Literal
```java
String s1 = "Java";
```

### ✔ Method 2 — Using new Keyword
```java
String s2 = new String("Java");
```

---

# 📌 4. Common String Methods (Most Important)

---

## 🔹 A. `length()`
Returns number of characters.

```java
String s = "Hello";
System.out.println(s.length()); // 5
```

---

## 🔹 B. `charAt()`
Returns character at index.

```java
System.out.println(s.charAt(1)); // 'e'
```

---

## 🔹 C. `substring()`
Extracts portion of string.

```java
String s = "Programming";
System.out.println(s.substring(0, 6)); // Progra
```

---

## 🔹 D. `toUpperCase()` & `toLowerCase()`
```java
"java".toUpperCase(); // JAVA
"HELLO".toLowerCase(); // hello
```

---

## 🔹 E. `equals()` & `equalsIgnoreCase()`
```java
"Java".equals("Java"); // true
"java".equalsIgnoreCase("JAVA"); // true
```

---

## 🔹 F. `contains()`
```java
"Hello World".contains("World"); // true
```

---

## 🔹 G. `startsWith()` and `endsWith()`
```java
"example.txt".endsWith(".txt"); // true
```

---

## 🔹 H. `replace()`
```java
"Java is fun".replace("fun", "powerful"); 
```

---

## 🔹 I. `trim()`
Removes extra spaces.

---

## 🔹 J. `split()`
```java
String s = "a,b,c";
String[] arr = s.split(",");
```

---

# 📌 5. String Comparison

### ❌ Wrong:
```java
if(s1 == s2)
```
(Compares memory addresses)

### ✔ Correct:
```java
if(s1.equals(s2))
```

---

# 📌 6. StringBuilder (Mutable)

- Faster
- Used for modifications
- Not thread-safe

### ✔ Example:
```java
StringBuilder sb = new StringBuilder("Hello");
sb.append(" World");
System.out.println(sb);
```

---

# 📌 7. StringBuffer (Mutable + Thread-safe)

Used in multithreading.

```java
StringBuffer sb = new StringBuffer("Java");
sb.append(" Programming");
```

---

# 📌 8. Converting Between String, StringBuilder, StringBuffer

### ✔ String → StringBuilder
```java
StringBuilder sb = new StringBuilder(str);
```

### ✔ StringBuilder → String
```java
String s = sb.toString();
```

---

# 📌 9. Important String Programs

---

## 🔹 A. Reverse a String
```java
String input = "hello";
String reversed = "";

for(int i = input.length() - 1; i >= 0; i--){
    reversed += input.charAt(i);
}
```

---

## 🔹 B. Count Vowels
```java
int count = 0;
for (char ch : str.toCharArray()) {
    if ("aeiouAEIOU".indexOf(ch) != -1) count++;
}
```

---

## 🔹 C. Check Palindrome
```java
String rev = new StringBuilder(str).reverse().toString();

if(str.equals(rev))
    System.out.println("Palindrome");
```

---

# 📌 10. Summary

You learned:

- String basics & immutability  
- Important methods  
- StringBuilder & StringBuffer  
- String operations and programs  

---

 
