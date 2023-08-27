#collections  #snapshot #document #getAttribute #snapShot #docChanges #realTime

Different collections for different types of data
![[Screenshot 2023-07-17 at 08.03.15.png]]

```html
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-9ndCyUaIbzAi2FUVXJi0CjmCapSmO7SnpJef0486qhLnuZ2cdeRhO02iuK6FUUVM" crossorigin="anonymous">
<title>Databases (Firebase)</title>
</head>
<body>
	<div class="container my-5">
	<h2>Recipes</h2>
	<ul>
	</ul>
	<form>
		<label for="recipe">Add a new recipe:</label>
		<div class="input-group">
		<input type="text" class="form-control" id="recipe" required>
		<div class="input-group-append">
		<input type="submit" value="add" class="btn btn-outline-secondary">
		</div>
		</div>
	</form>
	<button>unsubscribe from changes</button>
	</div>
	
	<script src="https://www.gstatic.com/firebasejs/5.9.1/firebase-app.js"></script>
	<script src="https://www.gstatic.com/firebasejs/5.9.1/firebase-firestore.js"></script>
	<script>
	const firebaseConfig = {
		apiKey: "AIzaSyBxnOS1bfkXeBalEw5DDnpbF2ni0FqkMAY",
		authDomain: "modern-javascript-learn.firebaseapp.com",
		projectId: "modern-javascript-learn",
		storageBucket: "modern-javascript-learn.appspot.com",
		messagingSenderId: "272090342836",
		appId: "1:272090342836:web:25a5378b72d2c1fb52bee1",
		measurementId: "G-TV6MXJGV6V"
	};
	
	// Initialize Firebase
	firebase.initializeApp(firebaseConfig);
	const db = firebase.firestore();
	// const analytics = getAnalytics(app);
	</script>
	<script src="sandbox.js"></script>
</body>
</html>
```


```js
const list = document.querySelector('ul');
const form = document.querySelector('form');
const button = document.querySelector('button');

const addRecipe = (recipe, id) => {
	let time = recipe.created_at.toDate();
	let html = `
		<li data-id="${id}">
		<div>${recipe.title}</div>
		<div><small>${time}</small></div>
		<button class="btn btn-danger btn-sm my-2">delete</button>
		</li>
	`;
	
	list.innerHTML += html;
};

// get documents, this is the one time version, it only gets data when the page refreshes
// db.collection('recipes').get().then(snapshot => {
// snapshot.docs.forEach(doc => {
// addRecipe(doc.data(), doc.id);
// });
// }).catch(err => {
// console.log(err);
// });

const deleteRecipe = (id) => {
	const recipes = document.querySelectorAll('li');
	recipes.forEach(recipe => {
		if(recipe.getAttribute('data-id') === id){
		recipe.remove(); // removing from DOM
	}
	})
}

// this is the real time version, everytime sth happens, itll return results of what happened
const unsub = db.collection('recipes').onSnapshot(snapshot => {
	// console.log(snapshot.docChanges());
	snapshot.docChanges().forEach(change => {
		const doc = change.doc;
		if(change.type === 'added'){
			addRecipe(doc.data(), doc.id)
		} else if (change.type === 'removed'){
			deleteRecipe(doc.id);
		}
		})
})

// save documents
form.addEventListener('submit', e => {
	e.preventDefault();
	const now = new Date();
	const recipe = {
		title: form.recipe.value,
		created_at: firebase.firestore.Timestamp.fromDate(now)
};

db.collection('recipes').add(recipe).then(() => {
	console.log('recipe added');
}).catch(err => {
	console.log(err);
});
});

// deleting data
list.addEventListener('click', e => {
	// console.log(e)
	if(e.target.tagName === 'BUTTON'){
	const id = e.target.parentElement.getAttribute('data-id');
	// console.log(id);
	db.collection('recipes').doc(id).delete().then(() => {
	console.log('recipe deleted');
	});
	}
});

//sub from db changes
button.addEventListener('click', () => {
	unsub();
	console.log('unsubscribed from collection changes');
})
```

