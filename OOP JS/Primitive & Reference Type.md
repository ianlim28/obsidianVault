When its primitive type, JS temporarily wraps that string (example) in a wrapper object

| **Primitive Types**  | **Reference Types** |
|----------------------|---------------------|
| numbers              | all types of object |
| strings              | object literals     |
| booleans             | arrays              |
| null                 | functions           |
| undefined            | dates               |
| symbols              | all other objects   |
| _all above is STACK_ | _all above is HEAP_ |


```js
// new means creating an object, Array is a constructor function
const ages = new Array(20,30,35);
console.log(typeof ages);

// alternative this is another way to create an array, its an object
const names = ['shaun','crystal'];
console.log(typeof names);

// this is a object constructor, use NEW keyword and a constructor
// go to console and youll see all sorts of methods and properties
const userTwo = new String('ryu');
```

