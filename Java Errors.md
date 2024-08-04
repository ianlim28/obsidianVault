##### <span style="color:orange">Run-time Errors</span>
Errors which happen during program execution (run-time) after successful compilation are called run-time errors. _Run-time errors_ occur when a program with no compile-time errors asks the computer to do something that the computer is unable to reliably do.

- Division by zero also known as division Error
- Trying to open a file that doesnt exist

##### <span style="color:orange">Exceptions</span>
Java uses _exceptions_ to handle errors and other exceptional events. Exceptions are the conditions that occur at runtime and may cause the termination of the program.

When an exception occurs, Java displays a message that includes the name of the exception, the line of the program where the exception occurred, and a _stack trace_. The [stack](https://www.codecademy.com/resources/docs/java/stack) trace includes:

- The method that was running
- The method that invoked it
- The method that invoked that one

```java
try {  
  
  //  Block of code to try  
  
} catch (NullPointerException e) {  
  
  // Print the error message like this:  
  System.err.println("NullPointerException: " + e.getMessage());  
    
  // Or handle the error another way here  
  
}
```
##### <span style="color:orange">Logic Errors</span>
Once we have removed the syntax [errors](https://www.codecademy.com/resources/docs/java/errors) and run-time errors, the program runs successfully. But sometimes, the program still doesn’t do what we want it to do or no [output](https://www.codecademy.com/resources/docs/java/output) is produced. Hmmm…

These types of errors, which provide incorrect output, but appear to be error-free, are called _logic errors_. Logic errors occur when there is a design flaw in your program.