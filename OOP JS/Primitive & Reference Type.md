#primitive #wrapper 
When its primitive type, JS temporarily wraps that string (example) in a wrapper object

| **Primitive Types**  | **Reference Types** |
|----------------------|---------------------|
| numbers              | all types of object |
| strings              | object literals     |
| booleans             | arrays              |
| null                 | functions           |
| undefined            | dates               |
| symbols              | all other objects   |
| _all above is STACK_ | _all above is HEAP_ |

```js
// new means creating an object, Array is a constructor function
const ages = new Array(20,30,35);
console.log(typeof ages);

// alternative this is another way to create an array, its an object
const names = ['shaun','crystal'];
console.log(typeof names);

// this is a object constructor, use NEW keyword and a constructor
// go to console and youll see all sorts of methods and properties
const userTwo = new String('ryu');
```

When dealing with primitive types in Java, you do not need to use the new keyword to create a value. Primitive types (e.g., int, float, double, boolean, etc.) are not objects, and they are directly stored in variables.

**Primitive Types**

You simply declare and assign values directly without using new:
```java
int age = 25;
double height = 175.5;
boolean isStudent = true;
char grade = 'A';
```

**Objects**

For objects (which are instances of classes), you typically use the new keyword to create an instance of the object:
```java
String name = new String("Alice");
Car myCar = new Car("Toyota", 2021, "Corolla");
```

Java has eight primitive types:

• byte
• short
• int
• long
• float
• double
• char
• boolean

**Creating Strings**

There are different ways to create String objects:

1. **String Literal**:
• When you use string literals, the String objects are interned, which means that they are stored in a common pool and reused, which can save memory.

```java
String str1 = "Hello";
```

2. **Using the** **new** **Keyword**:
• This approach explicitly creates a new String object, which is not interned.
```java
String str2 = new String("Hello");
```


##### <span style="color:orange">Wrapper Class</span>

Wrapper classes in Java are classes that encapsulate (or “wrap”) the primitive data types into objects. Each of the eight primitive types has a corresponding wrapper class in the java.lang package. The purpose of wrapper classes is to provide an object representation of primitive values, which allows them to be used in contexts that require objects, such as collections (e.g., ArrayList, HashMap) or when you need to use methods that are available only to objects.

**List of Wrapper Classes:**
Here are the wrapper classes corresponding to each primitive type:

1. **byte** **→** **Byte**
2. **short** **→** **Short**
3. **int** **→** **Integer**
4. **long** **→** **Long**
5. **float** **→** **Float**
6. **double** **→** **Double**
7. **char** **→** **Character**
8. **boolean** **→** **Boolean**

1. **Object Representation:**
• Wrapper classes allow primitive types to be used as objects. For example, Java collections (like ArrayList, HashMap) cannot store primitive types directly, so wrapper classes are used to store these values as objects.

```java
List<Integer> numbers = new ArrayList<>(); // Can only use Integer, not int
numbers.add(10); // Autoboxing converts int to Integer automatically
```

2. **Utility Methods:**
• Wrapper classes provide several utility methods to work with primitive types, such as parsing strings into numeric values, comparing values, or converting between different types.

```java
int num = Integer.parseInt("123"); // Converts a string to an int
Integer max = Integer.max(10, 20); // Returns the maximum of two integers
```

3. **Constants:**

• Wrapper classes include useful constants, such as Integer.MAX_VALUE, Integer.MIN_VALUE, which represent the maximum and minimum values of the respective primitive types.

```java
System.out.println("Max int value: " + Integer.MAX_VALUE);
```

4. **Autoboxing and Unboxing:**

• Java provides a feature called autoboxing, which automatically converts a primitive value into its corresponding wrapper class when needed. Conversely, unboxing converts a wrapper class object back into its corresponding primitive type.
```java
Integer wrappedInt = 5; // Autoboxing: int to Integer
int primitiveInt = wrappedInt; // Unboxing: Integer to int
```