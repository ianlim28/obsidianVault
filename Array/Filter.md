#filter

```js
const scores = [10,30,15,20,25,55,90];
const result = scores.filter((score) => {
	return score > 20;
});

console.log(result);

const users = [
	{name: 'shaun', premium: true},
	{name: 'yoshi', premium: false},
	{name: 'mario', premium: false},
	{name: 'chun-li', premium: true}
];

// because its only 1 line, we dont need curly braces
const premiumUsers = users.filter(user => user.premium);
console.log(premiumUsers)
```

