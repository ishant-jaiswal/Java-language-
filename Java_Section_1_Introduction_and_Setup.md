# Java Deep Guide --- Section 1

## Introduction & Setup (Deep Explanation)

------------------------------------------------------------------------

## 1.1 What is Java?

Java is a **high‑level, object‑oriented, platform‑independent**
programming language created by Sun Microsystems (now Oracle).\
It follows the principle **WORA --- Write Once, Run Anywhere**, enabled
by the **Java Virtual Machine (JVM)**.

### Key Characteristics

-   **Platform‑Independent** → Code runs on any device with a JVM\
-   **Object-Oriented** → Everything revolves around classes & objects\
-   **Robust** → Strong memory management, exception handling, type
    safety\
-   **Secure** → Sandboxing, bytecode verification\
-   **Multi-threaded** → Built-in support for parallel programming\
-   **Rich Standard Library** → IO, Collections, Networking, Utilities

------------------------------------------------------------------------

## 1.2 Java Architecture (Deep Explanation)

Java code passes through three main stages:

    Java Source Code (.java)
            ↓
    Java Compiler (javac) → Bytecode (.class)
            ↓
    Java Virtual Machine (JVM) executes bytecode

### ✔ JDK (Java Development Kit)

Contains: - javac (compiler) - java (JVM launcher) - javadoc - debugging
tools - standard library (rt.jar or modules)

### ✔ JRE (Java Runtime Environment)

Contains: - JVM - Core libraries\
**No compiler.** Used only to *run* Java code.

### ✔ JVM (Java Virtual Machine)

Responsible for: - Loading bytecode\
- JIT compilation\
- Memory management\
- Garbage collection

------------------------------------------------------------------------

## 1.3 Installing Java

### Step 1: Download JDK

Use Oracle JDK or OpenJDK (recommended LTS versions: 11, 17, 21).

### Step 2: Set JAVA_HOME (Windows / Mac / Linux)

Example (Windows PowerShell):

    setx JAVA_HOME "C:\Program Files\Java\jdk-21"

### Step 3: Verify Installation

    java -version
    javac -version

------------------------------------------------------------------------

## 1.4 Your First Java Program (Deep Explanation)

Below is the classic **Hello World** program:

``` java
public class Hello {
    public static void main(String[] args) {
        System.out.println("Hello, Java!");
    }
}
```

### Breakdown:

  -------------------------------------------------------------------------------------
  Line                                       Meaning
  ------------------------------------------ ------------------------------------------
  `public class Hello`                       Declares a class named *Hello*

  `public static void main(String[] args)`   Entry point for any Java program

  `System.out.println(...)`                  Prints output to console
  -------------------------------------------------------------------------------------

------------------------------------------------------------------------

## 1.5 Compiling & Running Java Code

### Step 1 --- Save as:

    Hello.java

### Step 2 --- Compile:

    javac Hello.java

This creates:

    Hello.class (bytecode)

### Step 3 --- Run:

    java Hello

### Output:

    Hello, Java!

------------------------------------------------------------------------

## 1.6 How JVM Executes Bytecode (Deep Explanation)

1.  ClassLoader loads `.class` file\
2.  Bytecode Verification checks for illegal instructions\
3.  Interpreter converts bytecode → machine instructions\
4.  JIT (Just-In-Time Compiler) optimizes hot code\
5.  Garbage Collector automatically frees unused memory

------------------------------------------------------------------------

## 1.7 Advantages & Disadvantages of Java

### ✔ Advantages

-   Platform‑independent\
-   Large ecosystem & community\
-   Strong memory management\
-   Powerful libraries (Collections, Streams, Concurrency)\
-   Stable for enterprise applications

### ✖ Disadvantages

-   Verbose syntax\
-   Slower than C/C++ in low-level tasks\
-   High memory usage due to JVM overhead

------------------------------------------------------------------------

## 1.8 Summary of Section 1

You learned: - What Java is\
- Java architecture (JDK, JRE, JVM)\
- How Java runs code using bytecode\
- How to install Java\
- Your first Java program\
- How compilation & execution works\
- JVM internals at a beginner-friendly level

------------------------------------------------------------------------


