# Java Section 19 — Java I/O (Streams, Readers/Writers, Files, NIO)

Java I/O (Input/Output) allows programs to read/write data from files, networks, memory, and other sources.

---

# **1. Streams Overview**
A **stream** is a sequence of data.

Two main categories:
- **Byte Streams** → Read/write raw bytes  
  Classes: `FileInputStream`, `FileOutputStream`
- **Character Streams** → Read/write text  
  Classes: `FileReader`, `FileWriter`

---

# -----------------------------------------
# **2. Byte Streams**

## **2.1 FileInputStream Example**
Reading bytes from a file:

```java
import java.io.*;

public class ReadBytes {
    public static void main(String[] args) {
        try {
            FileInputStream fis = new FileInputStream("data.txt");
            int b;
            while ((b = fis.read()) != -1) {
                System.out.print((char)b);
            }
            fis.close();
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

---

## **2.2 FileOutputStream Example**
Writing bytes to a file:

```java
import java.io.*;

public class WriteBytes {
    public static void main(String[] args) {
        try {
            FileOutputStream fos = new FileOutputStream("output.txt");
            fos.write("Hello Java IO".getBytes());
            fos.close();
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

---

# -----------------------------------------
# **3. Character Streams**

## **3.1 FileReader Example**
```java
FileReader fr = new FileReader("data.txt");
int ch;
while ((ch = fr.read()) != -1) {
    System.out.print((char) ch);
}
fr.close();
```

---

## **3.2 FileWriter Example**
```java
FileWriter fw = new FileWriter("output.txt");
fw.write("Welcome to Java FileWriter");
fw.close();
```

---

# -----------------------------------------
# **4. Buffered Streams**

### Why Buffered Streams?
- Faster  
- Reduce number of disk accesses  

---

## **4.1 BufferedReader Example**
```java
import java.io.*;

BufferedReader br = new BufferedReader(new FileReader("data.txt"));

String line;
while ((line = br.readLine()) != null) {
    System.out.println(line);
}

br.close();
```

---

## **4.2 BufferedWriter Example**
```java
BufferedWriter bw = new BufferedWriter(new FileWriter("output.txt"));
bw.write("Buffered writing is fast!");
bw.close();
```

---

# -----------------------------------------
# **5. File Class (java.io.File)**

Used for:
- Checking file existence  
- Creating files/directories  
- Deleting files  
- Listing directory contents  

---

## **5.1 File Example**
```java
import java.io.File;

public class FileDemo {
    public static void main(String[] args) {
        File f = new File("test.txt");

        System.out.println("Exists: " + f.exists());
        System.out.println("Path: " + f.getAbsolutePath());
        System.out.println("Is File: " + f.isFile());
        System.out.println("Is Directory: " + f.isDirectory());
    }
}
```

---

# -----------------------------------------
# **6. Serialization & Deserialization (Basics)**

Serialization = Convert object → file  
Deserialization = Convert file → object

---

## **6.1 Serialization Example**
```java
import java.io.*;

class Student implements Serializable {
    String name;
    int age;
}

public class WriteObj {
    public static void main(String[] args) throws Exception {
        Student s = new Student();
        s.name = "John";
        s.age = 20;

        ObjectOutputStream out = new ObjectOutputStream(new FileOutputStream("obj.dat"));
        out.writeObject(s);
        out.close();
    }
}
```

---

## **6.2 Deserialization Example**
```java
import java.io.*;

public class ReadObj {
    public static void main(String[] args) throws Exception {
        ObjectInputStream in = new ObjectInputStream(new FileInputStream("obj.dat"));
        Student s = (Student) in.readObject();
        System.out.println(s.name + " " + s.age);
        in.close();
    }
}
```

---

# -----------------------------------------
# **7. Java NIO (New I/O)**  
Introduced in Java 7 for:
- Fast file operations  
- Non-blocking IO  
- Improved APIs  

Main package: `java.nio.file`

---

## **7.1 Reading File using NIO**
```java
import java.nio.file.*;

public class NIORead {
    public static void main(String[] args) throws Exception {
        String data = Files.readString(Path.of("data.txt"));
        System.out.println(data);
    }
}
```

---

## **7.2 Writing File using NIO**
```java
Files.writeString(Path.of("output.txt"), "Hello from NIO!");
```

---

## **7.3 Copying & Deleting Files**
```java
Files.copy(Path.of("a.txt"), Path.of("b.txt"));
Files.delete(Path.of("b.txt"));
```

---

# -----------------------------------------
# **8. Directory Operations (NIO)**

```java
Files.createDirectory(Path.of("myfolder"));
Files.createDirectories(Path.of("a/b/c"));
Files.list(Path.of(".")).forEach(System.out::println);
```

---

# -----------------------------------------
# **9. Comparison — IO vs NIO**

| Feature | IO | NIO |
|--------|----|-----|
| Speed | Slower | Faster |
| API | Simple | Modern |
| Data Flow | Stream-based | Buffer-based |
| Non-blocking | No | Yes |

---

# -----------------------------------------
# **10. Best Practices**
- Prefer **Buffered** streams for speed.  
- Use **try-with-resources** to avoid memory leaks.  
- Prefer **NIO** for modern applications.  

---

# **End of Section 19 — Java I/O**  
Say **"next section"** to continue (Concurrency: Threads, Executors, Synchronization, Locks, Futures).
