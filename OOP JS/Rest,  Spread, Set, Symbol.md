#spread #rest #set #symbol 
When you dont know how many parameter youll end up inputing into the function 

**REST**
```js
// rest parameter, when you dont know how many parameters will be inputted
const double = (...nums) => {
	return nums.map(num => num*2);
}

const result = double(1,2,3,4,5,7,5,4,3,4,5);
console.log(result);
```

**SPREAD**
Its a bit the opposite of rest, where you take in a array and spread them out
Doing spread with object makes a full copy of it, not just a pointer
```js
// spread syntax (arrays)
const people = ['shaun','ryu','crystal'];
console.log(...people);

const members = ['mario','chun-li', ...people];


// spread syntax (objects)
const person = { name: 'shaun', age:30, job: 'net ninja'};
const personClone = {...person}; // making a full copy of the object, not just a pointer
```

**SET**
Set removes duplicates but you need `new` keyword in there
```js
// sets
const namesArray = ['ryu','chun-li','ryu','shaun'];
console.log(namesArray);

const namesSet = new Set(namesArray);
console.log(namesSet);

const uniqueNames = [...namesSet];
console.log(uniqueNames);

// everything in one line
const oneLineUnique = [...new Set(namesArray)];
console.log(oneLineUnique);
```

`add` `delete` `size` `has` 
```js
const ages = new Set();
ages.add(20);
ages.add(25).add(30); // you can chain them 
console.log(ages);
ages.delete(25);
console.log(ages, ages.size); // length is not available but size is
console.log(ages.has(30));

ages.clear() // clears out 
```

**Symbol**
```js
// symbol, its primitive type
// no 2 symbols are the same
const symbolOne = Symbol('a generic name');
const symbolTwo = Symbol('a generic name');

console.log(symbolOne === symbolTwo);

const ninja = {};
ninja.age = 30;
ninja['belt'] = 'orange';
ninja['belt'] = 'black'; // this will overwrite the orange

ninja[symbolOne] = 'ryu';
ninja[symbolTwo] = 'shaun';

console.log(ninja);
```

