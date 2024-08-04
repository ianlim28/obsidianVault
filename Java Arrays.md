An array is a group of data consisting of the same type

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