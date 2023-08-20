---
share: true
---
TAGS: #Hashing #Immutable_Class #Generics #Priority_Queue
## Dynamic Array vs. Static Array

A dynamic array, also known as a resizable array or Array List in Java, is a data structure that can grow or shrink in size during runtime. It provides a flexible way to store elements of the same data type, much like a regular array. The key difference is that a dynamic array can dynamically resize itself to accommodate more elements as needed.

In Java, the `ArrayList` class from the `java.util` package is an example of a dynamic array. It allows you to add, remove, and access elements while automatically handling the resizing of the underlying array.

On the other hand, a static array has a fixed size determined at the time of its creation. The size cannot be changed after initialization. Static arrays in Java are declared with a fixed size using square brackets, such as `int[] staticArray = new int[10];`.

---

## Memory Allocation on the Heap in Java

In Java, memory allocation for objects is primarily done on the heap. The heap is a region of memory used for dynamic memory allocation, where objects are created and managed by the Java Virtual Machine (JVM).

To allocate memory on the heap for an object, you use the `new` keyword followed by the constructor of the class. Here's an example of memory allocation for an object on the heap in Java:

```java
public class Student {
    private String name;
    private int age;

    public Student(String name, int age) {
        this.name = name;
        this.age = age;
    }

    // Other methods and properties...
}

public class Main {
    public static void main(String[] args) {
        // Allocate memory for a Student object on the heap
        Student student = new Student("John Doe", 20);
        
        // Now 'student' references the allocated object
    }
}
```

In this example, the `new Student("John Doe", 20)` statement allocates memory on the heap for a `Student` object and initializes its properties. The variable `student` then holds a reference to this object.

Remember that Java automatically manages memory through garbage collection, which means you don't need to explicitly free the memory when an object is no longer in use. The JVM takes care of reclaiming memory from objects that are no longer reachable.

---
## Hashing Concepts

Hashing is a fundamental concept in computer science used to map data of arbitrary size to fixed-size values (usually integers), which are typically used as indexes or keys in data structures. Hashing is widely used in various applications such as data retrieval, encryption, and checking data integrity.

A hash function takes an input (or 'message') and returns a fixed-size string of characters, which is typically a numeric value. The output, known as a hash code or hash value, should have the following properties:

1. Deterministic: The same input will always produce the same hash value.
2. Fast Computation: The hash function should be efficient to compute.
3. Avalanche Effect: A small change in the input should result in a significantly different hash value.
4. Pre-image Resistance: Given a hash value, it should be computationally infeasible to find the original input.

In data structures like hash tables, hash codes are used to index and quickly retrieve data. Collisions, which occur when two different inputs produce the same hash value, are a common concern when designing hash functions. Techniques like chaining or open addressing are used to handle collisions.

---
An immutable class in Java is a class whose instances cannot be modified after they are created. This ensures that the state of the object remains constant throughout its lifetime. To create an immutable class, follow these key principles:

1. Make the class `final` to prevent inheritance, as subclasses could potentially introduce mutable behavior.
2. Declare all fields as `final` to make them unmodifiable after object creation.
3. Initialize all fields through the constructor.
4. Avoid providing any setter methods.
5. Do not expose mutable objects or references to mutable objects.

Here's an example of an immutable class in Java:

```java
public final class ImmutablePerson {
    private final String name;
    private final int age;

    public ImmutablePerson(String name, int age) {
        this.name = name;
        this.age = age;
    }

    public String getName() {
        return name;
    }

    public int getAge() {
        return age;
    }
}
```

In this example, the `ImmutablePerson` class is immutable because its fields are declared as `final`, and it provides only getter methods to access the values. Once an instance of `ImmutablePerson` is created, its state cannot be changed.

Usage of the `ImmutablePerson` class:

```java
public class Main {
    public static void main(String[] args) {
        ImmutablePerson person = new ImmutablePerson("Alice", 30);
        
        System.out.println("Name: " + person.getName());
        System.out.println("Age: " + person.getAge());
        
        // Trying to modify the object (which is not possible)
        // person.setName("Bob"); // This will not compile
        
        // Creating a new instance with different values
        ImmutablePerson newPerson = new ImmutablePerson("Bob", 25);
        
        System.out.println("Name (new): " + newPerson.getName());
        System.out.println("Age (new): " + newPerson.getAge());
    }
}
```

Remember that in an immutable class, you're essentially creating a new object whenever you want to change a property. This can be memory-intensive, so immutability should be chosen based on the requirements of your program.

Also, note that if your class contains mutable objects (like collections), you need to ensure that they are either not exposed publicly or that their modifications are properly managed to maintain the immutability of the class.

---
## Implementation of Vector/ ArrayList using Generics

```java
public class CustomVector<T> {
    private Object[] array;
    private int size;
    private int capacity;

    public CustomVector(int initialCapacity) {
        if (initialCapacity <= 0) {
            throw new IllegalArgumentException("Initial capacity must be positive.");
        }
        capacity = initialCapacity;
        array = new Object[capacity];
        size = 0;
    }

    public void add(T element) {
        if (size == capacity) {
            expandCapacity();
        }
        array[size++] = element;
    }

    @SuppressWarnings("unchecked")
    public T get(int index) {
        if (index < 0 || index >= size) {
            throw new IndexOutOfBoundsException("Index out of bounds: " + index);
        }
        return (T) array[index];
    }

    public int size() {
        return size;
    }

    private void expandCapacity() {
        capacity *= 2;
        Object[] newArray = new Object[capacity];
        System.arraycopy(array, 0, newArray, 0, size);
        array = newArray;
    }

    // Other methods like remove, clear, etc. can be added here
}
```

Please note that this is a simplified version of a Vector class and might not handle all edge cases. Now, let's discuss the approaches to finding the third largest number in a large dataset:

### Approaches to Finding Third Largest Number

1. **Sorting:** One common approach is to sort the dataset in descending order and then directly access the third largest element. However, this has a time complexity of O(n log n) for most sorting algorithms, which might not be efficient for large datasets.

2. **Priority Queue (Heap):** You can use a min-heap to find the third largest element. Start by inserting the first three elements into the heap. Then, for each subsequent element, compare it with the smallest element in the heap. If it's larger, remove the smallest element and insert the new element. At the end, the smallest element in the heap will be the third largest in the dataset. This approach has a time complexity of O(n log k), where k is the number of elements to be maintained in the heap.

3. **Linear Scan:** Perform a linear scan of the dataset while maintaining three variables to track the first, second, and third largest numbers. Update these variables as you iterate through the dataset. This approach has a time complexity of O(n), making it efficient for large datasets.

Here's a basic implementation of the linear scan approach:

```java
public int findThirdLargest(int[] nums) {
    if (nums.length < 3) {
        throw new IllegalArgumentException("Dataset should have at least three numbers.");
    }

    int first = Integer.MIN_VALUE;
    int second = Integer.MIN_VALUE;
    int third = Integer.MIN_VALUE;

    for (int num : nums) {
        if (num > first) {
            third = second;
            second = first;
            first = num;
        } else if (num > second) {
            third = second;
            second = num;
        } else if (num > third) {
            third = num;
        }
    }

    return third;
}
```

---
## Priority Queue

A priority queue is a data structure that maintains a set of elements with associated priorities. Elements are removed from the queue based on their priority. In Java, the `PriorityQueue` class is provided in the `java.util` package to implement a priority queue. It uses a heap data structure internally to efficiently manage the elements.

Here's how you can use the `PriorityQueue` class in Java and some of its methods:

1. **Import the PriorityQueue class:**
   
   First, make sure to import the `PriorityQueue` class:

   ```java
   import java.util.PriorityQueue;
   ```

2. **Create a Priority Queue:**

   You can create a priority queue by specifying its initial capacity and providing a comparator (if needed) to determine the order of elements. If you don't provide a comparator, the natural ordering of elements is used.

   ```java
   PriorityQueue<Integer> priorityQueue = new PriorityQueue<>();
   ```

3. **Adding Elements:**

   You can add elements to the priority queue using the `add()` or `offer()` methods:

   ```java
   priorityQueue.add(10);
   priorityQueue.offer(20);
   ```

4. **Removing Elements:**

   The `poll()` method is used to remove and return the element with the highest priority (smallest value). If the priority queue is empty, `poll()` returns `null`.

   ```java
   Integer highestPriority = priorityQueue.poll();
   ```

5. **Peeking:**

   The `peek()` method returns the element with the highest priority (smallest value) without removing it. If the priority queue is empty, `peek()` returns `null`.

   ```java
   Integer highestPriority = priorityQueue.peek();
   ```

6. **Size:**

   The `size()` method returns the number of elements in the priority queue.

   ```java
   int queueSize = priorityQueue.size();
   ```

7. **Custom Comparator:**

   You can provide a custom comparator when creating the priority queue to specify the ordering of elements:

   ```java
   PriorityQueue<Integer> customPriorityQueue = new PriorityQueue<>((a, b) -> b - a);
   ```

8. **Using Objects with Comparable:**

   If you're using custom objects, you can make your objects implement the `Comparable` interface and define the natural ordering:

   ```java
   class CustomObject implements Comparable<CustomObject> {
       // ...

       @Override
       public int compareTo(CustomObject other) {
           // Implement comparison logic here
       }
   }
   ```

Remember that the `PriorityQueue` class is a min-heap implementation, meaning elements with higher priority (smaller value) will be at the front of the queue.

These are some of the basic methods and usage patterns of the `PriorityQueue` class in Java. You can explore additional methods and features in the official Java documentation for the `PriorityQueue` class.

---
## Snake and Ladders problem

1. Modules: Snake, Ladder, Dice 
2. Conditions: (Only if multiplayer mode)
   > 1. Ladder gets a double chance
   > 2. 6 on a dice gets a double chance
3. **IF MULTIPLAYER:**
>    1. Class snakes_ladders
>    2. Object attributes: Position, Dice (Initialized with a random function which throws a number between 1 to 6)


```java
import java.util.LinkedList;
import java.util.Queue;

public class SnakeAndLaddersBFS {
    static class Cell {
        int position;
        int moves;

        Cell(int position, int moves) {
            this.position = position;
            this.moves = moves;
        }
    }

    public static void main(String[] args) {
        int[] moves = new int[101];  // Array to store movement due to snake/ladder

        // Initialize moves array based on snakes and ladders

        int finalPosition = 100;
        Queue<Cell> queue = new LinkedList<>();
        boolean[] visited = new boolean[finalPosition + 1];

        queue.offer(new Cell(1, 0));
        visited[1] = true;

        while (!queue.isEmpty()) {
            Cell current = queue.poll();

            if (current.position == finalPosition) {
                System.out.println("Minimum moves required: " + current.moves);
                break;
            }

            for (int i = 1; i <= 6; i++) {
                int nextPosition = current.position + i;

                if (nextPosition <= finalPosition && !visited[nextPosition]) {
                    visited[nextPosition] = true;

                    // If there's a snake or ladder at the next position
                    if (moves[nextPosition] != 0) {
                        nextPosition = moves[nextPosition];
                    }

                    queue.offer(new Cell(nextPosition, current.moves + 1));
                }
            }
        }
    }
}
```

---
