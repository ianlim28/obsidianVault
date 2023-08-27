#find

Returns the first results and stops

```js
const scores = [10,30,15,20,25,55,90];
//returns the first match and stops
const firstHighScore = scores.find((score) => {
	return score > 50;
})

console.log(firstHighScore);
```