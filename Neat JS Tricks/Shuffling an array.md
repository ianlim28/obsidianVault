#shuffling 
```js
const shuffle = (quotes) => {
	let CI = quotes.length;
	let tempValue;
	let randomIndex;
	//while elements exist in the array
	while (CI > 0) {
		randomIndex = Math.floor(Math.random() * CI);
		// decrease CI by 1
		CI --;
		tempValue = quotes[CI];
		quotes[CI] = quotes[randomIndex];
		quotes[randomIndex] = tempValue;
	}
	return quotes;
}
```

The algorithm works as follows:

1. Declare and initialize the variables `CI` (current index), `tempValue` (temporary value), and `randomIndex`.

2. Enter a while loop that continues as long as `CI` is greater than 0.
   
3. Inside the while loop, generate a random index `randomIndex` using the `Math.random()` function multiplied by the value of `CI`. This random index represents the position of the element to be swapped with the current index.
   
4. Decrease `CI` by 1 to move to the next index in the array.
   
5. Assign the value at the current index `quotes[CI]` to `tempValue` for temporary storage.
   
6. Assign the value at the random index `quotes[randomIndex]` to the current index `quotes[CI]`.
   
7. Assign the value of `tempValue` to the random index `quotes[randomIndex]`.
   
8. Repeat steps 3-7 until all elements in the array have been iterated over.
   
9. Return the modified `quotes` array, which is now shuffled.
   
In summary, the `shuffle` function takes an array and rearranges its elements randomly, resulting in a shuffled array.