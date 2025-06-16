# Java-

### List
#### Question 80: What are the benefits of using "Generics" with "List"?
Answer: Generics provide type safety. They ensure that you insert only the specified type of objects into your list. This reduces bugs and eliminates the need for typecasting.

When retrieving values from a generic List, you don't need to cast them.

List<String> names = new ArrayList<>();

String name = names.get(0);  // ✅ No cast needed

Without generics:

List names = new ArrayList();

String name = (String) names.get(0);  // ❗ Must cast

#### Question 79: How can you synchronize a "List"?
Answer:
List<String> syncList = Collections.synchronizedList(new ArrayList<String>());

Extra Notes: -

Thread-safe operations:
Synchronization ensures that all operations on the list (like adding, removing, getting elements, etc.) are atomic, meaning they are treated as a single, indivisible unit. This prevents race conditions where one thread might modify the list while another is reading or iterating through it. 
Locking mechanisms:
Synchronization often involves using locking mechanisms to control access to the list. When one thread is accessing the list, other threads are blocked until the first thread completes its operation, preventing conflicts. 
Using synchronized collections:
Many programming languages provide built-in synchronized versions of lists (like java.util.Collections.synchronizedList() in Java). These collections automatically handle the synchronization, making it easier to work with threads safely. 

#### Question 78: What is the 'subList' method in List?
Answer: The subList method creates a view of the portion of this list between the specified fromIndex, inclusive, and toIndex, exclusive.
The subList() method returns a new list (referred to as a sublist) which contains the items of the list between two indices.

Note: The item at the last index is not included in the sublist.

Note: The sublist is a view of the original list, which means that changing the sublist also changes the original list.

Syntax public List sublist(int start, int end)

#### Question 77: Compare Iterator and "ListIterator".
Answer:
Iterator: Can traverse the list in the forward direction only.
ListIterator: Can traverse the list in either direction, modify the list during iteration, and obtain the iterator’s current position in the list.

##### Iterator
Purpose: Iterates through elements of any collection (like ArrayList, HashSet, etc.) in a forward direction.
Methods: hasNext(), next(), remove() (optional).
Usage: Primarily for accessing elements and potentially removing them during iteration.
Example: 
import java.util.ArrayList;
import java.util.Iterator;
import java.util.List;

public class IteratorExample {

    public static void main(String[] args) {
    
        List<String> list = new ArrayList<>();
        list.add("apple");
        list.add("banana");
        list.add("cherry");

        Iterator<String> iterator = list.iterator();
        while (iterator.hasNext()) {
            String element = iterator.next();
            System.out.println(element);
        }
    }
}

##### ListIterator
Purpose:
Iterates through elements of a list in both forward and backward directions.
Methods:
hasNext(), next(), hasPrevious(), previous(), add(), set(), remove(), nextIndex(), previousIndex() (all from Iterator are also available).
Usage:
Offers more flexibility for traversing and modifying list elements during iteration.
Example: 

import java.util.ArrayList;
import java.util.List;
import java.util.ListIterator;

public class ListIteratorExample {
    public static void main(String[] args) {
        List<String> list = new ArrayList<>();
        list.add("apple");
        list.add("banana");
        list.add("cherry");

        ListIterator<String> listIterator = list.listIterator();

        // Forward iteration
        while (listIterator.hasNext()) {
            System.out.println("Forward: " + listIterator.next());
        }

        // Backward iteration
        while (listIterator.hasPrevious()) {
            System.out.println("Backward: " + listIterator.previous());
        }
    }
}

#### Question 76: How do you convert a List to an array?
Answer:
String[] array = list.toArray(new String[list.size()]);

#### Question 75: What are "Vector" and "Stack" classes?
Answer:
Vector: Similar to ArrayList, but it is synchronized.
Stack: Extends Vector with five operations that allow a vector to be treated as a stack.

##### Stack:
The Java Collection framework provides a Stack class, which implements a Stack data structure. The class is based on the basic principle of LIFO (last-in-first-out). Besides the basic push and pop operations, the class also provides three more functions, such as empty, search, and peek.

The Stack class extends Vector and provides additional functionality for stack operations, such as push, pop, peek, empty, and search.
The Stack class can be considered as a subclass of Vector because it inherits all of its methods and properties.

// Java Program Implementing Stack Class
import java.util.Stack;
public class Geeks 
{
    public static void main(String[] args) 
    {
        // Create a new stack
        Stack<Integer> s = new Stack<>();
        // Push elements onto the stack
        s.push(1);
        s.push(2);
        s.push(3);
        s.push(4);
        // Pop elements from the stack
        while(!s.isEmpty()) {
            System.out.println(s.pop());
        }
    }
}

##### Vector: 

The Vector class in Java implements a growable array of objects. Vectors were legacy classes, but now it is fully compatible with collections.
Key Features of Vector:

1.It expands as elements are added.
2.Vector class is synchronized in nature means it is thread-safe by default.
3.Like an ArrayList, it maintains insertion order.
4.It allows duplicates and nulls.
5.It implements List, RandomAccess, Cloneable, and Serializable.

Vector Class Declaration
public class Vector<E> extends AbstractList<E> implements List<E>, RandomAccess, Cloneable, Serializable

Here, E is the type of element.
It extends AbstractList and implements List interfaces.
It implements Serializable, Cloneable, Iterable<E>, Collection<E>, List<E>, RandomAccess interfaces.
The directly known subclass is Stack.

// Java Program Implementing Vector
import java.util.Vector;

public class Geeks
{
    public static void main(String[] args) 
    {
        // Create a new vector
        Vector<Integer> v = new Vector<>(3, 2);

        // Add elements to the vector
        v.addElement(1);
        v.addElement(2);
        v.addElement(3);

        // Insert an element at index 1
        v.insertElementAt(0, 1);

        // Remove the element at index 2
        v.removeElementAt(2);

        // Print the elements of the vector
        for (int i : v) {
            System.out.println(i);
        }
    }
}

##### Purpose to use Vector" classes in java
Vector classes in Java serve as dynamic arrays, capable of growing or shrinking in size as needed. They are part of the Java Collections Framework and implement the List interface, providing a way to store elements sequentially, similar to an array, but with the added flexibility of being able to adjust its size dynamically. 

##### Difference between arraylist and vector in java
1. Synchronization:
ArrayList is not synchronized, meaning it is not thread-safe. Multiple threads can access and modify an ArrayList concurrently, which can lead to data corruption if not handled carefully.
Vector is synchronized, making it thread-safe. Only one thread can access a Vector at a time, preventing race conditions and data corruption in multi-threaded environments.
2. Growth:
ArrayList increases its capacity by 50% when it needs to grow.
Vector doubles its capacity when it needs to grow.
3. Performance:
ArrayList generally offers better performance than Vector in single-threaded environments because it is not synchronized. The overhead of synchronization in Vector can slow down operations.
Vector is slower than ArrayList due to the synchronization overhead, but it is suitable for multi-threaded environments where thread safety is crucial.
4. Legacy:
ArrayList is not a legacy class and was introduced in Java 1.2 as part of the collections framework.
Vector is a legacy class and was part of the original Java 1.0 release.
5. Traversal:
ArrayList can be traversed using an Iterator.
Vector can be traversed using both an Iterator and Enumerator.

#### Question 74: How do you remove elements from a List?
Answer: Elements can be removed from a list using the remove() method. It can be called using an element or using an index:

list.remove("apple");  // removes "apple" from list
list.remove(0);       // removes the first element

#### Question 73: What is the difference between "ArrayList" and "LinkedList"?
ArrayList:
Underlying Structure: Dynamic array (resizable array). 
Random Access: Fast (O(1)) due to direct indexing into the array. 
Insertions/Deletions: Slower (O(n)) if elements need to be shifted after an insertion or removal in the middle. 
Memory Usage: May be slightly less memory overhead due to the simple array structure. 
Suitable for: Scenarios where random access is frequent and insertions/deletions are infrequent. 
LinkedList:
Underlying Structure: Doubly linked list (each element points to the next and previous element). 
Random Access: Slower (O(n)) because you have to traverse from the beginning. 
Insertions/Deletions: Fast (O(1)) because only pointers need to be updated. 
Memory Usage: Higher memory overhead due to additional node references. 
Suitable for: Scenarios where frequent insertions/deletions are required, especially in the middle of the list. 

https://rameshfadatare.medium.com/difference-between-arraylist-and-linkedlist-in-java-ea609090c361

#### Question 72: How do you iterate over a "List"?
List<String> list = Arrays.asList("apple", "banana", "cherry");
for(String fruit : list) {
    System.out.println(fruit);
}

#### Question 71: What is the "List" interface in Java?
Answer: The List interface is part of the Java Collections Framework and it represents an ordered collection (also known as a sequence). The user can access elements by their integer index (position in the list), and search for elements in the list.

### JDBC
#### Question 70: What is Connection Pooling?
Answer: Connection pooling is a technique used to improve performance in applications that need to make calls to a database by reusing the connections instead of creating a new one each time.
Connection pooling is a technique used to efficiently manage database connections by reusing them instead of opening and closing a new connection for each database operation. It involves maintaining a pool of pre-established connections, which can be borrowed by applications needing to interact with the database, and then returned to the pool after use. This approach minimizes the overhead associated with creating and destroying connections, improving performance, especially in applications with high database traffic. 

#### Question 69: How do you handle SQL exceptions?
Answer:
try {
    // code that may throw SQLException
} catch (SQLException ex) {
    // handle exception
}

#### Question 68: Explain the types of JDBC drivers.
Answer: There are four types of JDBC drivers:

Type 1: JDBC-ODBC bridge
Type 2: Native-API/partly Java driver
Type 3: Net-protocol/all-Java driver
Type 4: Native-protocol/all-Java driver

1. Type 1 (JDBC-ODBC Bridge): 
Uses ODBC (Open Database Connectivity) to connect to the database. 
Requires a separate ODBC driver for each database, making it less portable. 
Has generally poor performance due to the translation overhead of using ODBC. 
Often considered deprecated and is less commonly used today.

2. Type 2 (Native-API Driver): 
Uses a database-specific native API to connect to the database. 
Requires the database vendor's client libraries on the application server. 
Offers better performance than Type 1, but still involves some overhead. 
May be more database-specific than Type 1.

3. Type 3 (Network Protocol/Middleware Driver): 
Uses a database-independent network protocol and middleware to connect to the database. 
Requires a middleware server between the application and the database. 
Provides a degree of abstraction and can support multiple databases. 
Can have performance overhead due to the middleware layer. 

4. Type 4 (Thin/Direct-to-Database Driver): 
Uses a direct, pure Java implementation to connect to the database.
Does not rely on any external client libraries or middleware.
Offers the best performance among the driver types.
Requires a specific database-vendor protocol implementation in Java.

#### Question 67: What do you mean by batch processing in JDBC?
Answer: Batch processing in JDBC is used to execute multiple SQL statements as a single batch, which reduces the number of communication rounds between the application and the database server.

#### Question 66: What is "ResultSet" in JDBC?
Answer: ResultSet is a table of data representing a database result set, which is generated by executing a statement that queries the database.

#### Question 65: How do you execute a query in JDBC?
Statement stmt = conn.createStatement();
ResultSet rs = stmt.executeQuery("SELECT * FROM myTable");

#### Question 64: What are "Statement" and "PreparedStatement"?
Answer:
Statement: Used to execute a simple SQL query with no parameters.
PreparedStatement: Used for executing SQL statements multiple times or when you need to bind parameters to the query.

#### Question 63: How do you connect to a database in Java?
Connection conn = DriverManager.getConnection("jdbc:subprotocol:subname", "user", "password");

#### Question 62: What are the core components of JDBC?
Answer: The core components of JDBC include DriverManager, Driver, Connection, Statement, ResultSet, and SQLException.

#### Question 61: What is JDBC?
Answer: JDBC (Java Database Connectivity) is an API that enables Java programs to execute SQL statements. This allows Java applications to interact with any SQL-compliant database.


### Stream API
### Question 51: What is the Stream API in Java?
Answer: The Stream API in Java provides a new abstraction called Stream, which allows you to process data in a declarative way. It supports operations like map, filter, limit, reduce, find, match, and sort, on collections of objects.

#### Question 52: What are the benefits of using Streams?
Answer: Streams can make the code more concise and readable. They can simplify code to perform bulk operations sequentially or parallelly. Streams don't store data and, instead, operate on the source data structures (e.g., collections) directly.

#### Question 53: How do you obtain a Stream from a List?
Answer:
List<String> myList = Arrays.asList("a1", "a2", "b1", "c2", "c1");
Stream<String> myStream = myList.stream();

#### Question 54: What is the difference between 'map' and 'flatMap' in Streams?
Answer:
map: It transforms each element in the stream using the given function. It is a one-to-one mapping.
flatMap: It helps in converting one type of stream element into another type and flattens the Stream of Streams into a Stream.

#### Question 55: What is the "filter" method in a "Stream"?
Answer: The filter method is used to evaluate each element in a stream using a predicate. If the predicate evaluates to true, the element is included in the resulting stream.

#### Question 56: How do you sort a "Stream"?
Answer:
List<String> myList = Arrays.asList("a1", "a2", "b1", "c2", "c1");
List<String> sortedList = myList.stream()
    .sorted()
    .collect(Collectors.toList());

#### Question 57: What are terminal operations on "Streams"?
Answer: Terminal operations produce a result from a stream pipeline. Terminal operations include operations like forEach, reduce, collect, and sum.

#### Question 58: What is the "collect" method in "Streams"?
Answer: The collect method is a terminal operation that transforms the elements of a stream into a different kind of result, e.g., a List, a Map, or even an Integer.

#### Question 59: What is the "forEach" operation in "Streams"?
Answer: The forEach operation is used to iterate over each element of the stream. The forEach operation is a terminal operation which means it consumes the stream and can't be used afterwards.

#### Question 60: Explain the "reduce" operation in "Streams".
Answer: The reduce operation combines all elements of the stream into a single result by applying a binary operator. This operation takes two parameters: an initial value, and a binary operator function.
