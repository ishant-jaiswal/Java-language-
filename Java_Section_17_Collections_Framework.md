# Java Section 17 — Collections Framework (List, Set, Map, Queue) + Iteration

The **Java Collections Framework (JCF)** provides reusable data structures to store, manipulate, and retrieve data efficiently.

Located mainly in **java.util** package.

---

# **1. Why Collections?**
- Dynamic size (unlike arrays)
- Built-in algorithms (sort, search, shuffle)
- Ready-made data structures
- Easy iteration
- Unified architecture

---

# **2. Collection Hierarchy Overview**

```
Iterable
 └── Collection
      ├── List
      ├── Set
      └── Queue
Map (separate hierarchy)
```

---

# ---------------------------------------
# **3. LIST INTERFACE**
Ordered, allows duplicates.

Implementations:
- **ArrayList**
- **LinkedList**
- **Vector**

---

# **3.1 ArrayList Example**
```java
import java.util.*;

public class Demo {
    public static void main(String[] args) {
        ArrayList<String> list = new ArrayList<>();

        list.add("Java");
        list.add("Python");
        list.add("C++");

        System.out.println(list);
    }
}
```

---

# **3.2 Important List Methods**
```java
list.add(1, "New");
list.get(2);
list.remove("Java");
list.set(0, "Updated");
list.size();
list.contains("Python");
```

---

# ---------------------------------------
# **4. SET INTERFACE**
No duplicates allowed.

Implementations:
- **HashSet** (unordered)
- **LinkedHashSet** (ordered)
- **TreeSet** (sorted)

---

# **4.1 HashSet Example**
```java
import java.util.*;

HashSet<Integer> set = new HashSet<>();
set.add(10);
set.add(20);
set.add(10);    // duplicate ignored
System.out.println(set);
```

---

# ---------------------------------------
# **5. MAP INTERFACE**
Stores key–value pairs.

Implementations:
- **HashMap**
- **LinkedHashMap**
- **TreeMap**

---

# **5.1 HashMap Example**
```java
import java.util.*;

HashMap<Integer, String> map = new HashMap<>();

map.put(1, "Apple");
map.put(2, "Banana");
map.put(3, "Cherry");

System.out.println(map);
```

---

# **5.2 Map Methods**
```java
map.get(2);
map.remove(3);
map.containsKey(1);
map.containsValue("Banana");
map.size();
```

---

# ---------------------------------------
# **6. QUEUE INTERFACE**
Used in FIFO structures.

Implementations:
- **LinkedList**
- **PriorityQueue**
- **ArrayDeque**

---

# **6.1 Queue Example**
```java
import java.util.*;

Queue<String> q = new LinkedList<>();

q.add("A");
q.add("B");
q.add("C");

System.out.println(q.poll());   // remove head
System.out.println(q.peek());   // view head
```

---

# ---------------------------------------
# **7. ITERATING OVER COLLECTIONS**

## **7.1 Using for-each loop**
```java
for (String s : list) {
    System.out.println(s);
}
```

---

## **7.2 Using Iterator**
```java
Iterator<String> it = list.iterator();

while (it.hasNext()) {
    System.out.println(it.next());
}
```

---

## **7.3 Using ListIterator (bidirectional)**
```java
ListIterator<String> it = list.listIterator();

while (it.hasNext()) {
    System.out.println(it.next());
}
```

---

## **7.4 Iterating Map**
```java
for (Map.Entry<Integer, String> entry : map.entrySet()) {
    System.out.println(entry.getKey() + " -> " + entry.getValue());
}
```

---

# ---------------------------------------
# **8. Sorting Collections**

## **8.1 Sorting List**
```java
Collections.sort(list);
```

---

## **8.2 Sorting with Custom Comparator**
```java
Collections.sort(list, (a, b) -> b.compareTo(a)); // reverse
```

---

# ---------------------------------------
# **9. Important Collections Utility Methods**

```java
Collections.reverse(list);
Collections.shuffle(list);
Collections.max(list);
Collections.min(list);
```

---

# ---------------------------------------
# **10. Differences Summary**

### **List**
- Ordered  
- Allows duplicates

### **Set**
- No duplicates  
- HashSet: fast  
- TreeSet: sorted  

### **Map**
- Key-value  
- Keys unique  

### **Queue**
- FIFO  
- Useful for scheduling

---

# **End of Section 17 — Collections Framework**
Say **"next section"** to continue (Generics).
