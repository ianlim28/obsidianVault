#bubbling

From [Net Ninja Chapter 55,56,57](https://netninja.dev/courses/modern-javascript-from-novice-to-ninja/lectures/31461909)


#innerHTML #append 
```js
const button = document.querySelector('button');
const items = document.querySelectorAll('li');

button.addEventListener('click', () => {
	ul.innerHTML += '<li>something new</li>'
	ul.append(li); // this appends to bottom of the parent
})
```

#textContent #prepend #remove
```js
const button = document.querySelector('button');
const items = document.querySelectorAll('li');

button.addEventListener('click', () => {
	const li = document.createElement('li')
	li.textContent = 'something new to do';
	ul.prepend(li); // this prepends to the top of the parent
})
```

#stopPropagation
if `li` is inside of ul like below, when you click on li, it will propagate upwards, you have to stopPropagation
```html
<ul>
	<li>buy milk</li>
</ul>
```

```js
items.forEach(item => {
	item.addEventListener('click', (e) => {
		console.log('event in LI');
		e.stopPropagation();
		e.target.remove();
})
})
```

#copyEvent
when user copies a text
```js
const copy = document.querySelector('.copy-me');
copy.addEventListener('copy', () => {
	console.log('Oi my content is copyright');
});
```

#mouseMoveEvent
when user moves mouse, display stuff in box class
```js
const box = document.querySelector('.box');
box.addEventListener('mousemove', e => {
	box.textContent = `x: ${e.offsetX} y: ${e.offsetY}`;
})
```

#wheelScrollEvent
queryselector is not needed as you want to catch the scroll of the page, not a specific class
```js
document.addEventListener('wheel', e => {
	console.log(e.pageX, e.pageY);
})
```