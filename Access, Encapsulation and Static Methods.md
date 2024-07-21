#static 
Static methods are methods that belong to an entire class, not a specific object of the class. Static methods are called using the class name and the `.` operator.

**Calling Static Methods**
Every method in the `Math` class is static. This means that we can call and use these methods without creating an object of the class. There are two main options for calling a static method.
```java
class Numbers {  
  public static void main(String[] args) {  
    // Call method using the Class name, the dot operator, the method name, and arguments  
    int smallerNumber = Math.min(3, 10);  
    System.out.println(smallerNumber); // Prints: 3  
  }  
}
```

##### <span style="color:orange">How to generate random numbers</span>
the value that you multiply by defines the number of possible values you can get. The number that you add defines the starting value. So, for example, `(int)(Math.random() * 3 ) + 5;` will give you one of three random values starting at `5`. So this could give you `5`, `6`, or `7`.

```java
// Random double value between 0 and 10, not including 10  
double a = Math.random() * 10;

// Random int value between 0 and 9  
int b = (int)(Math.random() * 10);

// Random int value between 1 and 10  
int c = (int)(Math.random() * 10) + 1;

// Random int value between 10 and 20  
int d = (int)(Math.random() * 11 ) + 10;
```


- Static methods and [variables](https://www.codecademy.com/resources/docs/java/variables) are associated with the class as a whole, not objects of the class.
- Static methods and variables are declared as static by using the `static` keyword upon declaration.
- Static methods cannot interact with non-static instance variables. This is due to static methods not having a `this` reference.
- Both static methods and non-static methods can interact with static variables.

**Parent Class Aspect Modifiers**
#public #private #protected #nomodifier
In Java, access modifiers determine the visibility and accessibility of classes, methods, and variables. They control how the members of a class can be accessed from other parts of your code.

**1. Public**

• **Keyword**: public
• **Accessibility**: A public class, method, or variable is accessible from any other class, regardless of the package it belongs to.
• **Use Case**: Use public for members that need to be accessible from outside the class, including from other packages.

```java
public class ParentClass {
    public int publicVariable;

    public void publicMethod() {
        // Accessible from anywhere
    }
}
```

```java
public class Utility {
    public static void printMessage(String message) {
        System.out.println(message);
    }
}

// Accessing from another class
Utility.printMessage("Hello, World!");
```

**2. Protected**

• **Keyword**: protected
• **Accessibility**: A protected member is accessible within its own package and by subclasses (derived classes) even if they are in different packages.
• **Use Case**: Use protected when you want to allow access to subclasses but hide the member from the rest of the world.

```java
public class ParentClass {
    protected int protectedVariable;

    protected void protectedMethod() {
        // Accessible within the package and subclasses
    }
}
```

```java
public class Animal {
    protected void makeSound() {
        System.out.println("Animal sound");
    }
}

public class Dog extends Animal {
    public void bark() {
        makeSound(); // Accessible because it's protected
        System.out.println("Woof!");
    }
}

// Accessing from another class
Dog dog = new Dog();
dog.bark(); // Outputs "Animal sound" followed by "Woof!"
```

**3. No Modifier (Package-Private)**

• **Keyword**: No specific keyword is used, simply omit the modifier.
• **Accessibility**: A member with no modifier (package-private) is accessible only within its own package.
• **Use Case**: Use package-private to restrict access to the members of the same package.

```java
public class ParentClass {
    int packagePrivateVariable; // No modifier

    void packagePrivateMethod() {
        // Accessible only within the same package
    }
}
```

```java
// In the same package
class PackageClass {
    void packageMethod() {
        System.out.println("Package-private method");
    }
}

public class Main {
    public static void main(String[] args) {
        PackageClass pc = new PackageClass();
        pc.packageMethod(); // Accessible because it's in the same package
    }
}
```

**4. Private**

• **Keyword**: private
• **Accessibility**: A private member is accessible only within the class it is declared in.
• **Use Case**: Use private to restrict access to the member within the class itself. This is useful for encapsulation and hiding implementation details.

```java
public class ParentClass {
    private int privateVariable;

    private void privateMethod() {
        // Accessible only within this class
    }
}
```

```java
public class EncapsulatedClass {
    private int privateValue;

    public void setPrivateValue(int value) {
        this.privateValue = value;
    }

    public int getPrivateValue() {
        return this.privateValue;
    }
}

public class Main {
    public static void main(String[] args) {
        EncapsulatedClass ec = new EncapsulatedClass();
        ec.setPrivateValue(10);
        System.out.println(ec.getPrivateValue()); // Outputs 10
    }
}
```

**Super Constructor**
#super 
In Java, the super keyword is used to refer to the immediate parent class object. It is used to call the constructor of the parent class and to access methods and variables of the parent class that have been overridden or hidden by the subclass.

**Key Points about the super Constructor**

1. **Calling the Parent Class Constructor**:
• The super constructor is used to invoke the constructor of the parent class.
• It must be the first statement in the subclass constructor.
• If you do not explicitly call the super constructor, the Java compiler automatically inserts a call to the no-argument constructor of the parent class.

2. **When to Use** **super**:
• Use super when you need to pass arguments to the parent class constructor.
• Use super to call the parent class constructor with specific parameters.
• Use super to initialize the parent class before performing additional initialization in the subclass.

Parent Class: Animal
```java
public class Animal {
    String name;

    // Constructor with one parameter
    public Animal(String name) {
        this.name = name;
        System.out.println("Animal constructor called");
    }
}
```

Subclass: Dog
```java
public class Dog extends Animal {
    String breed;

    // Constructor with two parameters
    public Dog(String name, String breed) {
        // Call the parent class constructor
        super(name);
        this.breed = breed;
        System.out.println("Dog constructor called");
    }
}
```

Main Class to Demonstrate the Usage
```java
public class Main {
    public static void main(String[] args) {
        Dog dog = new Dog("Buddy", "Golden Retriever");
    }
}
```

**Explanation**

1. **Parent Class Constructor**:
• The Animal class has a constructor that takes one parameter, name.
• This constructor initializes the name instance variable and prints a message.

2. **Subclass Constructor**:
• The Dog class extends Animal and has its own constructor that takes two parameters, name and breed.
• Inside the Dog constructor, super(name) is used to call the parent class constructor and pass the name parameter to it.
• The breed instance variable is then initialized, and a message is printed.

3. **Main Method**:
• When a Dog object is created, the Dog constructor is called.
• The Dog constructor calls the Animal constructor using super(name).
• The Animal constructor executes first, followed by the rest of the Dog constructor.

Another subclass: Puppy
```java
public class Puppy extends Dog {
    int age;

    // Constructor with three parameters
    public Puppy(String name, String breed, int age) {
        // Call the parent class constructor
        super(name, breed);
        this.age = age;
        System.out.println("Puppy constructor called");
    }
}
```
