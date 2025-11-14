# Java – Section 5  
## Control Flow Statements (Deep Explanation + Examples)

---

# 📌 1. What Are Control Flow Statements?

Control flow statements decide **how the program executes** based on conditions or repeated actions.

Java has 3 main categories:

1. **Decision-Making Statements**  
   - if  
   - if-else  
   - else-if  
   - switch  

2. **Looping Statements**  
   - for  
   - while  
   - do-while  

3. **Jump Statements**  
   - break  
   - continue  
   - return  

---

# 📌 2. IF Statement (Decision Making)

### ✔ Syntax:
```java
if (condition) {
    // code
}
```

### ✔ Example:
```java
int age = 20;

if (age >= 18) {
    System.out.println("You can vote.");
}
```

---

# 📌 3. IF–ELSE Statement

```java
if (condition) {
    // true block
} else {
    // false block
}
```

### ✔ Example:
```java
int marks = 45;

if (marks >= 50) {
    System.out.println("Pass");
} else {
    System.out.println("Fail");
}
```

---

# 📌 4. ELSE–IF Ladder

Used when you have multiple conditions.

### ✔ Example:
```java
int score = 85;

if (score >= 90) {
    System.out.println("A");
} else if (score >= 80) {
    System.out.println("B");
} else if (score >= 70) {
    System.out.println("C");
} else {
    System.out.println("D");
}
```

---

# 📌 5. SWITCH Statement

Switch is used when checking **fixed values**.

### ✔ Syntax:
```java
switch(value) {
    case 1: 
        break;
    case 2: 
        break;
    default:
}
```

### ✔ Example:
```java
int day = 3;

switch(day) {
    case 1: System.out.println("Monday"); break;
    case 2: System.out.println("Tuesday"); break;
    case 3: System.out.println("Wednesday"); break;
    default: System.out.println("Invalid day");
}
```

---

# 📌 6. LOOPS in Java

Loops execute code repeatedly.

---

# 🔹 A. FOR LOOP

### ✔ Syntax:
```java
for(initialization; condition; update){
    // code
}
```

### ✔ Example:
```java
for (int i = 1; i <= 5; i++) {
    System.out.println(i);
}
```

---

# 🔹 B. WHILE LOOP

Used when number of iterations is unknown.

### ✔ Example:
```java
int i = 1;

while (i <= 5) {
    System.out.println(i);
    i++;
}
```

---

# 🔹 C. DO-WHILE LOOP

Executes at least **one time** even if condition is false.

### ✔ Example:
```java
int i = 1;

do {
    System.out.println(i);
    i++;
} while (i <= 5);
```

---

# 📌 7. Enhanced FOR LOOP (For-Each)

Used for arrays.

### ✔ Example:
```java
int[] nums = {10, 20, 30};

for (int n : nums) {
    System.out.println(n);
}
```

---

# 📌 8. Jump Statements

---

# 🔹 A. BREAK

Stops the loop.

### ✔ Example:
```java
for (int i = 1; i <= 10; i++) {
    if (i == 5) break;
    System.out.println(i);
}
```

---

# 🔹 B. CONTINUE

Skips current iteration.

### ✔ Example:
```java
for (int i = 1; i <= 5; i++) {
    if (i == 3) continue;
    System.out.println(i);
}
```

---

# 🔹 C. RETURN

Ends a method.

```java
return value;
```

---

# 📌 9. Nested Loops

### ✔ Example:
```java
for(int i = 1; i <= 3; i++){
    for(int j = 1; j <= 3; j++){
        System.out.println(i + " " + j);
    }
}
```

---

# 📌 10. Summary

You learned:

- if, else-if, switch  
- for, while, do-while  
- for-each loop  
- break, continue, return  
- nested loops  

This is one of the most important chapters for logic building.

---


