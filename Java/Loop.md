#return 

```java
import java.util.ArrayList;

class Lunch {
 
  public static ArrayList<String> removeAnts(ArrayList<String> lunchBox) {
    // Add your code below
    for (int i = 0; i < lunchBox.size(); i++) {
      if (lunchBox.get(i).equals("ant")) { // Use equals() for string comparison
        lunchBox.remove(i);
        i--; // Decrement i to account for the removed element
      }
    }
    return lunchBox;
  }
  
  public static void main(String[] args) {
    ArrayList<String> lunchContainer = new ArrayList<String>();
    lunchContainer.add("apple");
    lunchContainer.add("ant");
    lunchContainer.add("ant");
    lunchContainer.add("sandwich");
    lunchContainer.add("ant");
    
    lunchContainer = removeAnts(lunchContainer);
    System.out.println(lunchContainer);
  }
}
```


**Why return lunchBox is necessary?**

**Method Contract**: The method signature `public static ArrayList <String> removeAnts(ArrayList<String> lunchBox)` specifies that the method returns an `ArrayList<String>`. Failing to return a value would violate this contract and cause a compilation error.

**Chainability and Further Use**: Returning the modified lunchBox allows the calling code to receive and use the modified list. This can be useful for chaining methods or for further processing of the list.

`while` loops
These are useful to repeat a code block an unknown number of times until some condition is met.

```java
int wishes = 0;  
  
while (wishes < 3) {  
  
  // code that will run  
  wishes++;  
  
}
```

`for` loops
These are ideal for when you are incrementing or decrementing with a counter variable.
```java
for (int i = 0; i < 5; i++) {  
  
  // code that will run  
  
}
```

`for-each` loops
These make it simple to do something with each item in a list.
```java
for (String inventoryItem : inventoryItems) {  
  
  // do something with each inventoryItem  
  
}
```

##### <span style="color:orange">Prime Game</span>
Keep forgetting
**Instantiation Syntax**: new `ArrayList<Integer>` should include parentheses.
```java
// Import statement:

import java.util.ArrayList;

class PrimeDirective {

	// Add your methods here:
	public static boolean isPrime(int number) {
	
		if (number <= 1) {	
			return false;
		}
		
		for (int i = 2;i <= Math.sqrt(number); i++){
				if (number % i == 0) {
			return false;
			}
		}
		return true;
		}
	
	public static ArrayList<Integer> onlyPrime(int[] numbers) {
		ArrayList<Integer> primes = new ArrayList<Integer>();
			for (int number : numbers){
				if (isPrime(number)) {
					primes.add(number);
			}
			}
		return primes;
		}
		  
	public static void main(String[] args) {
	
		PrimeDirective pd = new PrimeDirective();
			
			int[] numbers = {6, 7, 29, 28, 33, 11, 100, 101, 43, 89};
			for (int number: numbers) {
				System.out.println(number + " is prime? " + isPrime(number));
				}
			ArrayList<Integer> primeNumbers = onlyPrime(numbers);
			System.out.println(primeNumbers);
		}
}
```

