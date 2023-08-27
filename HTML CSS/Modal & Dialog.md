#modal #dialog havent gotten to dialog yet
A modal or dialog box is a message box that allows further interactivity of the page without navigating away from the current content in the browser. A modal box is not locked to the screen (i.e., the client can navigate away from it without a required interaction), though it is typically the user’s focus (based on your styling of the box).

```html
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<link rel="stylesheet" href="styles.css">
<title>Learn Modal</title>
</head>
<body>
	<button class="modal-btn">click me, i make a modal</button>
		<div class="modal">
			<div class="modal-content">
			<span class="close-btn">&times;</span>
			<p>this is the text inside the modal</p>
			</div>
		</div>
	<script src="sandbox.js"></script>
</body>
</html>
```

```js
const modalBtn = document.querySelector(".modal-btn");
const modal = document.querySelector(".modal");
const closeBtn = document.querySelector(".close-btn");

modalBtn.addEventListener('click', (e) =>{
console.log(e)
modal.style.display = "block"
})

closeBtn.addEventListener('click', () =>{
modal.style.display = "none"
})
```

```css
.modal {
	display: none;
	position: fixed;
	padding-top: 50px;
	left: 0;
	width: 100%;
	height: 100%;
	background-color: rgb(0, 0, 0);
	background-color: rgba(0, 0, 0, 0.5);
}

.modal-content {
	position: relative;
	background-color: white;
	padding: 20px;
	margin: auto;
	width: 75%;
	-webkit-animation-name: animatetop;
	-webkit-animation-duration: 0.4s;
	animation-name: animatetop;
	animation-duration: 0.4s
}

.close-btn {
	float: right;
	color: lightgray;
	font-size: 24px;
	font-weight: bold;
}

  

.close-btn:hover {
	color: darkgray;
}

@-webkit-keyframes animatetop {
	from {top:-300px; opacity:0}
	to {top:0; opacity:1}
}

@keyframes animatetop {
	from {top:-300px; opacity:0}
	to {top:0; opacity:1}
}
```