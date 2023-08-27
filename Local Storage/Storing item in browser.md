#localStorage 

Values stored inside local storage __will be string and has to be string!!__
inspect element, go to console and type localStorage or window.localStorage (its the same)

```js
// storage data in local storage
localStorage.setItem('name','mario');
localStorage.setItem('age','50');

// get data from local storage
let name = localStorage.getItem('name')
let age = localStorage.getItem('age')
console.log(name, age);

// updating data
localStorage.setItem('name', 'luigi');
localStorage.setItem('age', '40');

name = localStorage.getItem('name');
age = localStorage.getItem('age');

console.log(name);

// deleting data from local storage
localStorage.removeItem('name');

// deleting all local storage
localStorage.clear();
```


Converting to string and storing 

```js
const todos = [
{text: "play mariokart", author:'shaun'},
{text: "buy milk", author:'mario'},
{text: "buy bread", author:'luigi'}
];


// turn into json string before storing in local storage in browser
// console.log(JSON.stringify(todos));
localStorage.setItem('todos', JSON.stringify(todos));
```

Converting local storage back to JSON 

```js
const stored = localStorage.getItem('todos');
//transforming it back to JSON
console.log(JSON.parse(stored));
```

