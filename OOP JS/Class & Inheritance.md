#chainMethod  #properties #constructor #inheritance  #super  #returnThis
the 'new' keyword
- it creates a new empty object {}
- it binds the value of 'this' to the new empty object
- it calls the constructor function to 'build' the object
- dont comma separate between properties and methods inside class

```js
class User{
	// this is a constructor function
	constructor(username, email){
		// set up properties
		this.username = username;
		this.email = email;
		this.score = 0;
	}
	login(){ // this is regular shorthand function, cant use arrow function
		console.log(`${this.username} just logged in`);
		return this; // need to have return this else you cant chain method
	}
	logout(){
		console.log(`${this.username} just logged out`);
		return this;
	}
	incScore(){
		this.score += 1;
		console.log(`${this.username} has a score of ${this.score}`);
		return this;
	}
}

const userOne = new User('mario','mario@gmail.com'); // this is an instance of the class
const userTwo = new User('luigi','luigi@gmail.com'); // this is an instance of the class

console.log(userOne);
console.log(userTwo);
userOne.login();
userOne.incScore().incScore().incScore();
```

## Inheritance

Admin inherited all the properties and method from User class 

```js
class Admin extends User{
	deleteUser(user){
		users = users.filter(u => u.username !== user.username);
	}
}

const userThree = new Admin('shaun','shaun@gmail.com'); // this is an instance of the class
let users = [userOne, userTwo, userThree];

userThree.deleteUser(userTwo);
console.log(users);
```

## Super 
when you extend a class and want to add properties in there, you'll need to have 'super' and what it does is that it looks inside its parent's class and looks inside their constructor

```js
class Admin extends User{
	constructor(username, email, title){
	//super looks for the parent class and looks for constructor there
	super(username, email);
		this.title = title;
	}
	deleteUser(user){
		users = users.filter(u => u.username !== user.username);
	}
}

const userThree = new Admin('shaun','shaun@gmail.com','black-belt-ninja'); // this is an instance of the class
console.log(userThree);
```

