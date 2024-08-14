#generics #interface #replacer 

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