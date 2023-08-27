#fetch #catch #throw #newError #response #responseStatus

Simple promise structure to start off with 
```js
// promise example
const getSomething = () => {
	return new Promise((resolve, reject) => {
	//fetch something
	// resolve('some data');
	reject('some error');
})
}

getSomething()
.then(data => {
	console.log(data);
})
.catch(err => {
	console.log(err);
})
```


### Modern Fetch Structure

**Fetch always returns a promise**
```js
// fetch api

fetch('todos/luigi.json')
.then(response => {
	console.log('resolved',response);
	return response.json(); // returns only when its resolved
})
.then((data) => {
	console.log(data);
})
.catch(err => {
	console.log('rejected',err);
})
```

### Async and await

async always returns a promise, not the data 
```js
const getTodos = async () => {
//await will stall until fetch returns a promise, it always does
	const response = await fetch('todos/luigi.json');

	if(response.status !== 200) {
		throw new Error('cannot fetch the data'); //when you throw a new error, the promise inside async is rejected
	}
	
	const data = await response.json(); 
	return data;
};

// still need a then because async returns a promise, not the data
getTodos()
	.then(data => console.log('resolved', data))
	.catch(err => console.log('rejected', err.message))
```






