---
share: true
---
## Dynamic Array vs. Static Array

A dynamic array, also known as a resizable array or Array List in Java, is a data structure that can grow or shrink in size during runtime. It provides a flexible way to store elements of the same data type, much like a regular array. The key difference is that a dynamic array can dynamically resize itself to accommodate more elements as needed.

In Java, the `ArrayList` class from the `java.util` package is an example of a dynamic array. It allows you to add, remove, and access elements while automatically handling the resizing of the underlying array.

On the other hand, a static array has a fixed size determined at the time of its creation. The size cannot be changed after initialization. Static arrays in Java are declared with a fixed size using square brackets, such as `int[] staticArray = new int[10];`.

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

## Hashing Concepts

Hashing is a fundamental concept in computer science used to map data of arbitrary size to fixed-size values (usually integers), which are typically used as indexes or keys in data structures. Hashing is widely used in various applications such as data retrieval, encryption, and checking data integrity.

A hash function takes an input (or 'message') and returns a fixed-size string of characters, which is typically a numeric value. The output, known as a hash code or hash value, should have the following properties:

1. Deterministic: The same input will always produce the same hash value.
2. Fast Computation: The hash function should be efficient to compute.
3. Avalanche Effect: A small change in the input should result in a significantly different hash value.
4. Pre-image Resistance: Given a hash value, it should be computationally infeasible to find the original input.

In data structures like hash tables, hash codes are used to index and quickly retrieve data. Collisions, which occur when two different inputs produce the same hash value, are a common concern when designing hash functions. Techniques like chaining or open addressing are used to handle collisions.

---
