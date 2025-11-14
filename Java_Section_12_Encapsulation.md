
# Section 12 — Encapsulation in Java  
Deep Explanation + Code Examples

---

## 1. What is Encapsulation?

Encapsulation is the process of **binding data (variables) and methods (functions)** into a single unit and restricting direct access to the data.

It protects data from unauthorized access.

### Encapsulation Achieved Using:
1. **Private Variables**
2. **Public Getters and Setters**
3. **Access Modifiers**

---

# 2. Why Encapsulation?

✔ Protects data (security)  
✔ Controls how data is accessed  
✔ Improves maintainability  
✔ Increases flexibility  

Example in real life:  
- A bank account hides its internal balance and exposes only deposit/withdraw methods.

---

# 3. Basic Encapsulation Example

```java
class Student {
    private String name;  // private data
    private int age;

    // Getter
    public String getName() {
        return name;
    }

    // Setter
    public void setName(String name) {
        this.name = name;
    }

    public int getAge() { 
        return age; 
    }

    public void setAge(int age) {
        if(age > 0)
            this.age = age;
    }
}

public class Main {
    public static void main(String[] args) {
        Student s = new Student();
        s.setName("John");
        s.setAge(21);

        System.out.println(s.getName());
        System.out.println(s.getAge());
    }
}
```

---

# 4. Access Modifiers in Java

| Modifier | Class | Package | Subclass | World |
|---------|-------|----------|----------|--------|
| **public** | ✔ | ✔ | ✔ | ✔ |
| **protected** | ✔ | ✔ | ✔ | ✖ |
| **default** (no keyword) | ✔ | ✔ | ✖ | ✖ |
| **private** | ✔ | ✖ | ✖ | ✖ |

---

# 5. Detailed Explanation of Access Modifiers

### 5.1 Public
Accessible from anywhere.

```java
public class Test { }
```

### 5.2 Private
Accessible only inside the class.

```java
private int age;
```

### 5.3 Protected
Accessible in same package + subclasses.

```java
protected void show() { }
```

### 5.4 Default (No modifier)
Accessible only within the same package.

```java
void display() { }
```

---

# 6. Encapsulation with Validation Logic

Setters can add business rules.

```java
class Employee {
    private double salary;

    public void setSalary(double salary) {
        if(salary > 0)
            this.salary = salary;
        else
            System.out.println("Invalid Amount!");
    }

    public double getSalary() {
        return salary;
    }
}
```

---

# 7. Read-Only and Write-Only Encapsulation

### Read-Only (Only getter)
```java
class Person {
    private String nationality = "Indian";

    public String getNationality() {
        return nationality;
    }
}
```

### Write-Only (Only setter)
```java
class Person {
    private String password;

    public void setPassword(String password) {
        this.password = password;
    }
}
```

---

# 8. Encapsulation in Real Project Example

```java
class BankAccount {
    private double balance;

    public void deposit(double amount) {
        if(amount > 0)
            balance += amount;
    }

    public void withdraw(double amount) {
        if(amount <= balance)
            balance -= amount;
        else
            System.out.println("Insufficient funds");
    }

    public double getBalance() {
        return balance;
    }
}
```

---

# 9. Encapsulation vs Abstraction

| Feature | Encapsulation | Abstraction |
|---------|----------------|-------------|
| Meaning | Data hiding | Hiding implementation |
| Achieved Using | Getters/Setters | Abstract class, Interface |
| Focus | Protecting data | Exposing essential features |

---

# 10. Key Points Summary

- Encapsulation hides data using **private variables**.
- Access is given through **getters and setters**.
- Ensures **security**, **privacy**, and **control**.
- Uses **access modifiers** heavily.

---

