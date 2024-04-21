JavaScript uses several naming conventions for different types of entities in the code. Here's a general guideline:

### Camel Case (`camelCase`)

- **Variables**: Regular variables in JavaScript are typically written in camel case.
   
```js
let myVariable;
```

- **Functions**: Functions are also usually named using camel case.
```js
function myFunction() {}    
```

- **Methods**: Similar to functions, method names are also written in camel case.
```js
const myObject = {   myMethod() {} };	
```

- **Instances**: Instances of classes are named using camel case.
```js
const myInstance = new MyClass();
``` 
- **Private properties**: In classes, private fields and methods conventionally start with an underscore followed by camel case.

```js
class MyClass {   _myPrivateField; }
```

### Pascal Case (`PascalCase`)

- **Classes**: Class names are typically written in Pascal case.
```js
class MyClassName {}
```

- **Components**: In React, component names are also written in Pascal case to distinguish them from regular HTML elements.

```js
function MyComponent() {}
```

- **Enums**: Enumerations are often written in Pascal case.

```js
enum Colors {   Red,   Green,   Blue }
```
 
- **Interfaces**: In TypeScript, interface names are usually in Pascal case.
```js
interface MyInterface {}
```

### Upper Case (`UPPER_CASE`)

- **Constants**: Constants that have static, unchanging values are conventionally written in all uppercase with underscores separating words.
```js
const MAX_USERS = 10; const API_KEY = 'abcdef';
```

- **Enum members**: The values of enumerations are often written in uppercase as well.
```js
enum Colors {   RED,   GREEN,   BLUE }
```

### General Guidelines

- **Start with a letter**: Names should always start with a letter, `$`, or `_`, but it's best practice to use letters.
- **Case sensitivity**: Remember that JavaScript is case-sensitive, so `myVariable` and `MyVariable` would be considered two distinct variables.
- **Avoid reserved words**: Don't use reserved keywords in JavaScript as names for variables, functions, methods, or classes.
- **Descriptive names**: Choose names that are descriptive and make the code more readable and understandable.

Following these conventions makes your code easier to read and understand for other developers, adheres to common practice, and helps distinguish between different types of entities at a glance.