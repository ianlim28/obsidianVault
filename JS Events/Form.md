#submitForm #onsubmit #returnFalse
 event listener is attached to the submit form, not the submit button because we want to submit the form
 
```html
<form class="signup-form">
	<input type="text" id="username" placeholder="username">
	<input type="submit" value="submit">
</form>
```

Default behaviour is that the page refreshes when you submit a form. We want to prevent default action

```js
const form = document.querySelector('.signup-form');
form.addEventListener('submit', (e) => {
	e.preventDefault();
	console.log(form.username.value);
})
```


#livefeedback #userInput
#### Live feedback
this live feedback on user input doesnt really work as intended, its supposed to check against regex and change color instantly. but instead it only changes color when i click on outside the box
```js
const form = document.querySelector('.signup-form');
const feedback = document.querySelector('.feedback');
const usernamePattern = /^[a-z]{6,12}$/;
const username = form.username.value;

form.addEventListener('submit', (e) => {

	e.preventDefault();
	if(usernamePattern.test(username)){
		feedback.textContent = 'that username is valid';
	} else{
		feedback.textContent = 'username must contain letters only and btw 6-12 characters long';
	}
});


//live feedback
form.username.addEventListener('keyup', e => {
	console.log(e);
	if(usernamePattern.test(e.target.value)){	
		form.username.classList.remove('error');
		form.username.classList.add('success');
	}else{
		form.username.classList.remove('success');
		form.username.classList.add('error');
}
});
```

this is the html
```html
<html lang="en">
<head>
	<meta charset="UTF-8">
	<meta name="viewport" content="width=device-width, initial-scale=1.0">
	<title>Document</title>
	<style>
		body{
		background: #eee;
		}
		form{
		max-width: 200px;
		margin: 40px auto;
		background: white;
		padding: 10px;
		}
		input{
		display: block;
		margin: 10px auto;
		padding: 4px;
		}
		.success{
		border: 2px solid limegreen;
		}
		.error{
		border: 2px solid crimson;
		}
	</style>
</head>
<body>

<form class="signup-form">
	<input type="text" id="username" placeholder="username">
	<input type="submit" value="submit">
	<div class="feedback"></div>
</form>
<script src="sandbox.js"></script>
</body>
</html>
```


## onsubmit return false

The purpose of using `return false` in the `onsubmit` attribute of the form is to prevent the form from being submitted to the server. This can be useful when you want to handle form submission with JavaScript code instead of sending the form data to the server.

```html
<form action="" onsubmit="return false">
	<input type="text" class="search" placeholder="Search by city name">
	<button type="submit" class="btn">Submit</button>
	<p class="error"></p>
</form>
```

