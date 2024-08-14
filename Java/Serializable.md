#serializable

Serialization in Java is a mechanism of converting an object’s state into a byte stream, which can then be reverted back into a copy of the object. The primary purpose of serialization is to save the state of an object so that it can be recreated later. This is useful for persisting objects to files, sending objects over a network, or storing objects in a database.

**Serializable Interface**

In Java, to make a class serializable, it must implement the Serializable interface, which is a marker interface (an interface with no methods). Implementing this interface signals to the Java runtime that instances of this class can be serialized.

  

**Key Concepts**
##### <span style="color:orange">Serializable Interface</span>
• In the example, the Car class implements the Serializable interface, making its instances serializable.
```java
public class Car implements Serializable {
    private String make;
    private int year;
    private static final long serialVersionUID = 1L;
    
    public Car(String make, int year) {
        this.make = make;
        this.year = year;
    }
}
```

2. **Fields**:
• The fields of the class (make and year) will be included in the serialization process.

3. **serialVersionUID**:
• private static final long serialVersionUID = 1L; is a unique identifier for the class. This ID helps in version control of the serialized objects.
• If you make any changes to the class (e.g., adding/removing fields), you should change the serialVersionUID to reflect the new version.
• If serialVersionUID is not explicitly defined, Java will compute one at runtime based on various aspects of the class. However, it is good practice to define it explicitly to avoid compatibility issues during deserialization.

##### <span style="color:orange">Serialization and Deserialization Example</span>
Here is an example demonstrating serialization and deserialization of the Car class:
**Serialization (Saving Object to a File)**

```java
import java.io.FileOutputStream;
import java.io.IOException;
import java.io.ObjectOutputStream;

public class SerializeCar {
    public static void main(String[] args) {
        Car car = new Car("Toyota", 2020);
        //serialize an object to a file
        try (FileOutputStream fileOut = new FileOutputStream("car.ser");
             ObjectOutputStream out = new ObjectOutputStream(fileOut)) {
            out.writeObject(car);
            System.out.println("Serialized data is saved in car.ser");
        } catch (IOException i) {
            i.printStackTrace();
        }
    }
}
```

**Deserialization (Reading Object from a File)**

```java
import java.io.FileInputStream;
import java.io.IOException;
import java.io.ObjectInputStream;

public class DeserializeCar {
    public static void main(String[] args) {
        Car car = null;
        
        try (FileInputStream fileIn = new FileInputStream("car.ser");
             ObjectInputStream in = new ObjectInputStream(fileIn)) {
            car = (Car) in.readObject();
            System.out.println("Deserialized Car:");
            System.out.println("Make: " + car.getMake());
            System.out.println("Year: " + car.getYear());
        } catch (IOException i) {
            i.printStackTrace();
        } catch (ClassNotFoundException c) {
            System.out.println("Car class not found");
            c.printStackTrace();
        }
    }
}
```

**Explanation:**
**Serialization**:
• FileOutputStream and ObjectOutputStream are used to write the Car object to a file named car.ser.
• out.writeObject(car); serializes the Car object and writes it to the file.

**Deserialization**:
• FileInputStream and ObjectInputStream are used to read the Car object from the file car.ser.
• car = (Car) in.readObject(); reads the object from the file and casts it to the Car type.

**Methods**
You might need to implement getter methods to access the fields in the Car class after deserialization:
```java
public String getMake() {
    return make;
}

public int getYear() {
    return year;
}
```

**Points to Note:**
• **Transient Fields**: Fields marked with the transient keyword will not be serialized. For example, if you add transient int mileage; to the Car class, the mileage field will not be saved during serialization.
• **Compatibility**: The serialVersionUID helps in maintaining compatibility between different versions of the class.

Serialization is a powerful feature in Java for persisting and transferring objects. Understanding how to correctly implement it helps in developing robust Java applications.


##### <span style="color:orange">Serialization of Static & Transient</span>
Serialization is the process of converting an object into a byte stream, allowing it to be easily saved to a file or transmitted over a network. Deserialization is the reverse process, where the byte stream is converted back into an object.

***Static Fields***
• **Static Fields:** Belong to the class itself rather than any particular object instance.
• **Serialization Behavior:** The JVM ignores static fields during serialization because they are not part of the object state. They exist once per class, not per object instance.

***Non-Static Fields***
• **Non-Static Fields:** Belong to individual instances of the class.
• **Serialization Behavior:** By default, the JVM includes all non-static fields in the serialization process, regardless of their access modifiers (private, final, etc.).

***Transient Keyword***
• **Transient Fields:** These are non-static fields that you do not want to serialize.
• **Behavior:** When a field is marked as transient, the JVM will skip this field during serialization. Instead of storing the actual value, the field will be assigned its default value upon deserialization (e.g., 0 for integers, null for objects).

**Example Explanation**
```java
public class Person implements Serializable {
  private String name;
  private int age;
  private static int numberOfPeople = 10;
  private transient int yearBorn;  
}
```
 
 **Static Field (***numberOfPeople****):
• **Serialization:** This field will not be serialized because it is static.
• **Deserialization:** The field will have the value currently assigned to it in the class, not the serialized value (which wouldn’t exist).

 **Transient Field (***yearBorn****):**
• **Serialization:** This field will be ignored during serialization.
• **Deserialization:** The field will be initialized to its default value (0 for int).

**Deserialization Details**
• **Static Fields During Deserialization:** The value of static fields is determined by the class definition in memory, not by the serialized data. Therefore, numberOfPeople will retain its current value in the class, which is 10.
• **Object Construction During Deserialization:**
	• **No Constructor Call:** During deserialization, the JVM does not call the constructor of the serialized object. Instead, it sets the fields directly using reflection.
	• **Non-Serializable Parent:** If the class has a non-serializable parent class, the constructor of the first non-serializable parent class in the hierarchy will be called during deserialization.

**Practical Implications**
	• **Excluding Fields:** If you want to exclude certain fields from being serialized (for security or other reasons), mark them as transient.
	• **Managing Static Fields:** Remember that static fields are not part of the object’s serialized state, so their values must be managed separately.
	• **Custom Serialization:** Sometimes, you might need custom serialization logic to handle complex scenarios (like non-serializable objects or dependent transient fields).

In summary, understanding how static and transient fields are handled during serialization and deserialization helps in effectively managing the serialized state of objects in Java.


```java
import java.io.Serializable;
import java.io.FileOutputStream;
import java.io.FileInputStream;
import java.io.ObjectOutputStream;
import java.io.ObjectInputStream;
import java.io.FileNotFoundException;
import java.io.IOException;

public class Car implements Serializable {
    private String make;
    private int year;
    private static final long serialVersionUID = 1L;
    private transient String model;

	public Car(String make, int year, String model) {
	    this.make = make;
	    this.year = year;
	    this.model = model;
	}
	
	public String toString(){
	    return String.format("Car make is: %s, Car year is: %d, Car model is: %s, serialVersionUID: %d", this.make, this.year, this.model, serialVersionUID);
	}

	public static void main(String[] args) throws FileNotFoundException, IOException, ClassNotFoundException {
	    Car toyota = new Car("Toyota", 2021, "Corolla");
	    Car honda = new Car("Honda", 2020, "Civic");
	
	    FileOutputStream fileOutputStream = new FileOutputStream("cars.txt");
	    ObjectOutputStream objectOutputStream = new ObjectOutputStream(fileOutputStream);
	    objectOutputStream.writeObject(toyota);
	    objectOutputStream.writeObject(honda);
	
	    FileInputStream fileInputStream = new FileInputStream("cars.txt");
	    ObjectInputStream objectInputStream = new ObjectInputStream(fileInputStream);
	
	    Car toyotaCopy = (Car) objectInputStream.readObject();
	    Car hondaCopy = (Car) objectInputStream.readObject();
	
	    boolean isSameObject = toyotaCopy == toyota;
	    System.out.println("Toyota (Copy) - "+ toyotaCopy);
	    System.out.println("Toyota (Original) - "+ toyota);
	    System.out.println("Is same object: "+ isSameObject);
	}
}

//OUTPUT, the model output in the copy is NULL, because it is transient
//Toyota (Copy) - Car make is: Toyota, Car year is: 2021, Car model is: null, serialVersionUID: 1
//Toyota (Original) - Car make is: Toyota, Car year is: 2021, Car model is: Corolla, serialVersionUID: 1
//Is same object: false
```


##### <span style="color:orange">Automatic Invocation of writeObject and readObject</span>

**Serialization (***writeObject****)**:
• When you call ObjectOutputStream.writeObject(), the serialization mechanism checks if the class of the object being serialized has a writeObject method.
• If such a method exists, it is invoked to perform the custom serialization logic defined within it. Otherwise, the default serialization process is used.

 **Deserialization (****readObject****)**:
• Similarly, when you call ObjectInputStream.readObject(), the deserialization mechanism checks if the class of the object being deserialized has a readObject method.
• If such a method exists, it is invoked to perform the custom deserialization logic. Otherwise, the default deserialization process is used.


**Car Class with Custom Serialization/Deserialization**
```java
import java.io.Serializable;
import java.io.FileOutputStream;
import java.io.FileInputStream;
import java.io.ObjectOutputStream;
import java.io.ObjectInputStream;
import java.io.FileNotFoundException;
import java.io.IOException;

public class Car implements Serializable {
    private String make;
    private int year;
    private static final long serialVersionUID = 1L;
    private Engine engine;

    public Car(String make, int year) {
        this.make = make;
        this.year = year;
        this.engine = new Engine(2.4, 6);
    }

    private void writeObject(ObjectOutputStream stream) throws IOException {
        stream.writeObject(this.make);
        stream.writeInt(this.year);
        stream.writeDouble(this.engine.getLiters());
        stream.writeInt(this.engine.getCylinders());
    }

    private void readObject(ObjectInputStream stream) throws IOException, ClassNotFoundException {
        this.make = (String) stream.readObject();
        this.year = stream.readInt();
        double liters = stream.readDouble();
        int cylinders = stream.readInt();
        this.engine = new Engine(liters, cylinders);
    }

    public String toString(){
        return String.format("Car make is: %s, Car year is: %d, %s", this.make, this.year, this.engine);
    }

    public static void main(String[] args) throws FileNotFoundException, IOException, ClassNotFoundException {
        Car toyota = new Car("Toyota", 2021);
        Car honda = new Car("Honda", 2020);

        // Serializing the objects
        FileOutputStream fileOutputStream = new FileOutputStream("cars.txt");
        ObjectOutputStream objectOutputStream = new ObjectOutputStream(fileOutputStream);
        objectOutputStream.writeObject(toyota);
        objectOutputStream.writeObject(honda);
        objectOutputStream.close();

        // Deserializing the objects
        FileInputStream fileInputStream = new FileInputStream("cars.txt");
        ObjectInputStream objectInputStream = new ObjectInputStream(fileInputStream);
        Car toyotaCopy = (Car) objectInputStream.readObject();
        Car hondaCopy = (Car) objectInputStream.readObject();
        objectInputStream.close();

        // Comparing original and deserialized objects
        boolean isSameObject = toyotaCopy == toyota;
        System.out.println("Toyota (Copy) - " + toyotaCopy);
        System.out.println("Toyota (Original) - " + toyota);
        System.out.println("Is same object: " + isSameObject);
    }
}

class Engine {
    private double liters;
    private int cylinders;

    public Engine(double liters, int cylinders) {
        this.liters = liters;
        this.cylinders = cylinders;
    }

    public double getLiters() {
        return liters;
    }

    public int getCylinders() {
        return cylinders;
    }

    @Override
    public String toString() {
        return String.format("Engine: %.1f liters, %d cylinders", liters, cylinders);
    }
}
```

**Key Points**

1. **Serialization Process**:
• When objectOutputStream.writeObject(toyota) is called, the JVM looks for a writeObject method in the Car class.
• Since the Car class defines a writeObject method, this method is invoked to write the Car object’s state to the stream.
• The writeObject method explicitly writes the make, year, and engine details to the stream.

2. **Deserialization Process**:
• When objectInputStream.readObject() is called, the JVM looks for a readObject method in the Car class.
• Since the Car class defines a readObject method, this method is invoked to read the Car object’s state from the stream.
• The readObject method explicitly reads the make, year, and engine details from the stream and reconstructs the Car object.

When you use the ObjectInputStream to read data during deserialization, the order in which you read the data must exactly match the order in which you wrote the data using the ObjectOutputStream. The JVM does not inherently know which piece of data corresponds to which field. Instead, it relies on the order of operations to match the written and read data.