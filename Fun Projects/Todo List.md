#addHTML #todo #trim #addValueWhenSubmit #preventDefault #reset
#eventDelegation #parentElement #classListContain

**Adding html**
just querySelector to find the class, then use template string and replace with variable. When user hits enter (still uses `submit` in eventlisterner), add.value, It also resets the form 

This is the html in index.html
```html
<ul class="list-group todos mx-auto text-light">
<li class="list-group-item d-flex justify-content-between align-items-center">
<span>make a veggie pie</span>
<i class="far fa-trash-alt delete"></i>
</li>
```

```js
const addForm = document.querySelector('.add');
const list = document.querySelector('.todos');
const generateTemplate = (todo) => {
const html = `
	<li class="list-group-item d-flex justify-content-between align-items-center">
	<span>${todo}</span>
	<i class="far fa-trash-alt delete"></i>
	</li>
	`;
	list.innerHTML += html;
};

addForm.addEventListener('submit', e => {
	e.preventDefault();
	const todo = addForm.add.value.trim();
	if(todo.length){
		generateTemplate(todo);
		addForm.reset();
	}
})
```

**Delete html**
when delete is clicked (if its outside it doesnt count), then itll find the parent of the delete class and delete the parents
```js
list.addEventListener('click', e => {
	if(e.target.classList.contains('delete')){
	e.target.parentElement.remove();
}
})
```

FIlter for todo list
#htmlCollection #children #convertToArray
#included 
Cant use array method on htmlCollection
Loops through the children of UL, go through each textContent and filter for a keyword
```html
<form class="search">
	<input class="form-control m-auto" type="text" name="search" placeholder="search todos" />
</form>
```

the `filtered` class is basically a css style with a background display of none
```js
//selecting an input element with the class name "search" using the querySelector method.
const search = document.querySelector('.search input')
const list = document.querySelector('.todos');

const filterToDos = (term) => {
Array.from(list.children)
.filter(todo => !todo.textContent.toLowerCase().includes(term))
.forEach((todo) => todo.classList.add('filtered'));

Array.from(list.children)
.filter(todo => todo.textContent.toLowerCase().includes(term))
.forEach((todo) => todo.classList.remove('filtered'));
};

search.addEventListener('keyup', e => {
	e.preventDefault();
	const term = search.value.trim().toLowerCase();
	filterToDos(term);
})
```