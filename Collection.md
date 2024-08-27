##### <span style="color:orange">Collections: Lesson</span>

![[Screenshot 2024-08-16 at 08.15.17.png]]

The [collections](https://www.codecademy.com/resources/docs/java/collections) framework provides data structures (through [interfaces](https://www.codecademy.com/resources/docs/java/interfaces) and implementing classes) and algorithms, which perform common tasks on collections. The collections framework allows us to focus on the important parts of our program and not on low-level implementation details (like needing to implement a dynamic sizing collection).

The collections framework provides a hierarchical relationship between its interfaces, making the various implementations compatible with each other and thus making our code scalable and flexible. All the interfaces in the collections framework are generic, which allows us to use optimized and tested “plumbing” for our specific [data types](https://www.codecademy.com/resources/docs/java/data-types).

##### <span style="color:orange">List</span>
One of the core interfaces is the `List` interface. A `List` is a collection where elements are ordered in a sequence. `List`s allow us to have duplicate elements and fine-grain control over where elements are inserted in the sequence. Like [arrays](https://www.codecademy.com/resources/docs/java/arrays), the position of a `List` is known as the _index_ and is `0` based. Unlike arrays, which have a static size, `List`s are dynamically sized.

The `ArrayList` is the overall preferred implementation for most use cases but the `LinkedList` performs better than an `ArrayList` if your program mostly inserts and deletes elements at the beginning or end of a list.

```java
List<Integer> intList = new ArrayList<>(); // Empty `List`  
intList.add(4); // 4  
intList.add(6); // 4, 6  
intList.add(3); // 4, 6, 3  
intList.set(1, 3); // 4, 3, 3  
  
int a = intList.get(2); // a = 3  
// get the first occurance of 3
int b = intList.indexOf(3); // b = 1  

//returns a sublist in a new `List` with the elements specified by the starting index `1` (inclusive) and ending index `3` (exclusive).
List<Integer> subIntList = intList.subList(1,3); // subIntList -> 3, 3
```

Whats the story with this?
```java
List<Integer> intList = new ArrayList<>(); // Empty `List` 
```

1. **List and ArrayList:**

• List is an **interface** in Java that represents an ordered collection (also known as a sequence). It provides methods for adding, removing, and accessing elements in the collection.

• ArrayList is a **concrete class** that implements the List interface. It provides a resizable array implementation of the List interface.

2. **Programming to an Interface:**

• When you write List `integer` intList, you’re saying that intList is a reference to an object that implements the List interface. The actual object that intList refers to is an instance of ArrayList.

• This allows you to use any class that implements List (like ArrayList, LinkedList, Vector, etc.) without changing the code that interacts with intList. This makes your code more flexible and easier to maintain.

More concrete example
```java
public class Example {
    public static void main(String[] args) {
        List<Integer> intList = new ArrayList<>(); // Initially, using ArrayList

        intList.add(1);
        intList.add(2);
        intList.add(3);

        System.out.println(intList); // Outputs: [1, 2, 3]

        // Later, you decide to change the implementation to LinkedList
        intList = new LinkedList<>(intList); // Reusing the elements

        System.out.println(intList); // Still works, and outputs: [1, 2, 3]
    }
}
```

##### <span style="color:orange">Sets</span>
A `Set` is a collection of unique elements and all of its [methods](https://www.codecademy.com/resources/docs/java/methods) ensure this stays true.

The [`HashSet`](https://www.codecademy.com/resources/docs/java/hashset?page_ref=catalog) implementation has the best performance when retrieving or inserting elements but cannot guarantee any ordering among them.

The [`TreeSet`](https://www.codecademy.com/resources/docs/java/set/treeset) implementation does not perform as well on insertion and deletion of elements but does keep the elements stored in order based on their values (this can be customized).

The `LinkedHashSet` implementation has a slightly slower performance on insertion and deletion of elements than a `HashSet` but keeps elements in insertion order.

##### <span style="color:orange">Queue</span>
The [`Queue`](https://www.codecademy.com/resources/docs/java/queue?page_ref=catalog) core interface in the [collections](https://www.codecademy.com/resources/docs/java/collections) framework is a collection that implements the Queue data structure. A `Queue` is a First In First Out (FIFO) data structure in which elements are inserted at the _tail_ (back) of the collection and removed from the _head_ (front).

A `Queue` has two types of access [methods](https://www.codecademy.com/resources/docs/java/methods) for inserting, removing, and getting (but not removing) the element at the head of the `Queue`.

The following methods throw an exception when:

- `add()` - there is no space for the element
- `remove()` - there are no elements to remove
- `element()` - there are no elements to get

The following methods `return` a special value:

- `offer()` - `false` there is no space for the element
- `poll()` - `null` there are no elements to remove
- `peek()` - `null` there are no elements to get

##### <span style="color:orange">Deque</span>
*(pronounced “Deck”)*

A deque (short for “double-ended queue”) is a type of queue that allows us to access elements from the front and the back of the queue. The `Deque` interface has two types of [methods](https://www.codecademy.com/resources/docs/java/methods) for manipulating the front and back of the collection.

- `addFirst()`, `addLast()` - there is no space to add an element.
- `removeFirst()`, `removeLast()` - there is no element to remove.
- `getFirst()`, `getLast()` - there is no element to get.
- 
The following methods return a special value:

- `offerFirst()`, `offerLast()` - `false` when there is no space to add an element.
- `pollFirst()`, `pollLast()` - `null` when there is no element to remove.
- `peekFirst()`, `peekLast()` - `null` when there is no element to get.

The `LinkedList`, although not the most optimized, is flexible enough to not only be used as a `List` and [`Queue`](https://www.codecademy.com/resources/docs/java/queue?page_ref=catalog), but also a `Deque`. The `ArrayDeque` is the preferred implementation when needing to manipulate elements at the front and back of a collection

```java
import java.util.Deque;
import java.util.ArrayDeque;
import java.util.List;
import java.util.ArrayList;

public class Main {
  public static void main(String[] args) {
    List<Integer> myInts = new ArrayList<>();
    myInts.add(9);
    myInts.add(13);
    myInts.add(2);
    myInts.add(1);
    myInts.add(11);
    myInts.add(39);
    myInts.add(78);
    myInts.add(4);

    Deque<Integer> result = separateInts(myInts);
    for(Integer i: result) {
      System.out.println(i);
    }
  }

  // if its even bring to the front, if its odd move to the back
  public static Deque<Integer> separateInts(List<Integer> integers){
    Deque<Integer> separatedDeque = new ArrayDeque<>();
    for (Integer item: integers){
      if (item % 2 == 0){
        separatedDeque.addFirst(item);
      } else {
        separatedDeque.addLast(item);       
      }
    }
    return separatedDeque;
  }
}
```

Looping through every element 

```java
import java.util.List;
import java.util.ArrayList;
import java.util.Set;
import java.util.HashSet;
import java.util.Queue;
import java.util.LinkedList;
import java.util.Deque;
import java.util.ArrayDeque;

public class Main {
  public static void main(String[] args) {
    List<Integer> intList = new ArrayList<>();
    Set<String> stringSet = new HashSet<>();
    Queue<Double> doubleQueue = new LinkedList<>();
    Deque<Integer> intDeque = new ArrayDeque<>();

    intList.add(5);
    intList.add(8);
    intList.add(5);
    intList.add(1);

    stringSet.add("Hello");
    stringSet.add("World");
    stringSet.add("World");

    doubleQueue.add(3.89);
    doubleQueue.add(889.64);

    intDeque.addFirst(7);
    intDeque.addFirst(8);
    intDeque.addLast(40);

    System.out.println(intList.getClass());
    printList(intList);
    System.out.println();
    System.out.println(stringSet.getClass());
    printSet(stringSet);
    System.out.println();
    System.out.println(doubleQueue.getClass());
    printQueue(doubleQueue);
    System.out.println();
    System.out.println(intDeque.getClass());
    printDeque(intDeque);
  }

	// this interface saved all the code below
	private static <T> void printCollection(Collection<T> collection) {
		for (T item: collection){
			System.out.println(item);
	}

}

//Each method is tailored to a specific type, but this results in code repetition. By using the Collection<T> interface, you avoid this redundancy because all of these types share a common interface (Collection).

/*
  private static <T> void printList(List<T> list) {
    for (T item: list) {
      System.out.println(item);
    }
  }

  private static <T> void printSet(Set<T> set) {
    for (T item: set) {
      System.out.println(item);
    }
  }

  private static <T> void printQueue(Queue<T> queue) {
    for (T item: queue) {
      System.out.println(item);
    }
  }

  private static <T> void printDeque(Deque<T> deque) {
    for (T item: deque) {
      System.out.println(item);
    }
  }
  */
}
```