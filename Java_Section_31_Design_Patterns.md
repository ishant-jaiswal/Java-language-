# Java Section 31 — Design Patterns (With Code Examples)

## 1. Introduction
Design patterns provide reusable solutions to common software design problems.  
They make your code cleaner, more flexible, and easier to maintain.

Patterns are grouped into 3 categories:

1. **Creational Patterns** – object creation  
2. **Structural Patterns** – object composition  
3. **Behavioral Patterns** – communication between objects  

This section includes clear explanations + Java examples.

---

# 🟥 PART 1 — CREATIONAL PATTERNS

## 2. Singleton Pattern
Ensures only one instance of a class exists.

### Problem:
- Need one global object (Logger, DB connection).

### Example:
```java
public class Singleton {
    private static Singleton instance;

    private Singleton() {} // private constructor

    public static synchronized Singleton getInstance() {
        if(instance == null) instance = new Singleton();
        return instance;
    }
}
```

Usage:
```java
Singleton s = Singleton.getInstance();
```

---

## 3. Factory Method Pattern
Creates objects without exposing creation logic.

### Example:
```java
interface Shape { void draw(); }

class Circle implements Shape {
    public void draw() { System.out.println("Circle"); }
}

class Rectangle implements Shape {
    public void draw() { System.out.println("Rectangle"); }
}

class ShapeFactory {
    public static Shape getShape(String type) {
        return switch(type) {
            case "circle" -> new Circle();
            case "rectangle" -> new Rectangle();
            default -> null;
        };
    }
}
```

Usage:
```java
Shape shape = ShapeFactory.getShape("circle");
shape.draw();
```

---

## 4. Builder Pattern
Used for constructing complex objects step-by-step.

### Example:
```java
class Student {
    private String name;
    private int age;
    private String course;

    public static class Builder {
        private final Student student = new Student();

        public Builder name(String name) {
            student.name = name;
            return this;
        }

        public Builder age(int age) {
            student.age = age;
            return this;
        }

        public Builder course(String course) {
            student.course = course;
            return this;
        }

        public Student build() { return student; }
    }
}
```

Usage:
```java
Student s = new Student.Builder()
                    .name("Ishant")
                    .age(22)
                    .course("Java")
                    .build();
```

---

# 🟦 PART 2 — STRUCTURAL PATTERNS  

## 5. Adapter Pattern
Allows incompatible interfaces to work together.

### Example:
```java
interface MediaPlayer { void play(String filename); }

class Mp3Player implements MediaPlayer {
    public void play(String filename) {
        System.out.println("Playing mp3: " + filename);
    }
}

// Adaptee
class Mp4Player {
    void playMp4(String filename) {
        System.out.println("Playing mp4: " + filename);
    }
}

// Adapter
class MediaAdapter implements MediaPlayer {
    Mp4Player mp4 = new Mp4Player();

    public void play(String filename) {
        mp4.playMp4(filename);
    }
}
```

Usage:
```java
MediaPlayer player = new MediaAdapter();
player.play("movie.mp4");
```

---

## 6. Decorator Pattern
Adds new features to an object without modifying its structure.

### Example:
```java
interface Coffee { String getDescription(); int cost(); }

class BasicCoffee implements Coffee {
    public String getDescription() { return "Coffee"; }
    public int cost() { return 50; }
}

class MilkDecorator implements Coffee {
    private Coffee coffee;

    public MilkDecorator(Coffee c) { this.coffee = c; }

    public String getDescription() { return coffee.getDescription() + ", Milk"; }
    public int cost() { return coffee.cost() + 20; }
}
```

Usage:
```java
Coffee c = new MilkDecorator(new BasicCoffee());
System.out.println(c.getDescription() + ": " + c.cost());
```

---

## 7. Facade Pattern
Provides a simplified interface to a complex subsystem.

### Example:
```java
class CPU {
    void start() { System.out.println("CPU started"); }
}
class Memory {
    void load() { System.out.println("Memory loaded"); }
}

class Computer {
    CPU cpu = new CPU();
    Memory memory = new Memory();

    void start() {
        cpu.start();
        memory.load();
        System.out.println("Computer ready");
    }
}
```

---

# 🟧 PART 3 — BEHAVIORAL PATTERNS

## 8. Strategy Pattern
Select algorithms at runtime.

### Example:
```java
interface PaymentStrategy { void pay(int amount); }

class UpiPayment implements PaymentStrategy {
    public void pay(int amount) { System.out.println("Paid via UPI"); }
}

class CardPayment implements PaymentStrategy {
    public void pay(int amount) { System.out.println("Paid via Card"); }
}

class PaymentContext {
    private PaymentStrategy strategy;

    public PaymentContext(PaymentStrategy strategy) {
        this.strategy = strategy;
    }

    void payBill(int amount) {
        strategy.pay(amount);
    }
}
```

Usage:
```java
PaymentContext ctx = new PaymentContext(new UpiPayment());
ctx.payBill(500);
```

---

## 9. Observer Pattern
Used for event-driven systems.

### Example:
```java
interface Observer { void update(String msg); }

class User implements Observer {
    private String name;
    User(String n) { this.name = n; }

    public void update(String msg) {
        System.out.println(name + " received: " + msg);
    }
}

class NotificationService {
    private List<Observer> observers = new ArrayList<>();

    void subscribe(Observer o) { observers.add(o); }
    void notifyAllUsers(String msg) {
        for (Observer o : observers) o.update(msg);
    }
}
```

Usage:
```java
NotificationService ns = new NotificationService();
ns.subscribe(new User("Ishant"));
ns.notifyAllUsers("New message!");
```

---

## 10. Command Pattern
Encapsulates operations as objects.

### Example:
```java
interface Command { void execute(); }

class Light {
    void on() { System.out.println("Light ON"); }
}

class LightOnCommand implements Command {
    Light light;
    LightOnCommand(Light l) { this.light = l; }
    public void execute() { light.on(); }
}

class RemoteControl {
    Command command;
    void setCommand(Command c) { command = c; }
    void pressButton() { command.execute(); }
}
```

Usage:
```java
RemoteControl rc = new RemoteControl();
rc.setCommand(new LightOnCommand(new Light()));
rc.pressButton();
```

---

# 11. Summary of Patterns

## Creational:
- Singleton  
- Factory Method  
- Builder  

## Structural:
- Adapter  
- Decorator  
- Facade  

## Behavioral:
- Strategy  
- Observer  
- Command  

These patterns form the foundation for writing clean, maintainable Java applications.

---




