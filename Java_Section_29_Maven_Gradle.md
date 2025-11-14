# Java Section 29 — Build Tools (Maven & Gradle Basics)

## 1. Introduction
Java projects usually use build tools to automate:
- Compilation
- Dependency management
- Packaging (JAR/WAR)
- Running tests
- Deployment

The two most popular Java build tools:
- **Maven**
- **Gradle**

---

# 🟥 Part 1 — Maven Basics

## 2. What is Maven?
Maven uses:
- **POM.xml** (Project Object Model)
- A **central repository** of dependencies
- **Goals** and **phases** (part of the build lifecycle)

---

## 3. Maven Project Structure
```
my-app/
 ├── src/
 │    ├── main/java
 │    ├── main/resources
 │    ├── test/java
 └── pom.xml
```

---

## 4. Example `pom.xml`

```xml
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 
                             http://maven.apache.org/xsd/maven-4.0.0.xsd">

    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>demo</artifactId>
    <version>1.0-SNAPSHOT</version>

    <dependencies>
        <dependency>
            <groupId>org.junit.jupiter</groupId>
            <artifactId>junit-jupiter</artifactId>
            <version>5.10.0</version>
            <scope>test</scope>
        </dependency>
    </dependencies>

</project>
```

---

## 5. Common Maven Commands

| Command | Description |
|--------|-------------|
| `mvn compile` | Compile source code |
| `mvn test` | Run tests |
| `mvn package` | Produce JAR/WAR |
| `mvn clean` | Delete target/ folder |
| `mvn install` | Add JAR to local repository |
| `mvn dependency:tree` | Show dependency tree |

---

## 6. Build Lifecycle
Maven uses structured phases:
1. **validate**
2. **compile**
3. **test**
4. **package**
5. **verify**
6. **install**
7. **deploy**

Running a later phase triggers all earlier phases automatically.

---

# 🟦 Part 2 — Gradle Basics

## 7. What is Gradle?
Gradle uses:
- Groovy or Kotlin DSL
- Faster incremental builds
- Highly customizable
- Used by Android Studio by default

---

## 8. Gradle Project Structure
```
my-app/
 ├── src/main/java
 ├── src/test/java
 ├── build.gradle
 ├── settings.gradle
```

---

## 9. Sample `build.gradle` (Groovy DSL)
```gradle
plugins {
    id 'java'
}

group = 'com.example'
version = '1.0'

repositories {
    mavenCentral()
}

dependencies {
    testImplementation 'org.junit.jupiter:junit-jupiter:5.10.0'
}

test {
    useJUnitPlatform()
}
```

---

## 10. Common Gradle Commands

| Command | Description |
|--------|-------------|
| `gradle build` | Compile + test + package |
| `gradle clean` | Remove build/ folder |
| `gradle test` | Run tests |
| `gradle dependencies` | Show dependency tree |
| `gradle tasks` | List all tasks |

---

## 11. Gradle vs Maven

| Feature | Maven | Gradle |
|---------|--------|---------|
| Speed | Slower | Faster (incremental) |
| Language | XML | Groovy/Kotlin DSL |
| Customization | Moderate | Very high |
| Android Support | No | Yes (Primary tool) |

---

## 12. Example: Creating a Fat JAR (Gradle)
```gradle
jar {
    duplicatesStrategy = DuplicatesStrategy.INCLUDE
    manifest {
        attributes 'Main-Class': 'com.example.Main'
    }
    from {
        configurations.runtimeClasspath.collect { it.isDirectory() ? it : zipTree(it) }
    }
}
```

---

## 13. Example: Creating a Fat JAR (Maven)
```xml
<plugin>
    <groupId>org.apache.maven.plugins</groupId>
    <artifactId>maven-assembly-plugin</artifactId>
    <version>3.5.0</version>
    <configuration>
        <descriptorRefs>
            <descriptorRef>jar-with-dependencies</descriptorRef>
        </descriptorRefs>
    </configuration>
    <executions>
        <execution>
            <id>make-assembly</id>
            <phase>package</phase>
            <goals><goal>single</goal></goals>
        </execution>
    </executions>
</plugin>
```

---

## 14. Summary

### Maven:
- XML-based  
- Strong conventions  
- Simple for standard projects  

### Gradle:
- Script-based  
- Faster builds  
- Best for Android  

---



