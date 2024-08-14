#appendChild #parentNode #localStorage
This project contains 2 parts with storage, one is where if the browser is refreshed, data is gone, the other version is local story
 
```html
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>Document</title>
<script
src="https://kit.fontawesome.com/1935d064dd.js"
crossorigin="anonymous"
></script>

<link rel="stylesheet" href="styles.css" />
</head>
<body>
<section>
<div class="container">
<div class="add-item">
<form action="" >
<input type="text" placeholder="Add a task">
<button>Add</button>
</form>
</div>
</div>

<!-- Unordered list -->
<h2>List of Tasks To Do</h2>
<hr />
<ol class="todo-list">
<!-- <li>
Task1
<button><i class="fas fa-trash-alt"></i></button>
</li> -->
</ol>
<hr>
<button class="clear">Clear Task</button>

</section>
<script src="script.js"></script>
</body>
</html>
```

Version 1 -> refresh browser and data is gone
```js
const input = document.querySelector('input'),
btn = document.querySelector('button'),
todo#List = document.querySelector('.todo-list'),
clear = document.querySelector('.clear');

// add list item
const addTask = (e) => {
	e.preventDefault();
	const newLi = document.createElement('li');
	const delBtn = document.createElement('button');
	
	delBtn.innerHTML = '<i class="fas fa-trash-alt"></i>';

if (input.value !== "") {
	newLi.textContent = input.value;
	newLi.appendChild(delBtn);
	todoList.appendChild(newLi);
	input.value = "";
} else {
	alert("Please enter a task");
};

//delete function
delBtn.addEventListener('click', function() {
	const del = confirm("You are about to delete this task");
	if(del == true) {
		const parent = this.parentNode;
		parent.remove();
	}
	})
};

btn.addEventListener('click', addTask);
	clear.addEventListener('click', () => {
	todoList.innerHTML = "";
})
```