---
share: true
---

## Graph

A graph is a data structure consisting of a set of nodes (vertices) connected by edges. Nodes can represent entities, and edges depict relationships between those entities. Graphs are used to model various real-world scenarios, such as social networks and transportation systems.

## Difference Between Tree and Graph

Tree:
- A type of graph with a hierarchical structure.
- One root node, every node has at most one parent.
- No cycles (loops) allowed.
- Used for representation and hierarchy, e.g., file systems.

Graph:
- A general structure with nodes and edges.
- No restrictions on node connections.
- May contain cycles.
- Used for modeling complex relationships, e.g., social networks.

## Difference Between Tree and Binary Tree

Binary Tree:
- A type of tree where each node has at most two child nodes.
- Can be categorized as complete, full, or balanced.
- Used for efficient data search and manipulation.

Tree:
- A broader structure with hierarchical relationships.
- Nodes can have any number of child nodes.
- Used for representing hierarchies and relationships.

## Difference Between Queue and Stack

Queue:
- Follows FIFO (First-In-First-Out) order.
- Elements are added at the rear (enqueue) and removed from the front (dequeue).
- Used for tasks like managing requests, breadth-first search.

Stack:
- Follows LIFO (Last-In-First-Out) order.
- Elements are added and removed from the top.
- Used for tasks like function calls, depth-first search.

## Procedure to Implement Queue Using Array

To implement a queue using an array:
1. Define an array to store the queue elements and two pointers: front and rear.
2. Initialize front and rear pointers to -1.
3. Implement enqueue operation:
   - Increment the rear pointer.
   - Add the new element to the rear of the array.
4. Implement dequeue operation:
   - If front is equal to rear, the queue is empty.
   - Otherwise, increment the front pointer.
5. Implement other necessary methods like isEmpty and isFull.

Example (in Python):
```python
class Queue:
    def __init__(self, capacity):
        self.capacity = capacity
        self.queue = [None] * capacity
        self.front = self.rear = -1

    def enqueue(self, item):
        if self.rear == self.capacity - 1:
            print("Queue is full.")
        else:
            self.rear += 1
            self.queue[self.rear] = item

    def dequeue(self):
        if self.front == self.rear:
            print("Queue is empty.")
        else:
            self.front += 1
            return self.queue[self.front]

    def isEmpty(self):
        return self.front == self.rear

    def isFull(self):
        return self.rear == self.capacity - 1
```
## Normalization and Anomalies

Normalization is the process of structuring a relational database to minimize data redundancy and maintain data integrity. It involves organizing data into multiple tables with defined relationships.

Anomalies in database design:

1. Insertion Anomaly: Difficulty inserting data due to missing values in certain columns that depend on other columns.
2. Update Anomaly: Inconsistencies that occur when data is updated in one place but not in related places.
3. Deletion Anomaly: Loss of necessary data unintentionally when deleting certain records.

## B-Tree

A B-tree is a self-balancing tree data structure used in databases and file systems. It is designed to keep data sorted and allows efficient insertion, deletion, and search operations. B-trees are commonly used in database index structures to speed up data retrieval.

## Index in DBMS

An index in a DBMS is a data structure that improves the speed of data retrieval operations on a database table. It acts like an index in a book, providing a way to quickly access specific rows based on certain columns. Indexes enhance query performance but require additional storage space and maintenance.