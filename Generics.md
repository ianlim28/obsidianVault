#generics #interface #replacer 
##### <span style="color:orange">What Are Generic Type Parameters?</span>
• **Generic Type Parameters** are placeholders for types that you can specify when you create an instance of a generic class, implement a generic interface, or invoke a generic method.


```java
public class Box <T> {  
  private T data;  

  // public constructor
  public Box(T data) {  
    this.data = data;  
  }  
  
  public T getData() {  
    return this.data;  
  }    
}


// creating a generic class
Box<String> myStringBox = new Box<>("Apple");
```

 type parameters are `E` (Elements), `K` (Key), `N` (Number), `T` (Type), `V` (Value), and `S` (or `U` or `V`) for multiple type parameters.


In Java, each primitive data type has a corresponding wrapper class. Wrapper classes provide a way to use primitive data types as objects, which is necessary in certain situations, such as when working with Java Collections (like ArrayList) that require objects rather than primitives. Here is a list of the primitive data types and their corresponding wrapper classes:

| Primitive Data Type | Wrapper Class |
|---------------------|---------------|
| `byte`              | `Byte`        |
| `short`             | `Short`       |
| `int`               | `Integer`     |
| `long`              | `Long`        |
| `float`             | `Float`       |
| `double`            | `Double`      |
| `char`              | `Character`   |
| `boolean`           | `Boolean`     |
• **Immutability**: Wrapper classes are immutable, meaning that once an object is created, its value cannot be changed.

• **Nullability**: Unlike primitives, wrapper class objects can be null, which can be useful when you need to represent the absence of a value.

• **Methods**: Wrapper classes provide various utility methods for parsing, comparing, and converting values. For example, Integer.parseInt(String) can be used to convert a String to an int.

##### <span style="color:orange">Autoboxing</span>
Autoboxing allows wrapper classes to take primitive values and convert them to their corresponding wrapper object by automatically calling the `valueOf()` method.
```java
Integer a = 56;  // Autoboxing, automatic call to `valueOf()`  
Box<Integer> intBox1 = new Box<>(a);  
Box<Integer> intBox2 = new Box<>(56);  // Autoboxing, automatic call to `valueOf()`  
Box<Integer> intBox3 = new Box<>(Integer.valueOf(56));
```

We can also take the wrapper object and convert it back to its primitive value using one of the wrapper object’s `Value()` methods

```java
Integer a = 56;  
int aPrimitive1 = a.intValue();  // Return primitive `int` value from `Integer` object  
int aPrimitive2 = a;  // Unboxing, automatic call to `intValue()`
```

##### <span style="color:orange">Generic Interface</span>


1. **Retriever`<T>`** **Interface:**
• This is a generic interface with a method retrieveData() that returns a value of type T.

```java
//Retriever.java
public interface Retriever<T>{
//method signature
	T retrieveData();
}
```

2. **Book** **Class:**

• Implements the Retriever`String>` interface, meaning it will work with String data.
• The retrieveData() method returns the name of the book.
```java
//Book.java
public class Book implements Retriever<String> {
    private String name;

    public Book(String name) {
        this.name = name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public String getName() {
        return this.name;
    }

    @Override
    public String retrieveData() {
        return this.name;
    }
}
```

3. **Container`T`** **Class:**

• This class is also generic and implements Retriever`T`, making it capable of working with any type T.
• The retrieveData() method returns the data stored in the container.
```java
//Container.java
public class Container<T> implements Retriever<T> {
    private T data;

    public Container(T data) {
        this.data = data;
    }

    public void setData(T data) {
        this.data = data;
    }

    public T getData() {
        return this.data;
    }

    @Override
    public T retrieveData() {
        return this.data;
    }
}
```

4. **Main** **Class:**
• In the main method, you create instances of Container and Book, demonstrating how Retriever can be used with different types.
• The retrieveData() method is called on both instances, and the results are printed.

```java
//Main.java
public class Main {
    public static void main(String[] args) {
        int myNumber = 24;
        String bookName = "Hello Book!";
        
        // Using the Retriever interface with different types
        Retriever<Integer> containerRetriever = new Container<>(myNumber);
        Retriever<String> bookRetriever = new Book(bookName);

        System.out.println("Container retrieved data: " + containerRetriever.retrieveData());
        System.out.println("Book retrieved data: " + bookRetriever.retrieveData());
    }
}
```

##### <span style="color:orange">Generic Methods</span>

```java
public class Main {
	public static void main(String[] args) {
	    String test1 = "Double";
	    double test2 = 5.8;
	
	    // Enter code below...  
	    boolean isTest1Double = isDouble(test1);
	    boolean isTest2Double = isDouble(test2);
	
	    System.out.println(isTest1Double);
	    System.out.println(isTest2Double);
	}
	// <T>: This is the type parameter. It means that the method can accept any type of object.
	
	public static <T> boolean isDouble(T object){
	    return object instanceof Double;
	}
}
```

• **Method Signature**: The method takes a single argument object of type T and returns a boolean.

• **Logic**: The method checks if the passed object is an instance of the Double class using the instanceof operator.

##### <span style="color:orange">Multiple type parameters</span>

```java
public class Container<T, S> {
  private T item1;
  private S item2;

  public Container(T item1, S item2) {
    this.item1 = item1;
    this.item2 = item2;
  }

  public T getItem1() {
    return this.item1;
  }

  public S getItem2() {
    return this.item2;
  }
}
```

• **Generic Type Parameters**:

• T and S are type parameters that allow you to specify the types of the two items when creating an instance of Container.
• These can be any types—T could be an Integer and S could be a String, for example.

```java
public class Main {
    public static void main(String[] args) {
        // Creating a Container to hold an Integer and a String
        Container<Integer, String> myContainer = new Container<>(42, "Hello, World!");

        // Accessing the items
        Integer item1 = myContainer.getItem1();
        String item2 = myContainer.getItem2();

        // Output the items
        System.out.println("Item 1: " + item1);  // Output: Item 1: 42
        System.out.println("Item 2: " + item2);  // Output: Item 2: Hello, World!
    }
}
```

##### <span style="color:orange">Upper Bounds</span>
An upper bound will restrict a generic type to be a specific type or any type that `extends`

```java
public class Box <T extends Number> {  
  private T data;  
}

Box<Integer> intBox = new Box<>(2);  // Valid type argument  
Box<Double> doubleBox = new Box<>(2.5);  // Valid type argument  
Box<String> stringBox = new Box<>("hello");  // Error
```

Example
```java
//Main.java
public class Main {
	public static void main(String[] args) {
		SchoolPerson person = new SchoolPerson("Peter");
		Bus<SchoolPerson> busWPerson = new Bus<>(person);
		busWPerson.printRider();	
	}
}
```

```java
//Bus.java
public class Bus<T extends SchoolPerson> {

	private T rider;
	
	public Bus(T rider) {
		this.rider = rider;
	}
	
	public void setRider(T rider) {
		this.rider = rider;
	}
	
	public T getRider() {
		return this.rider;
	}
	
	public void printRider() {
		System.out.println(rider.toString());
	}
}
```

```java
//SchoolPerson.java
public class SchoolPerson {

	private String name;
	
	public SchoolPerson(String name) {
		this.name = name;
	}
	
	public void setName(String name) {
		this.name = name;
	}
	
	public String getName() {
		return this.name;
	}
	
	public String toString() {
		return "SchoolPerson (name = "+ this.name + ")";
	}
}
```


##### <span style="color:orange">Wildcards</span>
We can make our code even more general when we don’t need the more strict type checking of using type parameters by using _wildcards_.
```java
public class Util {  
  public static void printBag(Bag<?> bag) {  
    System.out.println(bag.toString());  
  }  
}  
Bag<String> myBag1 = new Bag("Hello");  
Bag<Integer> myBag2 = new Bag(23);  
Util.printBag(myBag1);  // Hello  
Util.printBag(myBag2);  // 23
```

In general, we should use type parameters, when we have a relationship between the type of arguments and the return type.

```java
public static <T> Bag<T> getBag(Bag<T> bag) {  
  return bag;  
}
```


##### <span style="color:orange">Wildcard Lower Bounds</span>
A lower bound wildcard restricts the wildcard to a class or interface and any of its parent types.
```java
public class Util {  
  public static void getBag(Bag<? super Integer> bag) {  
    return bag;  
  }  
}
```
In the example above, we used the `super` keyword to restrict the argument to `getBag()` to be a `Bag` of `Integer`, `Number`, or `Object`. If a call to `getBag()` with `Bag<Double>` is made, it would result in an error because `Double` is not an `Integer` or one of its parents.

- They cannot be used with generic type parameters, only wildcards.
- A wildcard cannot have both a lower bound and an upper bound. In this case, it’s best to use a generic type parameter.
- An upper bound wildcard should be used when the variable is being used to serve some type of data to our code.
- A lower bound wildcard should be used when the variable is receiving data and holding it for later use.
- When a variable that serves data is used and only uses `Object` methods, an unbounded wildcard is preferred.
- When a variable needs to serve data and store data for later use, a wildcard should not be used (use a type parameter instead).


