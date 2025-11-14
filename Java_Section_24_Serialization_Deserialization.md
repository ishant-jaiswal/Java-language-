# Java Section 24 — Serialization & Deserialization

## 1. What is Serialization?
Serialization is the process of converting a Java object into:
- A **byte stream**
- So it can be saved to a file, sent over a network, or stored.

Deserialization converts the byte stream back into the **original Java object**.

Java supports serialization through:
- `java.io.Serializable` interface

---

## 2. Marking a Class as Serializable
A class is serializable if it implements `Serializable`.

```java
import java.io.Serializable;

class Student implements Serializable {
    int id;
    String name;

    Student(int id, String name) {
        this.id = id;
        this.name = name;
    }
}
```

---

## 3. Serializing an Object (Writing Object to File)

```java
import java.io.*;

public class SerializeDemo {
    public static void main(String[] args) {
        try {
            Student s = new Student(1, "Ishant");

            FileOutputStream fos = new FileOutputStream("student.ser");
            ObjectOutputStream oos = new ObjectOutputStream(fos);

            oos.writeObject(s);
            oos.close();
            fos.close();

            System.out.println("Object Serialized!");
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

This creates a file **student.ser** containing the serialized object.

---

## 4. Deserializing an Object (Reading Object From File)

```java
import java.io.*;

public class DeserializeDemo {
    public static void main(String[] args) {
        try {
            FileInputStream fis = new FileInputStream("student.ser");
            ObjectInputStream ois = new ObjectInputStream(fis);

            Student s = (Student) ois.readObject();

            System.out.println(s.id + " - " + s.name);

            ois.close();
            fis.close();
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

---

## 5. serialVersionUID
Used to maintain versioning of serialized classes.

```java
class Student implements Serializable {
    private static final long serialVersionUID = 1L;
}
```

If `serialVersionUID` changes, deserialization will throw:

```
InvalidClassException
```

---

## 6. transient Keyword (Skip a Field)
Fields marked as `transient` are **not serialized**.

```java
class Employee implements Serializable {
    String name;
    transient String password; // will not be saved
}
```

---

## 7. Example: transient Effect

```java
Employee e = new Employee();
e.name = "Ishant";
e.password = "12345";
```

After serialization & deserialization:
- name → "Ishant"
- password → null

---

## 8. Serialization with Inheritance

- All parent classes must also be `Serializable`
- Otherwise, they must have a **no-arg constructor**

---

## 9. Custom Serialization (writeObject & readObject)

```java
private void writeObject(ObjectOutputStream oos) throws Exception {
    oos.defaultWriteObject();
    oos.writeInt(age); // custom data
}

private void readObject(ObjectInputStream ois) throws Exception {
    ois.defaultReadObject();
    age = ois.readInt();
}
```

---

## 10. Serializing Collections

Any `Serializable` object can be stored in collections.

```java
List<Student> list = new ArrayList<>();
list.add(new Student(1, "Aman"));
list.add(new Student(2, "Riya"));

ObjectOutputStream oos = new ObjectOutputStream(new FileOutputStream("list.ser"));
oos.writeObject(list);
```

---

## 11. Real-World Uses of Serialization
- Store application state
- Cache objects in memory/disk
- Send objects over network (RMI, sockets)
- Save user profiles in games

---

## 12. Serialization Alternatives
- JSON (Jackson / Gson)
- XML
- Protocol Buffers
- Avro

These are often more efficient and cross-language.

---

## End of Section 24
