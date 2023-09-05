
#eventDelegation 

project: 100days Day 37 Weight Converter

Instead of having multiple addeventlisteners, you can use `classList.contains`, find all the child within the form

```html
<form action="">
<p class="alert alert-info">
Type a value in any of the fields to convert weight
</p>
<div class="mb-3">
<label for="" class="form-label">Weight in pounds</label>
<input type="number" class="form-control form-control-lg pounds" placeholder="Pounds">
</div>
<div class="mb-3">
<label for="" class="form-label">Weight in kilogramgs</label>
<input type="number" class="form-control form-control-lg kilograms" placeholder="Kilograms">
</div>
<div class="mb-3">
<label for="" class="form-label">Weight in Grams</label>
<input type="number" class="form-control form-control-lg grams" placeholder="Grams">
</div>
<div class="mb-3">
<label for="" class="form-label">Weight in Ounces</label>
<input type="number" class="form-control form-control-lg ounces" placeholder="Ounces">
</div>
</form>
```

```js
let pounds = document.querySelector(".pounds"),
kilograms = document.querySelector(".kilograms"),
grams = document.querySelector(".grams"),
ounces = document.querySelector(".ounces"),
form = document.querySelector("form");

//event delegation
//Pounds converter
form.addEventListener('input', convertWeight);
function convertWeight(e) {
	e.preventDefault();
	if (e.target.classList.contains("pounds")) {
		let x = e.target.value;
		kilograms.value =(x / 2.2046).toFixed(2);
		grams.value = (x / 0.0022046).toFixed(2);
		ounces.value = (x * 16).toFixed(2);
	}
	
	if (e.target.classList.contains("kilograms")) {
		let x = e.target.value;
		pounds.value = (x * 2.2046).toFixed(2);
		grams.value = (x * 1000).toFixed(2);
		ounces.value = (x * 35.274).toFixed(2);
	}
	
	if (e.target.classList.contains("grams")) {
		let x = e.target.value;
		kilograms.value = (x / 1000).toFixed(2);
		pounds.value = (x * 0.0022046).toFixed(2);
		ounces.value = (x * 0.035274).toFixed(2);
	}
	
	if (e.target.classList.contains("ounces")) {
		let x = e.target.value;
		kilograms.value = (x / 35.274).toFixed(2);
		grams.value = (x / 0.035274).toFixed(2);
		pounds.value = (x * 0.0625).toFixed(2);
	}
}
```