# Java Section 28 — Testing (JUnit Example)

## 1. Introduction to Testing
Testing ensures code works as expected, reduces bugs, and improves maintainability.  
Java’s most popular testing framework is **JUnit 5**.

---

## 2. Setting up JUnit 5

### If using Maven:
Add this to your `pom.xml`:
```xml
<dependency>
    <groupId>org.junit.jupiter</groupId>
    <artifactId>junit-jupiter</artifactId>
    <version>5.10.0</version>
    <scope>test</scope>
</dependency>
```

### If using Gradle:
```gradle
testImplementation 'org.junit.jupiter:junit-jupiter:5.10.0'

test {
    useJUnitPlatform()
}
```

---

## 3. JUnit Test Structure

A typical JUnit test file looks like:

```java
import org.junit.jupiter.api.Test;
import static org.junit.jupiter.api.Assertions.*;

public class CalculatorTest {

    @Test
    void testAddition() {
        Calculator c = new Calculator();
        assertEquals(5, c.add(2, 3));
    }
}
```

---

## 4. Example: Class Under Test

```java
public class Calculator {

    public int add(int a, int b) {
        return a + b;
    }

    public int divide(int a, int b) {
        if(b == 0) throw new IllegalArgumentException("Cannot divide by zero");
        return a / b;
    }
}
```

---

## 5. Example Test Cases

### ✔ Test addition
```java
@Test
void testAdd() {
    Calculator c = new Calculator();
    assertEquals(10, c.add(7, 3));
}
```

### ✔ Test division
```java
@Test
void testDivide() {
    Calculator c = new Calculator();
    assertEquals(5, c.divide(10, 2));
}
```

### ✔ Test exception
```java
@Test
void testDivideByZero() {
    Calculator c = new Calculator();
    assertThrows(IllegalArgumentException.class, () -> c.divide(10, 0));
}
```

---

## 6. Assertions Overview

| Assertion | Purpose |
|----------|---------|
| `assertEquals(a, b)` | Checks equality |
| `assertNotEquals(a, b)` | Ensures values differ |
| `assertTrue(condition)` | Condition must be true |
| `assertFalse(condition)` | Condition must be false |
| `assertThrows()` | Verify exception thrown |

---

## 7. BeforeEach & AfterEach

Used to run code before/after each test:
```java
@BeforeEach
void init() {
    calculator = new Calculator();
}

@AfterEach
void cleanup() {
    calculator = null;
}
```

---

## 8. Parameterized Tests

Allows providing multiple inputs:
```java
@ParameterizedTest
@ValueSource(ints = {1, 2, 3, 4})
void testIsEven(int number) {
    assertTrue(number > 0);
}
```

---

## 9. Test Suites

Group multiple test classes:

```java
@RunWith(JUnitPlatform.class)
@SelectPackages("com.myapp.tests")
public class TestSuite {}
```

---

## 10. Mockito Introduction (Optional)

Mockito is used for mocking dependencies.

Example:
```java
CalculatorService service = mock(CalculatorService.class);

when(service.add(2, 3)).thenReturn(5);
```

---

## 11. Running Tests

### Maven:
```
mvn test
```

### Gradle:
```
gradle test
```

### IDE:
- IntelliJ: Right-click → Run Test
- VS Code: Click on test icons
- Eclipse: Run As → JUnit Test

---


