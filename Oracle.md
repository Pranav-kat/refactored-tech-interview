---
share: true
---
## Normalization in DBMS with Examples

Normalization in DBMS is the process of organizing database tables to reduce data redundancy and improve data integrity. It involves breaking down larger tables into smaller, more manageable ones. The main normalization forms are:

1. First Normal Form (1NF): Ensures atomicity of data by eliminating repeating groups. Example: Storing multiple phone numbers in a single field.

2. Second Normal Form (2NF): Ensures that non-key attributes depend on the entire primary key. Example: A table with order details and customer information where customer details repeat for each order.

3. Third Normal Form (3NF): Eliminates transitive dependencies, ensuring that non-key attributes depend only on the primary key. Example: A table with product details and supplier information where supplier details repeat for each product.

## Different Sorting Algorithms and Their Implementation in Real Life

Various sorting algorithms, such as Bubble Sort, Insertion Sort, Merge Sort, Quick Sort, and Heap Sort, arrange elements in ascending or descending order. In real life, sorting algorithms are used in tasks like organizing data, finding the highest or lowest value, displaying rankings, and optimizing search operations.

## Doubly Linked List with Real-Time Examples

A doubly linked list is a data structure where each node contains data and two pointers, one to the next node and another to the previous node. A real-time example of a doubly linked list is a browser's backward and forward navigation. Each page visited is a node, and the backward and forward buttons use the pointers to traverse the visited pages.

## Difference Between UNION and UNION ALL

UNION and UNION ALL are used to combine the results of two or more SELECT queries:

- UNION: It returns distinct rows by removing duplicates from the combined result set. Example: SELECT col1 FROM table1 UNION SELECT col1 FROM table2;

- UNION ALL: It returns all rows from the combined result set, including duplicates. Example: SELECT col1 FROM table1 UNION ALL SELECT col1 FROM table2;

## Difference Between UNION and JOIN

UNION and JOIN are used for different purposes in SQL:

- UNION: Combines the results of two or more SELECT queries with compatible column types. It is used to stack rows vertically.

- JOIN: Combines rows from two or more tables based on a related column. It is used to retrieve data from multiple tables based on a common field.

## Different Types of JOIN with Examples

Different types of JOIN in SQL are:

- INNER JOIN: Returns rows with matching values in both tables. Example: SELECT * FROM customers INNER JOIN orders ON customers.customer_id = orders.customer_id;

- LEFT JOIN (or LEFT OUTER JOIN): Returns all rows from the left table and matching rows from the right table. Example: SELECT * FROM employees LEFT JOIN departments ON employees.department_id = departments.department_id;

- RIGHT JOIN (or RIGHT OUTER JOIN): Returns all rows from the right table and matching rows from the left table. Example: SELECT * FROM employees RIGHT JOIN departments ON employees.department_id = departments.department_id;

- FULL JOIN (or FULL OUTER JOIN): Returns all rows when there is a match in either the left or right table. Example: SELECT * FROM employees FULL JOIN departments ON employees.department_id = departments.department_id;

# Short and Concise Answers

## Different Server Technologies

Some different server technologies are:
- Apache HTTP Server: A popular open-source web server software.
- Nginx: A lightweight and high-performance web server.
- Microsoft Internet Information Services (IIS): A web server for Windows servers.
- Node.js: A runtime environment for server-side JavaScript.
- Tomcat: An open-source application server for Java Servlets and JSP.
- Django: A Python web framework with a built-in development server.
- Flask: A lightweight Python web framework.
- Ruby on Rails: A web framework for Ruby language.

## JDK Architecture

JDK (Java Development Kit) architecture includes:
1. Java Development Tools: Compiler (javac), Debugger (jdb), etc.
2. Java Runtime Environment (JRE): JVM (Java Virtual Machine) to run Java programs.
3. Java API: Core libraries for various functionalities like I/O, collections, etc.

## Different Types of Data Structures

Some different types of data structures are:
1. Arrays
2. Linked Lists
3. Stacks
4. Queues
5. Trees
6. Graphs
7. Hash Tables
8. Heaps

## Difference Between Arrays and Linked Lists

Arrays:
- Fixed size (static).
- Contiguous block of memory.
- Access time for elements is O(1).
- Insertion and deletion are O(n) as shifting is required.

Linked Lists:
- Dynamic size (can grow).
- Elements stored in separate memory locations (nodes) connected via pointers.
- Access time for elements is O(n) as traversal is required.
- Insertion and deletion are O(1) for singly linked lists (with access to the node to be modified) and O(n) for doubly linked lists.

## Code to Insert Element in Sorted Linked List

```java
class SortedLinkedList {
    Node head;

    void insert(int data) {
        Node newNode = new Node(data);
        if (head == null || data < head.data) {
            newNode.next = head;
            head = newNode;
        } else {
            Node current = head;
            while (current.next != null && current.next.data < data) {
                current = current.next;
            }
            newNode.next = current.next;
            current.next = newNode;
        }
    }
}
```

# Short and Concise Answers

## Multithreading in Java

Multithreading is the simultaneous execution of multiple threads within a single process. In Java, you can achieve multithreading in two ways:
1. Extending the Thread class: Create a class that extends the Thread class and override the `run()` method with the code to be executed in the thread.
2. Implementing the Runnable interface: Create a class that implements the Runnable interface and implement the `run()` method. Then, create a Thread object and pass the Runnable object as a target to the Thread constructor.

## Try Block Without Catch Block

Yes, you can have a try block without a catch block. It is allowed to have a try block followed by a finally block without a catch block. The finally block is executed regardless of whether an exception occurs or not.

Follow-up: The finally block gets executed in the following scenarios:
- When an exception is thrown and caught by a catch block.
- When an exception is thrown but not caught (propagated up the call stack).
- When there is no exception and normal execution completes.

## OOPS Concepts in Java

1. Encapsulation: The bundling of data (attributes) and methods that operate on the data within a single unit (class). Access to the data is controlled through methods.

2. Inheritance: The process of creating a new class (subclass) from an existing class (superclass), inheriting its properties and behaviors.

3. Polymorphism: The ability of a class to take on multiple forms. It is achieved through method overloading (compile-time polymorphism) and method overriding (runtime polymorphism).

4. Abstraction: Hiding the implementation details and exposing only essential features to the user. Abstract classes and interfaces are used to achieve abstraction.

## Collections in Java

Collections in Java are frameworks that provide classes and interfaces to store and manage groups of objects. They offer various data structures like lists, sets, maps, etc. to manipulate collections of objects easily and efficiently.

## Hashing

Hashing is the process of converting input data (keys) into a fixed-size hash value (hash code) using a hash function. It is commonly used in data structures like hash tables to quickly retrieve and store data.

## Primary and Secondary Index in DBMS

In DBMS, an index is a data structure that improves the speed of data retrieval. 
- Primary Index: It is created on the primary key of a table. There is only one primary index per table, and it organizes data for fast access using the primary key.
- Secondary Index: It is created on non-primary key attributes. A table can have multiple secondary indexes, and they provide additional ways to access data.

## DDL and DML Statements with Examples

DDL (Data Definition Language) statements are used to define and manage database objects like tables, views, indexes, etc. Examples include `CREATE`, `ALTER`, and `DROP` statements.

DML (Data Manipulation Language) statements are used to manipulate data stored in the database. Examples include `SELECT`, `INSERT`, `UPDATE`, and `DELETE` statements.

## finalize() Method in Java

`finalize()` is a method in Java's Object class. It is called by the garbage collector before reclaiming an object's memory when it is no longer reachable. However, `finalize()` is considered outdated, and it is not recommended to rely on it for cleanup tasks. Instead, developers should use `try-with-resources` or explicitly manage resources using `close()` methods for better memory management.
