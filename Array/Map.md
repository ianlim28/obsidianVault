#map

Takes an array, modifies it and stores as new array

```js
const prices = [10,30,15,20,25,55,90];
const salePrices = prices.map((price) => {
	return price / 2;
})

console.log(salePrices);
```

This is okay, because it doesnt edit the original JSON
```js
const products = [
	{name: 'gold star', price: 20},
	{name: 'mushroom', price: 40},
	{name: 'green shells', price: 30},
	{name: 'banana skin', price: 10},
	{name: 'red shells', price: 50}
];

const saleProduct = products.map((product) => {
	if(product.price > 30){
	return {name: product.name, price:product.price / 2};
	} else {
	return product;
}
})
console.log(saleProduct);

// or use the spread method
const updatedProducts = products.map((product) => { 
	if(product.price > 30){ 
	return {...product, price: product.price / 2}; 
	} else { return product; } });
```

This is NOT OKAY, because it edits the original JSON

```js
const products = [
	{name: 'gold star', price: 20},
	{name: 'mushroom', price: 40},
	{name: 'green shells', price: 30},
	{name: 'banana skin', price: 10},
	{name: 'red shells', price: 50}
];

// cant do this directly, else it will edit the original json and we dont want that

const saleProduct = products.map((product) => {
	if(product.price > 30){
	product.price = product.price / 2;
	// return {name: product.name, price:product.price / 2};
}
})
```