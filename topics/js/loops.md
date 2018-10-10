# Getting loopy in javascript

> Loops are an incredibly useful tool for processing large or variable sums of data or to repeat an operation a set amount of times.

Sometimes you need to deal with a large amount of data. So let's say you are an eccentric billionaire, are you are throwing a fancy dinner party for 600 guests, each of which needs a custom meal. Rather than writing out six hundred functions that assign a meal to each individual guest; we can write a single loop that runs a the meal assignment function 600 times, saving us time and making our code easier to tweak, fix and read. How would that look?

Let's say we had an array with all of our 600 guests stored as objects.

```
let guests = [
  { name : 'Hermina Hubelsplotch', hair : 'brown'},
  { name : 'Harold Blumenfield', hair : 'black' },
  { name : 'Dunco Chillsbader', hair : 'blue' },
  { name : 'Chilp Poddlesboddle', hair : 'bad' },
  { name : 'Hurk Flurk', hair : 'blue' },
  ...
] // Array containing 600 guests
```

## Basic for loop

This is the earliest type of loop in javascript, it's called a `for` loop, while it's the oldest, it's not necessarily the prettiest type of loop. But let's check it out.

```
for( let i = 0; i < 600; i++ ) {
  guest[i].food = randomFood()
}
```

So above we have taken our array containing 600 guests individual guests (here stored as objects), and using the function `randomFood()`, we've assigned the guest a random type of food. The bit within the `for()` statement, says that we are taken the variable `i` setting it to 0, next we are telling the loop to run as long as `i` is below 600, and that each time the loop runs the ariable `i` should increment increase by one. Effectively, we have a loop that will run 600 times.

Instead of using a set number like 600, we would probably have relied on the array length property, that returns the amount of values within an array. So our loop would instead have read `for( let i = 0; i < guests.length; i++ )`, this saves us having to know the exact length of an array.

## ES6 Loops

The above example is the perfect time to instead use an ES6 loop, they are easier to read and often a lot easier working with. Let's work with the same example as above. We could instead have used a `for each` loop, that simply runs through each of the values in the array.

```
guests.forEach(guest => guest.food = randomFood())
```

Here, we are doing the exact same thing, we are taking each of the guests inside of the guests array, looping through each of them and assigning them a food. And you can see it is much more compact and easier to understand, no incrementing variables and statement evaluation like in the normal for loop.

### Evaluating values with ES6

Great, we've assigned the guests food, but what if we needed to categorize them for the seating plan? [ES6 has a lot of powerful types of loops that can do just that](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array), but let's say we wanted to have a table of all blue haired people, to find everybody with blue hair, we can use the filter loop. It works similarly to the `forEach` loop, except it evaluates a statement and if it returns true, it will add the values to a new array.

```
let blueHairedGuests = guests.filter(guest => guest.hair === 'blue')
```

So, here we filtered our original guests array, finding only those with blue hair, and adding them to a new array, without modifying our original guests array.

## While Loops

The `while` loop is the final type of loop, and it's also the most dangerous. A `while` loop runs endlessly while its statement validates as true. (Fastest way of crashing a browser: `while(true){ console.log("Good bye") }`), as of such it's often one worth avoiding. It has its uses, but just be careful not to crash browsers. Let's use it to assign food to each of our guests.

```
let i = 0

while( i < guests.length ) {
  guests[i].food = randomFood()
  i++
}
```

Here, we've told the loop to run as long as i is smaller than the total amount of guests. At the end of the while, we've added `i++` to make sure that we increment the variable `i`, otherwise the loop will run endlessly, crashing the browser.

## Timed loops

Okay, okay, these aren't really loops. But there are timed loops too, like `setInterval()`, which calls a function endlessly at a set interval, until clearInterval is called.

These can be relatively resource intensive, and they certainly shouldn't be our first choice for something like assigning the guests food. But they can be incredibly useful in certain scenarios. Say for example, that we wanted to create a strobe light, we could use the setInterval function to toggle between white and black.

```
let white = false

setInterval(() => {
  if(white) {
    document.body.style.background = "#000"
  } else {
    document.body.style.background = "#fff"
  }
}, 16.6667)
```

It's not going to be very impressive since most screens only update 60 times each second, whereas a strobe light can update much faster. So as setInterval takes it time in milliseconds, we've gone ahead and divided 1000 milliseconds, by 60, to reflect our 60 hz refresh rate, giving us 16.66667.
