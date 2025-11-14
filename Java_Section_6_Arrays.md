# Java – Section 6  
## Arrays in Java (Deep Explanation + Examples)

---

# 📌 1. What Is an Array?

An **array** is a data structure used to store **multiple values of the same data type** in a single variable.

### ✔ Example:
```java
int[] numbers = {10, 20, 30, 40};
```

---

# 📌 2. Why Use Arrays?

Without arrays:
```java
int a=10, b=20, c=30;
```
Difficult to manage.

With arrays:
```java
int[] arr = {10, 20, 30};
```
Easy to loop, store, and process.

---

# 📌 3. Declaring & Initializing Arrays

### ✔ Method 1 — Direct Initialization
```java
int[] arr = {1, 2, 3, 4};
```

### ✔ Method 2 — Declare then Create
```java
int[] arr;
arr = new int[5]; // default values = 0
```

### ✔ Method 3 — Declare + Create + Initialize
```java
int[] arr = new int[]{10, 20, 30};
```

---

# 📌 4. Accessing Array Elements

```java
System.out.println(arr[0]); // first element
System.out.println(arr[arr.length - 1]); // last element
```

---

# 📌 5. Looping Through Arrays

### ✔ Using for loop
```java
for (int i = 0; i < arr.length; i++) {
    System.out.println(arr[i]);
}
```

### ✔ Using for-each loop
```java
for (int num : arr) {
    System.out.println(num);
}
```

---

# 📌 6. Updating Array Elements

```java
arr[2] = 100;
```

---

# 📌 7. 1D Array Example (Full Program)

```java
public class ArrayExample {
    public static void main(String[] args) {
        int[] nums = {5, 10, 15, 20};

        for (int n : nums) {
            System.out.println(n);
        }
    }
}
```

---

# 📌 8. 2D Arrays (Matrix)

2D array = array of arrays.

### ✔ Declaring a 2D array:
```java
int[][] matrix = new int[3][3];
```

### ✔ Initializing:
```java
int[][] matrix = {
    {1, 2, 3},
    {4, 5, 6},
    {7, 8, 9}
};
```

### ✔ Accessing:
```java
System.out.println(matrix[1][2]); // 6
```

---

# 📌 9. Looping in 2D Arrays

```java
for (int i = 0; i < matrix.length; i++) {
    for (int j = 0; j < matrix[i].length; j++) {
        System.out.print(matrix[i][j] + " ");
    }
    System.out.println();
}
```

---

# 📌 10. Jagged Arrays (Irregular Arrays)

Different rows → different lengths.

### ✔ Example:
```java
int[][] jagged = {
    {1, 2},
    {3, 4, 5},
    {6}
};
```

---

# 📌 11. Common Array Operations

---

## 🔹 A. Finding Max Element
```java
int max = arr[0];
for (int n : arr) {
    if (n > max) max = n;
}
```

---

## 🔹 B. Finding Min Element
```java
int min = arr[0];
for (int n : arr) {
    if (n < min) min = n;
}
```

---

## 🔹 C. Searching an Element (Linear Search)

```java
int key = 20;
boolean found = false;

for (int i = 0; i < arr.length; i++) {
    if (arr[i] == key) {
        found = true;
        break;
    }
}
```

---

## 🔹 D. Sorting Array (Using Arrays.sort)

```java
import java.util.Arrays;

Arrays.sort(arr);
```

---

## 🔹 E. Copying Arrays

### Method 1: Using loop  
```java
int[] copy = new int[arr.length];
for (int i = 0; i < arr.length; i++){
    copy[i] = arr[i];
}
```

### Method 2: Using clone  
```java
int[] copy = arr.clone();
```

### Method 3: Using Arrays.copyOf  
```java
int[] copy = Arrays.copyOf(arr, arr.length);
```

---

# 📌 12. Multidimensional Array Example

```java
public class MatrixExample {
    public static void main(String[] args) {
        int[][] mat = {
            {1, 2},
            {3, 4}
        };

        for (int[] row : mat) {
            for (int val : row) {
                System.out.print(val + " ");
            }
            System.out.println();
        }
    }
}
```

---

# 📌 13. Summary

You learned:

- 1D, 2D, Jagged arrays  
- Accessing, updating, looping  
- Searching and sorting  
- Copying arrays  
- Working with matrices  

This is one of the most important fundamentals.

---

 
