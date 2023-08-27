#smoothScrolling #sticky #toggle

When clicking on nav on the top, it scrolls smoothly down to the section in the bottom. If you link the href id tag in nav li, then itll automatically take you to the section

```html
<nav>
<div class="logo">Logo</div>
	<ul class="nav-list">
		<li><a href="#">Home</a></li>
		<li><a href="#two">Two</a></li>
		<li><a href="#three">Three</a></li>
		<li><a href="#four">Four</a></li>
		<li><a href="#five">Five</a></li>
	</ul>
</nav>
</div>
</header>

<section id="two">
<div class="container box">
	<h2>Section 2</h2>
	<div class="flex">
		<img src="https://picsum.photos/400/250" alt="">
		<p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Obcaecati officiis accusantium, odit commodi sequi architecto cum ad placeat consequuntur voluptas facere cupiditate, tenetur ex iure. Tempore nulla temporibus numquam! Nemo. Lorem ipsum dolor sit amet consectetur adipisicing elit. Obcaecati officiis accusantium, odit commodi sequi architecto cum ad placeat consequuntur voluptas facere cupiditate, tenetur ex iure. Tempore nulla temporibus numquam! Nemo.</p>
	</div>
</div>
</section>
```

```css
html {
	font-size: 10px;
	scroll-behavior: smooth;
}
```

## Sticky Nav bar
when you scroll, you want the nav bar to remain sticky and maybe change the color of the nav bar. You do not need to specify the sticky class in your HTML. The specified CSS rules are applied to any element with the class "sticky" that is a descendant of a "header" element.

```css
header.sticky {
	background-color: white;
	border-bottom: 1px solid #777;
	padding: 1rem 0;
}
```

```js
// sticky header
window.addEventListener('scroll', () => {
	const header = document.querySelector("header");
	header.classList.toggle("sticky", window.scrollY > 0);
});
```

