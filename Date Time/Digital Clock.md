#date #new #innerHTML #setInterval 

Set Interval to call a function every second, that function would just take the current timestamp and display that in the html

```html
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>Dates & Times</title>
<style>
body{
	background: #333;
}
.clock{
	font-size: 4em;
	text-align: center;
	margin: 200px auto;
	color: yellow;
	font-family: Arial, Helvetica, sans-serif;
}

.clock span{
	padding: 20px;
	background: #444;
}

</style>
</head>
	<body>
		<div class="clock"></div>
		<script src="sandbox.js"></script>
	</body>
</html>
```

```js
const clock = document.querySelector('.clock');
const tick = () => {
	const now = new Date();
	const h = now.getHours();
	const m = now.getMinutes();
	const s = now.getSeconds();
	const html = `
	<span>${h}</span> :
	<span>${m}</span> :
	<span>${s}</span>
	`;
	
	clock.innerHTML = html;
}

setInterval(tick,1000);
```