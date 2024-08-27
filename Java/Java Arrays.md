An array is a group of data consisting of the same type
What is the difference between list and array in Java?

**1. Size and Resizability:**
**Array:**
• An array is a fixed-size data structure. Once you define the size of an array, it cannot be changed. If you need more or fewer elements, you must create a new array with the required size.
• Example: int[] numbers = new int[10]; – This array can hold exactly 10 integers.

**List:**
• A List is part of the Java Collections Framework and can grow or shrink dynamically. You don’t need to specify the size of a list when you create it, and it can automatically adjust its size as you add or remove elements.
• Example: List`<Integer>` numbers = new ArrayList<>(); – This list can hold any number of integers, and you can add or remove elements as needed.

**2. Type and Flexibility:**
**Array:**
• Arrays can hold either primitive data types (e.g., int, char, float) or objects. The type of elements in an array must be uniform (all elements must be of the same type).
• Example: int[] numbers = {1, 2, 3}; – An array of integers.

 **List:**
• List can only hold objects, not primitive types. However, with Java’s auto-boxing feature, primitives can be automatically converted to their corresponding wrapper classes (e.g., int to Integer).
• Example: List`<Integer>` numbers = new ArrayList<>(); – A list of Integer objects.

**3. Performance:**
 **Array:**
• Arrays have less overhead and generally provide faster access to elements because they are a more basic, lower-level data structure. Index-based access is constant time, O(1).
• Example: Accessing an element in an array by index is very fast: numbers[2].

 **List:**
• Lists, particularly implementations like ArrayList, provide similar performance for random access but can be slower due to the overhead of maintaining the list’s dynamic nature. Operations like adding or removing elements may involve shifting elements, which can be costly.
• Example: Accessing an element in a list by index: numbers.get(2);.

**4. Flexibility in Operations:**

**Array:**
• Arrays are more rigid in terms of operations. Basic operations like adding, removing, or searching for an element need to be implemented manually or involve creating new arrays.
• Example: To remove an element from an array, you must manually shift elements.

**List:**
• Lists are more flexible and offer many built-in methods for common operations, such as adding, removing, finding, and iterating over elements.
• Example: You can easily remove an element from a list with numbers.remove(Integer.valueOf(3));.

**5. Memory Efficiency:**
**Array:**
• Arrays can be more memory-efficient because they don’t have the overhead associated with dynamic resizing and additional features provided by the List interface.
• Example: An array uses a contiguous block of memory.

**List:**
• Lists have some overhead due to dynamic resizing and the need to store additional metadata like the current size and capacity.
• Example: An ArrayList may have extra capacity beyond the number of elements it currently holds.

**6. Multi-dimensional Structures:**
**Array:**
• Arrays can be multi-dimensional (e.g., a 2D array like int[][] matrix = new int[3][3];), which is useful for representing grids or matrices.

**List:**
• While you can create lists of lists (e.g., List<List`<Integer>`>), these are not as naturally suited to multi-dimensional structures as arrays.

**7. Primitive vs. Object Storage:**
 **Array:**
• Can store both primitives and objects directly, which can save on memory and avoid boxing overhead.

 **List:**
• Can only store objects, so primitives are automatically boxed into their wrapper classes (e.g., int becomes Integer).

**Summary:**
• **Array**: Fixed size, can store both primitives and objects, more memory-efficient, fast access but less flexible for operations like adding/removing elements.
• **List**: Dynamic size, can only store objects, more flexible with built-in methods for various operations, slight overhead due to dynamic resizing and object storage.



```java
[1, 2, 3, 4, 5]

//array of objects
["hello", "world", "how", "are", "you"]

//array of arrays
[[1, 2, 3], [4, 5, 6], [7, 8, 9]]

//jagged arrays
[['a', 'b', 'c', 'd'], ['e', 'f'], ['g', 'h', 'i', 'j'], ['k']]

```

##### <span style="color:orange">Declaration, Initialization, and Assignment</span>
```java
//Declaring without initializing
int[][] intArray1;  

// Initializing an empty 2D array which has already been declared
//intArray1 = new int[row][column];
intArray2 = new int[3][5];

// Declaring and initializing an empty 2D array at once  
String[][] stringData = new String[3][6];

//how to initialize?
// if variable has not yet been declared
double[][] doubleValues = {{1.5, 2.6, 3.7}, {7.5, 6.4,5.3}, {9.8,  8.7, 7.6}, {3.6, 5.7, 7.8}};

//If the variable has already been declared
String[][] stringValues;  
stringValues = new String[][] {{"working", "with"}, {"2D",  
"arrays"}, {"is", "fun"}};



public class Main {

	public static void main(String[] args) {
	// Declare a 2d array of float values called floatTwoD
	float[][] floatTwoD;
	floatTwoD = new float[4][10];
	
	//declare
	char[][] ticTacToe = {{'X','O','O'},{'O','X',' '},{'X',' ','X'}};
	
	//initialize
	ticTacToe = new ticTacToe[][] {{'O','X','X'},{'X','O',' '},{'O',' ','O'}};
	}
}
```

##### <span style="color:orange">Accessing Elements in a 2D array</span>
```java
String[] words = {"cat", "dog", "apple", "bear", "eagle"};

// Store the first element from the String array  
String firstWord = words[0];  
  
// Store the last element of the String array  
String lastWord = words[words.length-1];  
  
// Store an element from a different position in the array  
String middleWord = words[2];

// Given a 2D array of integer data  
int[][] data = {{2,4,6}, {8,10,12}, {14,16,18}};  
  
// Access and store a desired element  
int stored = data[0][2];
```



##### <span style="color:orange">Looping through arrays</span>
```java
public class Main {

public static void main(String[] args) {

	int[][] binary = {
		{0, 1, 0, 1},	
		{1, 1, 1, 0},
		{1, 0, 0, 1},
		{1, 0, 1, 0}
	};
	
	int onesCount = 0;
	System.out.println(onesCount);

	String[][] wordData = {{"study", "consider", "examine", "learn"}, {"ponder", "read", "think", "cogitate"}};


	for (int[] row: binary){
	
		for (int element: row){
			if (element == 1){		
				onesCount += 1;
			}
		}
		}
		System.out.println("Total number of 1s: " + onesCount);
		
	int i = 0, j = 0;
	while (i < wordData.length) {
		j = 0;
		while (j < wordData[i].length) {
			System.out.println(wordData[i][j] + ": [" + i + "]" + "[" + j + "]");
			j++;
			}
		i++;
		}
	}
}
```

```java
// Row-major order  
for(int o = 0; o < letters.length; o++) {  
    for(int i = 0; i < letters[o].length; i++) {  
        char c = letters[o][i];  
    }  
}  
  
// Column-major order  
for(int o = 0; o < letters[0].length; o++) {  
    for(int i = 0; i < letters.length; i++) {  
        char c = letters[i][o];  
    }  
}
```

##### <span style="color:orange">Flipping words from upper to lower</span>
```java
import java.util.Arrays;

public class Main {
    public static void main(String[] args) {
        String[][] words = {
            {"championship", "QUANTITY", "month"},
            {"EMPLOYEE", "queen", "understanding"},
            {"method", "writer", "MOVIE"}
        };
        
        System.out.println("Before...");
        System.out.println(Arrays.deepToString(words).replace("],", "],\n") + "\n");

        for (int i = 0; i < words.length; i++) {
            for (int j = 0; j < words[i].length; j++) {
                if (words[i][j] != null) {
                    // Flip the capitalization
                    words[i][j] = words[i][j].equals(words[i][j].toUpperCase()) 
                                  ? words[i][j].toLowerCase() 
                                  : words[i][j].toUpperCase();
                }
            }
        }

        System.out.println("After...");
        System.out.println(Arrays.deepToString(words).replace("],", "],\n") + "\n");
    }
}
```