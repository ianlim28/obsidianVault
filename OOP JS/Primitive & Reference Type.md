#primitive
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