# collection_framework

### **ArrayList in Java**

An `ArrayList` is part of the Java Collections Framework and implements the **List** interface. It is a dynamic array that grows as elements are added to it.

---

### **Key Characteristics of ArrayList**

1. **Dynamic Sizing**: 
   - Unlike arrays, an `ArrayList` can dynamically resize as elements are added or removed.
   - It automatically grows when the current array is full by creating a new array with a larger size and copying the old array into it.

2. **Ordered Collection**: 
   - `ArrayList` maintains the insertion order. Elements are indexed, meaning they can be accessed by their index (0-based).

3. **Allows Duplicates**: 
   - `ArrayList` allows duplicate elements.

4. **Indexed Access**: 
   - You can access elements by their index (O(1) time complexity for getting an element).

5. **Null Elements**: 
   - `ArrayList` allows **null** values as valid elements, but this should be used with caution (since `null` can lead to `NullPointerException` in some cases).

---

### **Basic Operations on ArrayList**

1. **Adding Elements**
   - `add(E e)`: Adds an element at the end of the list.
   - `add(int index, E element)`: Inserts an element at the specified position.
   - **Example**:
     ```java
     ArrayList<String> list = new ArrayList<>();
     list.add("Apple");
     list.add("Banana");
     list.add(1, "Orange"); // Adds "Orange" at index 1
     ```

2. **Accessing Elements**
   - `get(int index)`: Retrieves the element at the specified index.
   - **Example**:
     ```java
     String fruit = list.get(0); // Accesses "Apple"
     ```

3. **Modifying Elements**
   - `set(int index, E element)`: Replaces the element at the specified index.
   - **Example**:
     ```java
     list.set(0, "Grapes"); // Replaces "Apple" with "Grapes"
     ```

4. **Removing Elements**
   - `remove(int index)`: Removes the element at the specified index.
   - `remove(Object o)`: Removes the first occurrence of the specified element.
   - **Example**:
     ```java
     list.remove(1); // Removes the element at index 1 ("Orange")
     list.remove("Banana"); // Removes "Banana"
     ```

5. **Size of ArrayList**
   - `size()`: Returns the number of elements in the list.
   - **Example**:
     ```java
     int size = list.size(); // Returns the size of the list
     ```

6. **Checking if ArrayList Contains an Element**
   - `contains(Object o)`: Returns `true` if the list contains the specified element.
   - **Example**:
     ```java
     boolean hasApple = list.contains("Apple"); // Returns true if "Apple" is present
     ```

7. **Clearing All Elements**
   - `clear()`: Removes all elements from the list.
   - **Example**:
     ```java
     list.clear(); // Removes all elements from the list
     ```

8. **Index of an Element**
   - `indexOf(Object o)`: Returns the index of the first occurrence of the specified element, or -1 if the element is not found.
   - **Example**:
     ```java
     int index = list.indexOf("Apple"); // Returns the index of "Apple"
     ```

9. **Checking if the List is Empty**
   - `isEmpty()`: Returns `true` if the list has no elements.
   - **Example**:
     ```java
     boolean isEmpty = list.isEmpty(); // Returns true if the list is empty
     ```

---

### **Performance Considerations**
1. **Time Complexity**:
   - **Add**: 
     - `add(E e)` – O(1) for adding at the end (amortized), but resizing the array can take O(n).
     - `add(int index, E element)` – O(n) because it might need to shift elements.
   - **Access**: 
     - `get(int index)` – O(1).
   - **Remove**: 
     - `remove(int index)` – O(n) because it may require shifting elements.
     - `remove(Object o)` – O(n) for searching and removal.
   - **Search**: 
     - `contains(Object o)` – O(n), as it may need to iterate over the entire list.

2. **Space Complexity**:
   - The `ArrayList` internally uses an array. If the number of elements exceeds the current array size, a new array is created with a larger size (typically 1.5 times the previous size). This resizing causes the space complexity to grow.
   
3. **Memory Usage**:
   - An `ArrayList` takes up more memory than a regular array because it has additional overhead (for instance, to handle dynamic resizing).
   
---

### **ArrayList vs. LinkedList**
- **ArrayList**:
  - Provides fast **random access** to elements via an index (O(1)).
  - Better for operations where the list size is known or grows in a predictable manner (due to amortized O(1) for adding at the end).
  - Slower for inserting or removing elements from the middle (O(n)).
  
- **LinkedList**:
  - Provides **O(1)** insertion and removal at the beginning and end.
  - Slower for random access to elements (O(n)) because it needs to traverse from the head or tail.
  - Better for frequent insertions and deletions.

---

### **Best Practices**
1. **Capacity Management**: 
   - If you know the size in advance, you can use the constructor `ArrayList(int initialCapacity)` to avoid resizing during runtime.
   - Example: `ArrayList<String> list = new ArrayList<>(100);` to initialize with a capacity of 100.
   
2. **Avoid Frequent Resizing**:
   - Repeated `add()` calls may cause the underlying array to resize multiple times, which is costly. Plan the size in advance if possible.

3. **Use Generics**: 
   - Always use generics to avoid `ClassCastException` and to provide type safety.
   - Example: `ArrayList<String> list = new ArrayList<>();`

4. **Iterating Over ArrayList**:
   - Use an `Iterator` or enhanced `for-each` loop for safe iteration over elements.
   - Example:
     ```java
     for (String item : list) {
         System.out.println(item);
     }
     ```

---

### **Example Code Snippet**

```java
import java.util.ArrayList;

public class ArrayListExample {
    public static void main(String[] args) {
        // Create an ArrayList
        ArrayList<String> fruits = new ArrayList<>();

        // Adding elements
        fruits.add("Apple");
        fruits.add("Banana");
        fruits.add("Mango");
        fruits.add(1, "Orange");

        // Accessing elements
        System.out.println("First fruit: " + fruits.get(0));  // Output: Apple

        // Modifying elements
        fruits.set(1, "Grapes");

        // Removing elements
        fruits.remove("Mango");
        fruits.remove(1);  // Removes "Grapes" (index 1)

        // Checking size and contents
        System.out.println("Size: " + fruits.size());  // Output: 2
        System.out.println("Contains Banana: " + fruits.contains("Banana"));  // Output: false
    }
}
```

---

### **Conclusion**
`ArrayList` is a versatile, widely used collection class in Java. It's most useful for scenarios where fast random access to elements is needed and when the size of the collection is dynamic. However, it’s less efficient than other collections for operations that involve frequent insertions or deletions in the middle of the list.


### **LinkedList in Java - Detailed Interview Notes**

A **LinkedList** in Java is a part of the Java Collections Framework and implements both the **List** and **Deque** interfaces. It is a doubly-linked list, which means each element (node) contains references (pointers) to both the next and the previous nodes in the list.

Unlike an **ArrayList**, which is backed by an array, a **LinkedList** stores its elements in nodes, where each node holds the data and references to its neighboring nodes. This structure allows **efficient insertions and deletions** at both ends of the list.

---

### **Key Characteristics of LinkedList**

1. **Dynamic Size**:
   - Unlike arrays or `ArrayLists`, a `LinkedList` doesn't need to know the size in advance. It grows and shrinks as elements are added or removed.

2. **Efficient Insertions and Deletions**:
   - Insertions and deletions are **O(1)** at the beginning and end of the list because only pointers need to be updated.
   - Inserting or deleting at any position other than the start or end requires traversal, so it's **O(n)** in the worst case.

3. **Ordered Collection**:
   - A `LinkedList` maintains the order of insertion, similar to `ArrayList`.

4. **Supports Null Elements**:
   - `LinkedList` allows **null** elements, but care should be taken while performing operations to avoid issues with `NullPointerException`.

5. **Doubly Linked**:
   - Each node contains a reference to both its **next** and **previous** node, allowing traversal in both directions.

6. **Implements List and Deque**:
   - As a `List`, it supports indexed access, but slower than `ArrayList`.
   - As a `Deque`, it can be used as a queue or stack with **FIFO (First-In-First-Out)** and **LIFO (Last-In-First-Out)** order.

---

### **Structure of LinkedList (Node Structure)**

A **LinkedList** consists of nodes, and each node contains:
1. **Data**: The value or data of the node.
2. **Next**: A reference to the next node in the list.
3. **Previous**: A reference to the previous node in the list.

```java
class Node {
    Object data;
    Node next;
    Node prev;
}
```

---

### **Basic Operations in LinkedList**

1. **Adding Elements**

   - **add(E e)**: Adds the element at the end of the list.
   - **add(int index, E element)**: Inserts the element at the specified position.
   - **addFirst(E e)**: Adds the element at the beginning.
   - **addLast(E e)**: Adds the element at the end (same as `add()` but specific to `LinkedList`).
   
   **Example**:
   ```java
   LinkedList<String> list = new LinkedList<>();
   list.add("Apple");        // Adds "Apple" at the end
   list.addFirst("Banana");  // Adds "Banana" at the beginning
   list.addLast("Mango");    // Adds "Mango" at the end
   list.add(1, "Orange");    // Adds "Orange" at index 1
   ```

2. **Accessing Elements**
   - **get(int index)**: Retrieves the element at the specified index.
   - **getFirst()**: Retrieves the first element.
   - **getLast()**: Retrieves the last element.
   
   **Example**:
   ```java
   String first = list.getFirst();   // Returns "Banana"
   String last = list.getLast();     // Returns "Mango"
   String element = list.get(1);     // Returns "Orange"
   ```

3. **Modifying Elements**
   - **set(int index, E element)**: Replaces the element at the specified index with the new element.

   **Example**:
   ```java
   list.set(1, "Grapes");  // Replaces "Orange" with "Grapes"
   ```

4. **Removing Elements**
   - **remove(int index)**: Removes the element at the specified index.
   - **remove(Object o)**: Removes the first occurrence of the specified element.
   - **removeFirst()**: Removes the first element.
   - **removeLast()**: Removes the last element.
   
   **Example**:
   ```java
   list.remove(1);        // Removes element at index 1 ("Grapes")
   list.remove("Banana"); // Removes "Banana"
   list.removeFirst();    // Removes first element ("Banana")
   list.removeLast();     // Removes last element ("Mango")
   ```

5. **Size and Checking Emptiness**
   - **size()**: Returns the number of elements in the list.
   - **isEmpty()**: Checks if the list is empty.
   
   **Example**:
   ```java
   int size = list.size();   // Returns the size of the list
   boolean empty = list.isEmpty();  // Returns true if the list is empty
   ```

6. **Other Useful Methods**
   - **contains(Object o)**: Checks if the list contains the specified element.
   - **clear()**: Removes all elements from the list.
   
   **Example**:
   ```java
   boolean hasApple = list.contains("Apple");  // Returns true if "Apple" is in the list
   list.clear();                               // Removes all elements
   ```

---

### **Performance Considerations**
1. **Time Complexity**:
   - **Add at the beginning or end**: O(1) for `addFirst()`, `addLast()`, `add()`.
   - **Get at an index**: O(n) because you must traverse the list to find the element.
   - **Remove at the beginning or end**: O(1) for `removeFirst()`, `removeLast()`.
   - **Remove by index or element**: O(n) for `remove(int index)` or `remove(Object o)`.
   - **Access by index**: O(n) for `get(int index)`.

2. **Space Complexity**:
   - Each node has three fields (data, next, previous), so it uses more memory than an `ArrayList` or regular array. Space complexity is proportional to the number of elements, **O(n)**.

---

### **LinkedList vs ArrayList**
- **LinkedList**:
  - Faster for frequent insertions or deletions at the **beginning** or **end** (O(1)).
  - Slower for random access (O(n)) because it needs to traverse the list.
  - Uses more memory due to the additional references (next and previous).
  - Can be used as a **Deque** (double-ended queue) for queue/stack operations.
  
- **ArrayList**:
  - Faster for random access (O(1)) due to contiguous memory storage.
  - Slower for insertions and deletions at the **middle** (O(n)).
  - More memory-efficient as it doesn't store additional pointers.

---

### **LinkedList as a Deque**
Since `LinkedList` implements the `Deque` interface, it can function as a **queue** or **stack**:
1. **Queue (FIFO)**:
   - `addFirst()`, `removeLast()`, `peekFirst()`, `peekLast()`
   - `offerFirst()`, `pollFirst()`, `offerLast()`, `pollLast()`
   
2. **Stack (LIFO)**:
   - `addFirst()` for **push** operation.
   - `removeFirst()` for **pop** operation.
   - `peekFirst()` for **peek** operation.

---

### **Example Code Snippet**

```java
import java.util.LinkedList;

public class LinkedListExample {
    public static void main(String[] args) {
        LinkedList<String> list = new LinkedList<>();

        // Adding elements
        list.add("Apple");
        list.add("Banana");
        list.addFirst("Mango");   // Adds at the beginning
        list.addLast("Grapes");   // Adds at the end

        // Accessing elements
        System.out.println("First: " + list.getFirst());  // Mango
        System.out.println("Last: " + list.getLast());    // Grapes

        // Modifying elements
        list.set(1, "Orange");  // Replaces "Banana" with "Orange"

        // Removing elements
        list.remove(1);         // Removes "Orange"
        list.removeFirst();     // Removes "Mango"
        list.removeLast();      // Removes "Grapes"

        // Checking size and emptiness
        System.out.println("Size: " + list.size());   // 1
        System.out.println("Is Empty: " + list.isEmpty());   // false
    }
}
```

---

### **Conclusion**
- **LinkedList** is ideal when you need efficient insertions and deletions at both ends of the list. It is commonly used in cases like implementing queues, stacks, or maintaining a dynamically sized list where frequent insertions or deletions happen at the start or end.
- **Limitations**: Its random access performance is poor compared to `ArrayList`. It's not suitable when you need frequent access to elements by index.
