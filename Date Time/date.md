#date #timestamp
```js
// dates & times
// date is a constructor, like calling a function, date is an object
const now = new Date();
console.log(now);
console.log(typeof now);

// year, months, day, times
console.log('getFullYear:', now.getFullYear());
console.log('getMonth', now.getMonth()); // starts from 0, dont forget
console.log('getDay', now.getDay()); // monday is 1
console.log('getHours', now.getHours()); //
console.log('getMinutes', now.getMinutes()); //
console.log('getSeconds', now.getSeconds()); //

// timestamps
console.log('timestamp', now.getTime()); //number milliseonds since 1 Jan 1970

//date strings
console.log(now.toDateString()); //Wed Jul 12 2023
console.log(now.toTimeString());
console.log(now.toLocaleTimeString());
```

### Timestamp
**Comparing timestamps**
```js
// comparing timestamps
const before = new Date('February 1 2019 7:30:59');
const now = new Date();

// console.log(now.getTime(), before.getTime());

const diff = now.getTime() - before .getTime();
console.log(diff);

const mins = Math.round(diff / 1000 / 60) //1 sec is 1000 ms
console.log(mins);

const hours = Math.round(mins / 60) //1 hour has 60 mins
console.log(hours);

const days = Math.round(hours / 60) //1 day has 24 hours
console.log(days);
console.log(mins, hours, days);
console.log(`the blog was written ${days} ago`);
```

**Converting numbers** (timestamps) back to object to do comparison

```js
// converting timestamps into date objects
const timestamp = 140223000418;
console.log(new Date(timestamp));
```

