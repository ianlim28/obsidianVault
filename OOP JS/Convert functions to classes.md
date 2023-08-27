
#localStorage #classes #constructor #this #await #sync #api #method #properties 

The weather app from Net Ninja was built with individual functions and will be converted to classes in the code snippet before
[[Weather App]] <- Original project

`forecast.js`
```js
class Forecast{
	constructor(){
		this.key = 'WgWNOTAX8ZxrBVT73wM6aRXJYyCFryiK';
		this.weatherURI = 'http://dataservice.accuweather.com/currentconditions/v1/';
		this.cityURI = 'http://dataservice.accuweather.com/locations/v1/cities/search';
	}
	async updateCity(city){
		const cityDets = await this.getCity(city);
		const weather = await this.getWeather(cityDets.Key);
		return { cityDets, weather};
	}
	async getCity(city){
		const query = `?apikey=${this.key}&q=${city}`
		const response = await fetch(this.cityURI+query);
		const data = await response.json()
		return data[0];
	}
	async getWeather(id){
		const query = `${id}?apikey=${this.key}`;
		const response = await fetch(this.weatherURI+query);
		const data = await response.json();
		return data[0];
	}
}
```

`apps.js`
```js
const cityForm = document.querySelector('form');
const card = document.querySelector('.card');
const details = document.querySelector('.details');
const time = document.querySelector('img.time');
const icon = document.querySelector('.icon img');
const forecast = new Forecast();
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
	
	cityForm.addEventListener('submit', (e) => {
		e.preventDefault();
		const city = cityForm.city.value.trim();
		cityForm.reset();
		
		//update the UI with the new city
		forecast.updateCity(city)
		.then(data => updateUI(data))
		.catch(err => err);
		
		// set local storage
		localStorage.setItem('city', city);
	});
	//after page refresh
	if(localStorage.getItem('city')){
		forecast.updateCity(localStorage.getItem('city'))
		.then(data => updateUI(data))
		.catch(err => console.log(err));
}
```

With the local storage, after refresh, if no one enters any city search, itll look inside localStorage and there is a value, itll take that value and update city and UI so there will be results returned 