[link](https://date-fns.org/)
[net ninja link](https://netninja.dev/courses/modern-javascript-from-novice-to-ninja/lectures/31493863)

```js
const now = new Date();
console.log(dateFns.isToday(now));

//formatting options
console.log(dateFns.format(now, 'YYYY')); //2023
console.log(dateFns.format(now, 'MMM')); //Jul
console.log(dateFns.format(now, 'dddd')); //Thursday
console.log(dateFns.format(now, 'dddd, Do, MMMM, YYYY')); //Thursday, 13th, July, 2023

// comparing dates
const before = new Date('February 1 2019 12:00:00');
console.log(dateFns.distanceInWords(now, before, {addSuffix:true})); //over 4 years ago
```