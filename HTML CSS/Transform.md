#transform #translate

The "transform: translateY(10rem);" property in the given code means that the element with the class "top" will be moved vertically by 10rem.

In CSS, the transform property is used to apply transformations to an element, such as moving, rotating, scaling, or skewing it. The translateY() function is a specific transformation that moves an element vertically.

In this case, the element will be translated vertically by 10rem, which means it will be moved 10rem downwards from its original position. This can be useful for creating animation effects or positioning elements in a specific way on the webpage.

```css
.top {
	position: fixed;
	bottom: 3rem;
	right: 3rem;
	background-color: transparent;
	padding: 1rem;
	border: 1px solid var(--color-sec);
	outline:none;
	font-size: 2rem;
	cursor: pointer;
	z-index: 111;
	opacity: 0;
	transform: translateY(10rem);
	transition: all .3s;
}
```

