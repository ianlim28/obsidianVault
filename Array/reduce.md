#reduce

always need to have return 

```js
const scores = [10,30,15,20,25,55,90,15,95];
// the 0 represents the acc at the start
const result = scores.reduce((acc,curr) => {
	if(curr > 50){
	acc++;
	}
return acc;
},0);

console.log(result);
```

Only add if its mario, dont forget return 
```js
const scores = [
	{player: 'mario', score: 50},
	{player: 'yoshi', score: 30},
	{player: 'mario', score: 70},
	{player: 'crystal', score: 60}
];

const marioTotal = scores.reduce((acc, curr) => {
	if(curr.player === 'mario'){
	acc += curr.score;
	}
return acc;

},0)

console.log(marioTotal);
```