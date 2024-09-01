- `binarySearch()`: Performs [binary search](https://www.codecademy.com/learn/fscp-22-search-graph-search-algorithms/modules/wdcp-22-binary-search-and-search-trees/cheatsheet) over a `List` to find the specified object and returns the index if found. This method is overloaded to also accept a [`Comparator`](https://www.codecademy.com/resources/docs/java/comparator) to define a custom ordering policy. Note: this method only provides the correct value if the elements in the `List` are sorted.
- [`max()`](https://www.codecademy.com/resources/docs/java/collections/max?page_ref=catalog): Returns the maximum element in the [`Collection`](https://www.codecademy.com/resources/docs/java/collection?page_ref=catalog). This method is overloaded to also accept a `Comparator` to define a custom ordering policy.
- [`min()`](https://www.codecademy.com/resources/docs/java/collections/min?page_ref=catalog): Returns the minimum element in the `Collection`. This method is overloaded to also accept a `Comparator` to define a custom ordering policy.
- [`reverse()`](https://www.codecademy.com/resources/docs/java/collections/reverse?page_ref=catalog): Reverses the order of elements in the `List` passed in as an argument.
- [`sort()`](https://www.codecademy.com/resources/docs/java/collections/sort?page_ref=catalog): Sorts the `List` passed in as an argument. This method is overloaded to also accept a `Comparator` to define a custom ordering policy.


##### <span style="color:orange">Collections</span>
1. **Adding Elements to** **List** **and** **Set****:**
• You create a List<`Integer`> named myList and add some integers to it.
• You also create a Set<`String`> named mySet and add a couple of strings to it.

2. **Finding the Maximum and Minimum:**
• Collections.max(mySet) is used to find the maximum element in mySet (lexicographically, for strings). Since sets are unordered collections, the “maximum” string will be the one that comes last in alphabetical order.
• Collections.min(myList) finds the minimum integer in myList.

3. **Binary Search:**
• Collections.binarySearch(myList, 57) is used to search for the element 57 in myList. However, binary search requires that the list be sorted beforehand for it to work correctly. Since the list was not sorted before this call, the output might not be as expected. It’s good to sort the list first before performing a binary search.

4. **Reversing and Sorting the List:**
• Collections.reverse(myList) reverses the order of elements in myList.
• Collections.sort(myList) sorts the elements of myList in ascending order.

5. **Printing the Collection:**
• The printCollection(Collection<`?`> collection) method is a generic method that prints out the elements of any Collection using an Iterator.

```java
import java.util.List;
import java.util.ArrayList;
import java.util.Collections;
import java.util.Collection;
import java.util.Set;
import java.util.HashSet;
import java.util.Iterator;

public class Main {
  public static void main(String[] args) {
    List<Integer> myList = new ArrayList<>();
    myList.add(3);
    myList.add(-1);
    myList.add(57);
    myList.add(29);

    Set<String> mySet = new HashSet<>();
    mySet.add("Hello");
    mySet.add("World");

    System.out.println("mySet max: \""+ Collections.max(mySet) + "\"");
    System.out.println();

    System.out.println("myList min: " + Collections.min(myList));
    System.out.println();

    // Sort before performing a binary search
    Collections.sort(myList);
    System.out.println("Index of 57 in myList is: " + Collections.binarySearch(myList, 57));
    System.out.println();

    System.out.println("myList prior to reverse: ");
    printCollection(myList);
    System.out.println();

    Collections.reverse(myList);
    System.out.println("myList reversed: ");
    printCollection(myList);
    System.out.println();

    System.out.println("myList prior to sort: ");
    printCollection(myList);
    System.out.println();

    Collections.sort(myList);
    System.out.println("myList after sort: ");
    printCollection(myList);
  }

  public static void printCollection(Collection<?> collection) {
    Iterator<?> myItr = collection.iterator();
    while (myItr.hasNext()) {
      System.out.println(myItr.next());
    }
  }
}
```


##### <span style="color:orange">Map</span>
[`Map`](https://www.codecademy.com/resources/docs/java/map?page_ref=catalog) defines a generic interface for an object that holds key-value pairs as elements. The _key_ is used to retrieve some value (like the index in an array or `List`). A key must be unique and map to exactly one value.

The `HashMap` defines no specific ordering for the keys and is the most optimized implementation for retrieving values. This is Java’s implementation of a [hash table](https://www.codecademy.com/resources/docs/general/data-structures/hash-table?page_ref=catalog).

A `Map` has the following [methods](https://www.codecademy.com/resources/docs/java/methods) for accessing its elements:
- `put()`: Sets the value that a key maps to. Note that this method replaces the value a key mapped to if the key was already present in the `Map`.

- `get()`: Gets, but does not remove, the value the provided key argument points to if it exists. This method returns `null` if the key is not in the `Map`.  
Let’s see how we can use them:

```java
import java.util.List;
import java.util.ArrayList;
import java.util.Map;
import java.util.HashMap;
import java.util.Random;

public class Main {
  public static void main(String[] args) {
    List<Integer> myInts = new ArrayList<>();
    Random random = new Random();

    for(int i = 0; i < 20; i++) {
      myInts.add(random.nextInt(5)); // Generates numbers between 0 and 4
    }

    System.out.println("myInts: " + myInts);

    Map<Integer, Integer> intCount = countNumbers(myInts);
    for(Map.Entry<Integer, Integer> entry: intCount.entrySet()) {
      System.out.println("Integer: " + entry.getKey() + " appears: " + entry.getValue() + " times");
    }
  }
	// looping through the list and count the occurance 
  public static Map<Integer, Integer> countNumbers(List<Integer> list) {
    Map<Integer, Integer> intCount = new HashMap<>();
    for (int element : list) {
        if (intCount.containsKey(element)) {
            intCount.put(element, intCount.get(element) + 1);
        } else {
            intCount.put(element, 1);
        }
    }
    return intCount;
  }
}
```


##### <span style="color:orange">Understanding Map.Entry</span>
• `Map.Entry<K, V>`: This is an interface nested inside the Map interface. It represents a key-value pair within the Map.
• `K` is the type of keys maintained by the map.
• `V` is the type of mapped values.
• **Why use** `Map.Entry<K, V>?`: When you want to iterate over the entries (i.e., the key-value pairs) in a Map, each entry can be represented as a Map.Entry<K, V> object. This allows you to access both the key and the value in each iteration.


**Understanding entrySet():**
• **entrySet()**: This method returns a Set of Map.Entry<K, V> objects. Each entry in this set is a key-value pair from the Map.
• By iterating over this Set, you can access each key-value pair in the Map.

```java
for (Map.Entry<Integer, Integer> entry : intCount.entrySet()) {
    System.out.println("Integer: " + entry.getKey() + " appears: " + entry.getValue() + " times");
}
```

**Key Differences Between Map and Other Collection Interfaces**

1. **Different Data Structures and Concepts**:
• **Map**: A Map represents a collection of key-value pairs where each key is unique and is mapped to a single value. It provides methods to perform operations based on keys and values, such as adding, removing, or retrieving a value based on its key.
• **Collection** Interfaces (List, Set, Queue): These interfaces represent a collection of elements, all of which are typically of the same type. These elements can be accessed, added, or removed, but they do not have any concept of key-value pairs. Each element is an independent entity.

2. **Hierarchy in the Java Collections Framework**:

• **Collection Interface**: In the Java Collections Framework, Collection is a root interface that provides a unified architecture for representing and manipulating a group of objects as a single unit. List, Set, and Queue all extend the Collection interface, inheriting its methods and characteristics.

• **Map Interface**: Map does not extend the Collection interface. It is a separate interface at the same level as Collection. The reason for this is that a Map does not fit the concept of a collection of individual elements — instead, it is a collection of mappings from keys to values.

```java
public interface Collection<E> {
    // Methods for handling a collection of elements
}

public interface Map<K, V> {
    // Methods for handling a collection of key-value pairs
}
```

3. **Element vs. Key-Value Pair**:

• **Collection Elements**: For List, Set, and Queue, the primary entity is the element itself. The focus is on operations like adding elements, removing elements, and iterating over elements.
• **Map Entries**: For a Map, the primary entity is the key-value pair (or entry). Operations are focused on managing these pairs, such as putting entries, getting values based on keys, and checking for the existence of keys or values.

4. **Methods and Usage**:

• **Collection Interface**: Methods in the Collection interface and its subinterfaces (add, remove, iterator, size, etc.) are focused on handling a homogeneous group of objects.
• **Map Interface**: Methods in the Map interface (put, get, remove, containsKey, containsValue, entrySet, etc.) are designed for handling key-value associations, reflecting its different use cases.

**Why Map is Part of the Java Collections Framework**

Despite not extending Collection, Map is considered a fundamental part of the Java Collections Framework due to its importance and utility in handling key-value pairs. It provides a robust way to manage associative data, which is crucial in many programming scenarios.

The Collections Framework is designed to provide a comprehensive set of interfaces and classes to work with data in different forms:

• **Collection Interfaces (List,Set,Queue)**: For working with collections of individual elements.
• **Map Interface**: For working with collections of key-value pairs.

  

By keeping Map as a separate interface that does not extend Collection, Java provides a clear distinction between these different types of data structures, each with its own set of operations and use cases.
##### <span style="color:orange">Stream</span>
A `Stream` is a sequence of elements created from a `Collection` source. A Stream can be used as input to a _pipeline_, which defines a set of _aggregate operations_ (methods that apply transformations to a `Stream` of data). The [output](https://www.codecademy.com/resources/docs/java/output) of an aggregate operation serves as the input of the next operation (these are known as _intermediate operations_) until we reach a _terminal operation_, which is the final operation in a pipeline that produces some non-`Stream` output.

##### <span style="color:orange">Lambda</span>
 A lambda eliminates the need to create (extremely verbose) anonymous [classes](https://www.codecademy.com/resources/docs/java/classes) to implement [methods](https://www.codecademy.com/resources/docs/java/methods). With lambdas, we can define the method with its parameter(s) and its return value in a small block of code.

```java
// without aggregate 
// Given `intList` with the following elements: 5, 4, 1, 3, 7, 8  
List<Integer> evenList = new ArrayList<>();  
for(Integer i: intList) {  
  if(i % 2 == 0) {  
    evenList.add(i*2);  
  }  
}  
// evenList will have elements 8, 16

//WITH aggregate
List<Integer> evenList = intList.stream()  
  .filter((number) -> {return number % 2 == 0;})  
  .map(evenNum -> evenNum*2)  
  .collect(Collectors.toList());
```

1. **Stream Creation**: intList.stream() creates a stream of the elements in intList.
2. **Filtering**:
• The stream goes through the filter operation.
• The filter lambda takes each element (number) from the stream and checks if it’s even (number % 2 == 0).
• If the number is even, it is passed on to the next step in the pipeline.

3. **Mapping**:
• The stream now contains only even numbers.
• The map operation then takes each even number (evenNum) and applies the transformation (evenNum * 2).
• The transformed value (e.g., 4 * 2 = 8) is passed to the next step.

4. **Collecting**:
• The collect operation gathers all the transformed elements into a List, which is then stored in evenList.
