# Java Deep Guide --- Section 2

## Basic Syntax (Deep Explanation)

------------------------------------------------------------------------

## 2.1 Java Program Structure

A typical Java program consists of:

``` java
// 1. Package declaration (optional)
package com.example;

// 2. Imports (optional)
import java.util.Scanner;

// 3. Class declaration
public class MyClass {

    // 4. Main method — program entry point
    public static void main(String[] args) {
        System.out.println("Hello Syntax!");
    }
}
```

### Breakdown

  Part        Meaning
  ----------- ----------------------------------------------
  `package`   Organizes classes into folders/namespaces
  `import`    Allows using classes from other packages
  `class`     Blueprint for creating objects
  `main()`    Entry point executed when the program starts

------------------------------------------------------------------------

## 2.2 Java Identifiers (Deep Explanation)

Identifiers are names given to variables, classes, methods, etc.

### Rules:

-   Must start with **letter**, \*\*underscore (\_)**, or **\$\*\*
-   Cannot start with a number\
-   Case-sensitive\
-   Cannot use Java keywords

### Valid examples:

    myVar
    number1
    _total
    $price

### Invalid examples:

    1value   (starts with number)
    class    (keyword)
    my-var   (hyphen not allowed)

------------------------------------------------------------------------

## 2.3 Variables and Data Types (High Clarity)

Java is **statically typed**, meaning you must declare the type before
using variables.

``` java
int age = 25;
double price = 99.99;
char grade = 'A';
boolean pass = true;
```

### Primitive Types

  Type      Size     Example
  --------- -------- ------------
  byte      1 byte   127
  short     2 byte   10000
  int       4 byte   10
  long      8 byte   999999L
  float     4 byte   12.5f
  double    8 byte   12.5
  char      2 byte   'A'
  boolean   1 bit    true/false

------------------------------------------------------------------------

## 2.4 Comments in Java

### Single-line:

``` java
// This is a comment
```

### Multi-line:

``` java
/*
This is a
multi-line comment
*/
```

### Documentation comments:

``` java
/**
 * This method prints a message.
 */
```

------------------------------------------------------------------------

## 2.5 Java Statements (Deep Explanation)

A statement ends with a semicolon.

``` java
int x = 10;
x = x + 5;
System.out.println(x);
```

------------------------------------------------------------------------

## 2.6 Blocks & Scope

A block `{ ... }` creates a new scope.

``` java
{
    int x = 20;
    System.out.println(x);
}
```

Variables inside a block are not accessible outside it.

------------------------------------------------------------------------

## 2.7 Input in Java (Scanner)

To get keyboard input:

``` java
import java.util.Scanner;

public class InputDemo {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        System.out.print("Enter your name: ");
        String name = sc.nextLine();
        System.out.println("Hello " + name);
    }
}
```

------------------------------------------------------------------------

## 2.8 Output in Java

### Print without newline

``` java
System.out.print("Hello ");
```

### Print with newline

``` java
System.out.println("World");
```

### Formatted output

``` java
System.out.printf("Age: %d", 25);
```

------------------------------------------------------------------------

## 2.9 Keywords in Java (Exhaustive List)

Java has **67 keywords**, including:

    class, public, static, void, int, double, boolean, if, else,
    switch, case, break, continue, for, while, do, return,
    try, catch, finally, throw, throws, new, this, super,
    implements, extends, interface, package, import, synchronized,
    volatile, enum, final, const, goto (reserved), private, protected

------------------------------------------------------------------------

## 2.10 Coding Style (Professional Tips)

### Naming conventions:

-   Classes → `PascalCase`\
-   Variables & methods → `camelCase`\
-   Constants → `UPPER_SNAKE_CASE`

### Example:

``` java
public class StudentRecord {
    private int studentId;
}
```

------------------------------------------------------------------------

## 2.11 Full Example Combining All Syntax

``` java
package demo;

import java.util.Scanner;

/**
 * Basic Syntax Example
 */
public class SyntaxDemo {

    public static void main(String[] args) {

        // Input
        Scanner sc = new Scanner(System.in);

        // Variable
        System.out.print("Enter a number: ");
        int num = sc.nextInt();

        // Output
        System.out.println("You entered: " + num);
    }
}
```

------------------------------------------------------------------------

## 2.12 Summary of Section 2

You learned: - Java program structure - Identifiers & keywords -
Variables and data types - Comments, statements, scope - Input/output
basics - Coding style used in professional Java development

------------------------------------------------------------------------


