# Java-

#### Question 80: What are the benefits of using "Generics" with "List"?
Answer: Generics provide type safety. They ensure that you insert only the specified type of objects into your list. This reduces bugs and eliminates the need for typecasting.
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





