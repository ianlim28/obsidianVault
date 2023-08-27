#objectShortHand #api #async #await #fetch  #classListRemove #classListContains #setAttribute 
Accu weather API project
[Net Ninja Weather App](https://netninja.dev/courses/modern-javascript-from-novice-to-ninja/lectures/31515766)
First you need to get the location key, then using the location key you get the weather data
*forecast.js*
```js
const key = '--'; // replace this with own API 

// get weather information
const getWeather = async (id) => {
	const base = 'http://dataservice.accuweather.com/currentconditions/v1/';
	const query = `${id}?apikey=${key}`;
	const response = await fetch(base+query);
	const data = await response.json();
	return data[0];
}

// get city information
const getCity = async (city) => {
	const base = 'http://dataservice.accuweather.com/locations/v1/cities/search';
	const query = `?apikey=${key}&q=${city}`
	const response = await fetch(base+query);
	const data = await response.json()
	// console.log(data[0]);
	return data[0];
}

getCity('manchester')
	.then(data => {
		return getWeather(data.Key);
	})
	.then(data => console.log(data))
	.catch(err => console.log(err));

```

*apps.js*
objectShortHand 
```js
const cityForm = document.querySelector('form');
const card = document.querySelector('.card');
const details = document.querySelector('.details');
const updateUI = (data) => {
	const {cityDets, weather} = data;
	
	// update details template
	details.innerHTML = `
		<h5 class="my-3">${cityDets.EnglishName}</h5>
		<div class="my-3">${weather.WeatherText}</div>
		<div class="display-4 my-4">
		<span>${weather.Temperature.Metric.Value}</span>
		<span>&deg;C</span>
		</div>
	`;
	
	//remove d-none if present
	if(card.classList.contains('d-none')){
		card.classList.remove('d-none')
	}
};

const updateCity = async (city) => {
	const cityDets = await getCity(city);
	const weather = await getWeather(cityDets.Key);
	return {
	// cityDets: cityDets,
	// weather: weather
	//when property name is the same as the value then you can do the following (object short hand)
	cityDets, weather
	};
};

cityForm.addEventListener('submit', (e) => {
	e.preventDefault();
	const city = cityForm.city.value.trim();
	cityForm.reset();
	//update the UI with the new city
	updateCity(city)
		.then(data => console.log(data))
		.catch(err => err);
})
```

**Updating the image in the application**

Use query selector to look for the class then setAttribute
```js
const time = document.querySelector('img.time');
const icon = document.querySelector('.icon img');

const updateUI = (data) => {
const {cityDets, weather} = data;
// update details template
details.innerHTML = `
	<h5 class="my-3">${cityDets.EnglishName}</h5>
	<div class="my-3">${weather.WeatherText}</div>
	<div class="display-4 my-4">
	<span>${weather.Temperature.Metric.Value}</span>
	<span>&deg;C</span>
	</div>
`;

// update the night/day & icon images
const iconSrc = `img/icons/${weather.WeatherIcon}.svg`;
icon.setAttribute('src',iconSrc);
let timeSrc = weather.IsDayTime ? 'img/day.svg' : 'img/night.svg';
time.setAttribute('src', timeSrc);
//remove d-none if present
if(card.classList.contains('d-none')){
	card.classList.remove('d-none')
}
};
```


Local Storage
it will check if there were any values stored in local storage after refresh, if theres a value, then take that, call the API again and load the information. Put this code all the way at the end of the application
```js
if(localStorage.getItem('city')){
updateCity(localStorage.getItem('city'))
.then(data => updateUI(data))
.catch(err => console.log(err));
} 
```
