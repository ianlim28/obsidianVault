Skeleton of Java
**Class**
• **Definition**: A class is a blueprint or template that defines the properties (fields) and behaviors (methods) that objects created from the class can have.
• **Example**: In your code, Car is the class.

```java
public class Car {
    String color;
    int milesDriven;
    
    public Car(String carColor) {
        color = carColor;
        milesDriven = 0;
    }
    
    public void drive() {
        String message = "Miles driven: " + milesDriven;
        System.out.println(message);
    }
    
    public static void main(String[] args) {
        Car myFastCar = new Car("red");
        myFastCar.drive();
    }
}
```

**Constructor**
• **Definition**: A constructor is a special method used to initialize objects. The constructor is called when an instance of the class is created. It usually initializes the fields of the new object.
• **Example**: In your code, the constructor is the method public Car(String carColor).

```java
public Car(String carColor) {
    color = carColor;
    milesDriven = 0;
}
```

**Instance (or Object)**
• **Definition**: An instance (or object) is a specific realization of any class. When a class is instantiated, it creates an object of that class, with its own set of attributes.
• **Example**: In your code, myFastCar is an instance of the Car class.
```java
Car myFastCar = new Car("red");
```

**Field (or Attribute)**
• **Definition**: Fields (or attributes) are variables that hold the state of an object. Each object has its own copy of the fields defined in the class.
• **Example**: In your code, color and milesDriven are fields.

```java
String color;
int milesDriven;
```

**Method**
• **Definition**: Methods define the behaviors or actions that objects created from the class can perform.
• **Example**: In your code, drive is a method.

```java
public void drive() {
    String message = "Miles driven: " + milesDriven;
    System.out.println(message);
}
```

**Main Method**
• **Definition**: The main method is the entry point of a Java program. It must be static and is used to run the program.
• **Example**: In your code, the main method is where you create an instance of Car and call its drive method.

```java
public static void main(String[] args) {
    Car myFastCar = new Car("red");
    myFastCar.drive();
}
```

**Summary**
• **Class**: Car (the blueprint).
• **Constructor**: public Car(String carColor) (initializes new objects).
• **Instance/Object**: myFastCar (a specific car created from the Car class).
• **Fields**: color, milesDriven (attributes of Car).
• **Method**: drive() (behavior of Car).
• **Main Method**: main (entry point of the program).



`public` means that other [classes](https://www.codecademy.com/resources/docs/java/classes) can access this method.
`void` means that there is no specific [output](https://www.codecademy.com/resources/docs/java/output) from the method.
[methods](https://www.codecademy.com/resources/docs/java/methods)


```java
public class Car {

  String color; // Instance variable

  // Constructor to initialize the color of the car
  public Car(String carColor) {
    color = carColor;
  }

  // Instance method to start the engine of the car
  public void startEngine() {
    System.out.println("Starting the car!");
    System.out.println("Vroom!");
  }

  // Static method, entry point of the program
  public static void main(String[] args) {
    // Create an instance of Car
    Car myFastCar = new Car("red");
    
    // Call an instance method on the created object
    myFastCar.startEngine();
    
    // Print a message
    System.out.println("That was one fast car!");
  }
}
```
In Java, the static keyword is used to indicate that a method or variable belongs to the class itself, rather than to instances of the class. Here’s an explanation of why the main method is static but the startEngine method is not:

**main Method**
1. **Static Context**:
• The main method is declared as static because it is the entry point of the program and must be callable by the Java Virtual Machine (JVM) without creating an instance of the class.

• The main method signature is defined by the Java Language Specification and must be public static void main(String[] args). This ensures that the JVM can invoke it directly using the class name.

2. **No Object Required**:

• Since the program needs to start without any pre-existing objects, the main method must be static. This allows the JVM to call it without needing to instantiate the class first.

**startEngine Method**
1. **Instance Method**:

• The startEngine method is not declared as static because it is meant to operate on an instance of the Car class. Each car can have its own state (e.g., color), and startEngine acts on the specific instance it is called on.
• Instance methods can access instance variables (like color) and other instance methods.

2. **Requires an Object**:

• To call the startEngine method, you need an instance of the Car class. This makes sense because starting an engine is an action that is specific to a particular car object.

**Key Points**
1. **Static Context (****main** **Method)**:

• The main method is static so the JVM can invoke it without creating an object of the class.
• You can create objects and call instance methods from within the main method.

2. **Instance Context (****startEngine** **Method)**:

• The startEngine method is an instance method because it performs actions on a specific instance of the Car class.
• It can access instance variables (e.g., color) and perform actions specific to the object on which it is called.

**Why the Difference?**
• **main** **Method**: Needs to be static to serve as the entry point for the program.
• **startEngine** **Method**: Should not be static because it operates on individual instances of the class, allowing each Car object to behave independently based on its state.

another example
```java
public class Store {

	// instance fields
	String productType;
	
	// constructor method
	public Store(String product) {
		productType = product;
	}
	
	// advertise method
	public void advertise() {
		System.out.println("Selling " + productType + "!");
		System.out.println("Come spend some money!");
	}
}
```

```java
public class Main {

	public static void main(String[] args) {
		Store lemonadeStand = new Store("Coffee");
		lemonadeStand.advertise();
	}

}
```


**Initialization and Declaration**
```java
public class Newsfeed {
  String[] topics = {"Opinion", "Tech", "Science", "Health"}; // Initialized directly
  int[] views = {0, 0, 0, 0}; // Initialized directly
  String[] favoriteArticles; // Declared but not initialized
  
  // Constructor
  public Newsfeed(){
    favoriteArticles = new String[10]; // Initialize in constructor
  }
  
  // Method to set a favorite article
  public void setFavoriteArticle(int favoriteIndex, String newArticle){
    favoriteArticles[favoriteIndex] = newArticle;
  }
  
  // Main method for testing
  public static void main(String[] args) {
    Newsfeed myFeed = new Newsfeed(); // Create an instance of Newsfeed
    myFeed.setFavoriteArticle(0, "Breaking News"); // Set a favorite article
    System.out.println(myFeed.favoriteArticles[0]); // Output the favorite article
  }
}
```

**Summary**

• **Class-level Declaration**: String[] favoriteArticles; declares the variable, indicating that each instance will have its own array.

• **Constructor Initialization**: favoriteArticles = new String[10]; in the constructor ensures that each instance of Newsfeed initializes favoriteArticles properly, providing flexibility and ensuring a fresh array for each instance.

• **Flexibility and Maintenance**: This approach keeps the initialization logic centralized and allows for easy modifications and future enhancements.