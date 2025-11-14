# Java Section 30 — Popular Frameworks Overview (Spring & Hibernate)

## 1. Introduction
Modern Java development relies heavily on frameworks to speed up development, reduce boilerplate, and follow industry best practices.  
Two of the most widely used frameworks are:

- **Spring Framework** (Enterprise-level apps, MVC, REST, Security, Dependency Injection)
- **Hibernate ORM** (Database ORM for Java, replaces JDBC boilerplate)

This section provides a clear, practical overview with examples.

---

# 🟩 PART 1 — SPRING FRAMEWORK

## 2. What is Spring?
Spring is a powerful Java framework providing:
- **Dependency Injection (DI)**  
- **Inversion of Control (IoC)**  
- **Spring Boot** for rapid development  
- **Spring MVC** for web apps  
- **Spring Data JPA** for database access  
- **Spring Security** for authentication  

---

## 3. Spring Boot — Quick Overview
Spring Boot simplifies Spring configuration and allows you to build production-grade apps with minimal setup.

### Example: Spring Boot Application
```java
@SpringBootApplication
public class DemoApplication {
    public static void main(String[] args) {
        SpringApplication.run(DemoApplication.class, args);
    }
}
```

### `pom.xml` Dependency
```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-web</artifactId>
</dependency>
```

---

## 4. Spring REST Controller Example

```java
@RestController
@RequestMapping("/api")
public class HelloController {

    @GetMapping("/hello")
    public String sayHello() {
        return "Hello from Spring!";
    }
}
```

Run the application → Open:  
`http://localhost:8080/api/hello`

---

## 5. Dependency Injection (Core Spring Concept)

### Without DI (Bad)
```java
class Car {
    Engine engine = new Engine(); // tightly coupled
}
```

### With DI (Good)
```java
@Component
class Engine {}

@Component
class Car {
    private final Engine engine;

    @Autowired
    Car(Engine engine) {
        this.engine = engine;
    }
}
```

Spring automatically injects dependencies.

---

## 6. Spring Data JPA Example

### Entity
```java
@Entity
public class Student {
    @Id
    @GeneratedValue
    private Long id;
    private String name;
}
```

### Repository
```java
public interface StudentRepository extends JpaRepository<Student, Long> {}
```

### Service
```java
@Service
public class StudentService {
    @Autowired
    StudentRepository repo;

    public List<Student> getAll() {
        return repo.findAll();
    }
}
```

---

# 🟦 PART 2 — HIBERNATE FRAMEWORK

## 7. What is Hibernate?
Hibernate is an **Object Relational Mapping (ORM)** tool that maps Java classes → database tables.

Features:
- Eliminates boilerplate JDBC code  
- Automatically handles SQL queries  
- Supports HQL, caching, lazy loading, transactions  

---

## 8. Hibernate Architecture Overview
- **SessionFactory** → creates sessions  
- **Session** → performs CRUD operations  
- **Transaction** → commit/rollback  
- **Persistent objects** → mapped using annotations  

---

## 9. Hibernate Configuration (Basic)

### `hibernate.cfg.xml`
```xml
<hibernate-configuration>
    <session-factory>
        <property name="hibernate.dialect">org.hibernate.dialect.MySQLDialect</property>
        <property name="hibernate.hbm2ddl.auto">update</property>
        <property name="hibernate.connection.driver_class">com.mysql.cj.jdbc.Driver</property>
        <property name="hibernate.connection.url">jdbc:mysql://localhost:3306/testdb</property>
        <property name="hibernate.connection.username">root</property>
        <property name="hibernate.connection.password">password</property>
    </session-factory>
</hibernate-configuration>
```

---

## 10. Hibernate Entity Example

```java
@Entity
@Table(name = "users")
public class User {

    @Id
    @GeneratedValue
    private int id;

    private String name;
}
```

---

## 11. Hibernate CRUD Example

```java
Session session = sessionFactory.openSession();
Transaction tx = session.beginTransaction();

User user = new User();
user.setName("John");

session.save(user);
tx.commit();
session.close();
```

---

## 12. Hibernate Query Examples (HQL)

```java
List<User> users = session.createQuery("FROM User", User.class).list();
```

Parameterized:

```java
Query<User> q = session.createQuery("FROM User WHERE name = :name", User.class);
q.setParameter("name", "John");
List<User> result = q.list();
```

---

# 🟧 Spring vs Hibernate

| Feature | Spring | Hibernate |
|--------|--------|-----------|
| Purpose | Full application framework | ORM for DB handling |
| Built-in Web? | Yes (Spring MVC/Boot) | No |
| DB Access? | Spring Data JPA | Core ORM |
| Learning Curve | Easier (Boot) | Moderate |
| Used Together? | **Yes — Most common approach** |

📌 Most real-world Java apps use:  
**Spring Boot + Spring Data JPA + Hibernate**

---

# 13. Summary

### Spring:
- Builds entire applications
- REST APIs, security, dependency injection
- Most widely used Java framework

### Hibernate:
- Maps Java classes to database tables
- Removes JDBC boilerplate
- Used underneath Spring Data JPA

---



