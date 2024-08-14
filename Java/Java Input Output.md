#input #output

| Class | Definition |
|---|---|
| [`System.out`](https://docs.oracle.com/javase/9/docs/api/java/lang/System.html#out) | A class that holds functions to display output in a terminal or command prompt application. |
| [`Scanner`](https://www.codecademy.com/courses/learn-intermediate-java/lessons/java-input-and-output/exercises/link) | A class used to read input passed into a Java program. |
| [`FileWriter`](https://docs.oracle.com/javase/9/docs/api/java/io/FileWriter.html) | A class that holds functions to convert byte data into readable text files. |
| [`FileReader`](https://docs.oracle.com/javase/9/docs/api/java/io/FileReader.html) | A class that has functions that convert input from files to byte data for a Java program to use. |

- [`System`](https://docs.oracle.com/javase/9/docs/api/java/lang/System.html) is a class in the `lang` package that is part of every Java installation. It contains several properties and [methods](https://www.codecademy.com/resources/docs/java/methods) to interface with various high-level aspects of the computer environment.
- `out` is an instance of a `PrintStream`, included as part of the `System` class, that is already open and provides [output](https://www.codecademy.com/resources/docs/java/output) to the user’s default console or display.

Everything that is contained in the [`java.lang`](https://docs.oracle.com/javase/9/docs/api/java/lang/package-summary.html) package is automatically imported into every Java program. Every Java SDK installation comes with everything in the `java.base` module, a [collection](https://www.codecademy.com/resources/docs/java/collection) of resources that make Java what it is. The other packages contained in [`java.base`](https://docs.oracle.com/javase/9/docs/api/java.base-summary.html) such as [`java.util`](https://docs.oracle.com/javase/9/docs/api/java/util/package-summary.html) and [`java.io`](https://docs.oracle.com/javase/9/docs/api/java/io/package-summary.html) provide helper functionality that isn’t necessary to every program, but is used in special circumstances, such as when we need a `Scanner`. We access these extra [classes](https://www.codecademy.com/resources/docs/java/classes) by importing them in our program. This tells the [compiler](https://www.codecademy.com/resources/docs/java/compiler) to go to those packages and make sure the resource is available for use when we build our programs. So why don’t we include everything in all Java programs? If we did that, our programs would be huge when compiled, including many many [files](https://www.codecademy.com/resources/docs/java/files) we will never use. Importing specific classes from these packages keeps our software lean and efficient.

The list below outlines some (but not all) of the different [methods](https://www.codecademy.com/resources/docs/java/methods) associated with the Scanner class that allow us to read the next piece of information we are looking for.

| Variable | Code                                     |
| -------- | ---------------------------------------- |
| String   | `String myString = input.next();`        |
| Int      | `int num = input.nextInt();`             |
| Double   | `double numDouble = input.nextDouble();` |
| Byte     | `byte numByte = input.nextByte();`       |
| Boolean  | `boolean isTrue = input.nextBoolean();`  |
| Long     | `long numLong = input.nextLong();`       |
| Short    | `short numShort = input.nextShort();`    |

| Code                      | Function                                                                                                                                                                                                                      |
| ------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `input.hasNext()`         | This function returns a boolean that indicates if there is another token left to process.                                                                                                                                     |
| `input.hasNextLine()`     | This function returns a boolean that indicates if there is another line in the input of the defined scanner.                                                                                                                  |
| `input.hasNextInt()`      | This function returns a boolean that validates if there is another `int` in the input of the defined scanner.                                                                                                                 |
| `input.useDelimiter(",")` | This function helps us specify what delimiters we want to use. A delimiter is used to separate data units. This `,` delimiter can be especially useful when a program is required to read CSV (comma-separated values) files. |

```java
import java.io.FileReader;
import java.io.IOException;

public class Introduction {
    public static void main(String[] args) throws IOException {
        String path = "./input.txt"; // Path to the file
        FileReader reader = new FileReader(path); // Create a FileReader object

        int counter = reader.read(); // Read the first character
        while (counter != -1) { // Loop until end of file
            System.out.print((char) counter); // Print the character
            counter = reader.read(); // Read the next character
        }
        reader.close(); // Close the FileReader
    }
}
```


##### <span style="color:orange">1. When to Use new and When Not to Use new</span>

In Java, the new keyword is used to create new instances (objects) of classes. Here’s a brief guide:

• **When to Use** **new**
	• When you are creating an instance of a class (i.e., creating an object).
	• new allocates memory for the object and initializes it.

```java
FileReader reader = new FileReader(path); // Creates a new FileReader object
Scanner scanner = new Scanner(System.in); // Creates a new Scanner object
```

• **When You Do Not Use** **new**
	• When you are dealing with primitive data types (e.g., int, char, double).
	• When you are calling a static method (e.g., Math.sqrt(4.0)).
	• When you are using an existing object reference or calling a method on an existing object.

```java
int counter = reader.read(); // Calls the read method on the existing FileReader object
char ch = (char) counter; // Casting an int to a char, no new object is created
```

##### <span style="color:orange">2. (char) counter Syntax</span>
The syntax (char) counter is a type cast. Casting is used to convert one data type to another. In this case, it converts the int value counter to a char.

• **Why Cast?**
	• The FileReader.read() method returns an int representing the ASCII value of a character.
	• To print this value as a character, you need to cast it to char.
```java
int counter = reader.read(); // counter holds an int value, say 65
char ch = (char) counter;    // casting int 65 to char, which is 'A'
System.out.print(ch);        // prints 'A'
```

##### <span style="color:orange">3. counter = reader.read()</span>
This line calls the read() method on the reader object and assigns the returned value to the counter variable.

• **Explanation:**
	• reader.read() reads the next character from the file and returns it as an int.
	• This returned int is stored in the counter variable.
	• The loop continues until reader.read() returns -1, indicating the end of the file.
	• the initialization of counter should be set to the value returned by reader.read() right at the start, not 0. This is because reader.read() immediately reads the first character of the file, and initializing counter to 0 would not correctly reflect the first character’s value from the file.
```java
int counter = reader.read(); // Reads a character and assigns its ASCII value to counter
while (counter != -1) {
    System.out.print((char) counter); // Prints the character
    counter = reader.read(); // Reads the next character
}
```


### File Writer
```java
import java.io.IOException;
import java.io.FileWriter;

public class Introduction {
    public static void main(String[] args) {
        String outputText = "Hello James!";
        
        // Using try-with-resources to ensure the FileWriter is closed properly
        try (FileWriter newfile = new FileWriter("output.txt")) {
            // Write message to file
            newfile.write(outputText);
            // FileWriter will be closed automatically here
        } catch (IOException e) {
            // Handle potential IOException
            e.printStackTrace();
        }
    }
}
```