#sort #sortNumber #sortString #sortJSON #sortObject

String sorting

```js
/ sorting strings, changes directly on the original array, its destructive

const names = ['mario','shaun','chun-li','yoshi','luigi'];
names.sort();
console.log(names);
names.reverse()
console.log(names);
```

Numbers sorting

```js
// sorting numbers, theres 1 caveat, it looks at the first digit, not the whole number, therefore this is not going to work, it will return [10,20,35,45,5,50,70]
const scores = [10,50,20,5,35,70,45];
scores.sort();
console.log(scores);

  
// this will work, when b-a, negative results goes first and positive results go second
scores.sort((a,b) => b-a);
console.log(scores);
```

Sorting objects
```js
// sorting objects
const players = [
	{name: 'mario', score: 20},
	{name: 'luigi', score: 10},
	{name: 'chun-li', score: 50},
	{name: 'yoshi', score: 30},
	{name: 'shaun', score: 70}
];  

// long version
players.sort((a,b) => {
	if(a.score > b.score){
	return -1; // then a will come first
	} else if(b.score > a.score){
	return 1;
	} else {
	return 0;
	}
})

//short version
players.sort((a,b) => b.score - a.score);
console.log(players);
```