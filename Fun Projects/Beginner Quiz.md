#scrollTo #animatedScore #setInterval #clearInterval #textContent #removeClassList 

The html code can be found [here](https://github.com/iamshaunjp/modern-javascript/blob/lesson-68/ninja_quiz/index.html)
[link to chapter on Net Ninja](https://netninja.dev/courses/modern-javascript-from-novice-to-ninja/lectures/31463297)
This is an easy fun quiz where you would answer a few questions with radio button and submit the form. It will then bring you back to the top and show an animated result

```js
const correctAnswers = ['B','B','B','B'];
const form = document.querySelector('.quiz-form');
const result = document.querySelector('.result');

form.addEventListener('submit', (e) => {
	e.preventDefault();
	let score = 0;
	const userAnswers = [form.q1.value, form.q2.value, form.q3.value, form.q4.value];
	//check answers
	
	userAnswers.forEach((answer, index) => {
		if(answer === correctAnswers[index]){
	score += 25;
	}
})
/**
* automatically scroll to the top
* window object (global object)
*/
	scrollTo(0,0);
/**
* show results on page
*/
// result.querySelector('span').textContent = `${score}%`; // this is to show static results
// output.setAttribute('class', 'd-block'); //this is 1 way of doing it
	result.classList.remove('d-none');
// this is to show animated results

	let output = 0;
	const timer = setInterval(() => {
	result.querySelector('span').textContent = `${output}%`;
	if(output === score){
	clearInterval(timer);
	} else{
	output++;
	}
	},30)
	})
```



