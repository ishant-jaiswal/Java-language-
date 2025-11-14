# Java Section 23 — JDBC (Java Database Connectivity)

## 1. Introduction to JDBC
JDBC allows Java programs to:

- Connect to databases  
- Execute SQL queries  
- Retrieve and update data  
- Manage transactions  

JDBC works with all major DBs (MySQL, Oracle, PostgreSQL, SQLite).

---

## 2. JDBC Architecture

### Components:
1. **DriverManager** — loads and manages DB drivers  
2. **Connection** — connects Java app → database  
3. **Statement / PreparedStatement** — executes SQL queries  
4. **ResultSet** — stores returned data  

---

## 3. Steps to Use JDBC

### 1. Load Driver  
```java
Class.forName("com.mysql.cj.jdbc.Driver");
```

### 2. Create Connection  
```java
Connection con = DriverManager.getConnection(
    "jdbc:mysql://localhost:3306/testdb",
    "root",
    "password"
);
```

### 3. Create Statement  
```java
Statement stmt = con.createStatement();
```

### 4. Execute Query  
```java
ResultSet rs = stmt.executeQuery("SELECT * FROM students");
```

### 5. Process Results  
```java
while (rs.next()) {
    System.out.println(rs.getInt("id") + " " + rs.getString("name"));
}
```

### 6. Close Resources  
```java
rs.close();
stmt.close();
con.close();
```

---

## 4. Full Working Example — Select Records

```java
import java.sql.*;

public class Main {
    public static void main(String[] args) {
        try {
            Class.forName("com.mysql.cj.jdbc.Driver");

            Connection con = DriverManager.getConnection(
                    "jdbc:mysql://localhost:3306/testdb", "root", "password");

            Statement stmt = con.createStatement();

            ResultSet rs = stmt.executeQuery("SELECT * FROM students");

            while (rs.next()) {
                System.out.println(rs.getInt("id") + " - " + rs.getString("name"));
            }

            rs.close();
            stmt.close();
            con.close();

        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

---

## 5. Using PreparedStatement (Prevents SQL Injection)
```java
String sql = "INSERT INTO students(name, age) VALUES (?, ?)";
PreparedStatement ps = con.prepareStatement(sql);
ps.setString(1, "Ishant");
ps.setInt(2, 22);
ps.executeUpdate();
```

---

## 6. Update Example
```java
String sql = "UPDATE students SET age = ? WHERE id = ?";
PreparedStatement ps = con.prepareStatement(sql);
ps.setInt(1, 25);
ps.setInt(2, 1);
ps.executeUpdate();
```

---

## 7. Delete Example
```java
String sql = "DELETE FROM students WHERE id = ?";
PreparedStatement ps = con.prepareStatement(sql);
ps.setInt(1, 3);
ps.executeUpdate();
```

---

## 8. Transaction Management
```java
con.setAutoCommit(false);

try {
    PreparedStatement ps1 = con.prepareStatement("UPDATE accounts SET balance = balance - 500 WHERE id=1");
    PreparedStatement ps2 = con.prepareStatement("UPDATE accounts SET balance = balance + 500 WHERE id=2");

    ps1.executeUpdate();
    ps2.executeUpdate();

    con.commit();  // transaction success
} catch (Exception e) {
    con.rollback(); // rollback on error
}
```

---

## 9. Using Try-With-Resources (Best Practice)
```java
try (Connection con = DriverManager.getConnection(url, user, pass);
     PreparedStatement ps = con.prepareStatement("SELECT * FROM students");
     ResultSet rs = ps.executeQuery()) {

    while (rs.next()) {
        System.out.println(rs.getString("name"));
    }
} catch (Exception e) {
    e.printStackTrace();
}
```

---

## 10. Common JDBC Drivers

| Database | Driver Class |
|----------|--------------|
| MySQL | com.mysql.cj.jdbc.Driver |
| PostgreSQL | org.postgresql.Driver |
| Oracle | oracle.jdbc.driver.OracleDriver |
| SQLite | org.sqlite.JDBC |

---

## End of Section 23
