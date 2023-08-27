#readystate #XMLHttpRequest #JSON
[readystate](https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest/readyState)

i think XMLHttpRequest is quite old school but anyway. 
So, the request is wrapped in getTodos function that takes a callback parameter with err and data
```js
const getTodos = (callback) => {
const request = new XMLHttpRequest();

request.addEventListener('readystatechange', ()=>{
	// console.log(request, request.readyState);
	if(request.readyState === 4 && request.status === 200){
		// console.log(request.responseText);
		callback(undefined, request.responseText);
		} else if(request.readyState === 4) {
		// console.log('could not fetch the data');
		callback('could not fetch data', undefined);
		}
	})
	
	request.open('GET','https://jsonplaceholder.typicode.com/todos/');
	request.send();
}

// always do err first then data
getTodos((err, data) => {
	console.log('callback fired');
	// console.log(err, data);
	if(err){
		console.log(err);
		} else {
		console.log(data);
	}
});
```

Asked ChatGPT to write the above in more modern JS and this is the output. Not sure how succinct this is.
```js
const getTodosModern = (callback) => {
	fetch('https://jsonplaceholder.typicode.com/todos/')
	.then(response => {
		if (response.ok) {
		return response.json();
		} else {
		throw new Error('Could not fetch data');
		} 
	})
	.then(data => {
	callback(undefined, data);
	})
	.catch(error => { callback(error.message, undefined); });
}

getTodosModern((err, data) => {
	console.log('callback fired');
	if (err) {
	console.log(err);
	} else {
	console.log(data);
} });
```

JSON has to be in double quotes
```json
[
	{
		"userId": 2,
		"id": 40,
		"title": "totam atque quo nesciunt",
		"completed": true
	},
	{
		"userId": 3,
		"id": 41,
		"title": "aliquid amet impedit consequatur aspernatur placeat eaque fugiat suscipit",
		"completed": false
	}
]
```