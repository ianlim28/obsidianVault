#chainMethod

This works but chaining works more elegantly
```js
const products = [
{name: 'gold star', price: 30},
{name: 'green shell', price: 10},
{name: 'red shell', price: 40},
{name: 'banana skin', price: 5},
{name: 'mushroom', price: 50}
];

//long version
const filtered = products.filter(product => product.price > 20);
const promos = filtered.map(product => {
	return `the ${product.name} is ${product.price /2} pounds`
})

console.log(filtered);
console.log(promos);
```

This is the chaining method
```js
const products = [
{name: 'gold star', price: 30},
{name: 'green shell', price: 10},
{name: 'red shell', price: 40},
{name: 'banana skin', price: 5},
{name: 'mushroom', price: 50}
];

const promos = products
	.filter(product => product.price > 20)
	.map(product => `the ${product.name} is ${product.price /2} pounds`);

console.log(promos);
```

