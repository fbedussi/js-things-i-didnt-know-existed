::::slide
# JS things I never knew existed
shameless copyed from 

[air.ghost.io/js-things-i-never-knew-existed]([https://air.ghost.io/js-things-i-never-knew-existed/])
::::

::::slide
:::slide
# Label Statements
You can name for loops
````
loop1: // labeling "loop1" 
for (let i = 0; i < 3; i++) { // "loop1"
   loop2: // labeling "loop2"
   for (let j = 0; j < 3; j++) { // "loop2"
      if (i === 1) {
         continue loop1; // continues upper "loop1"
         // break loop1; // breaks out of upper "loop1"
      }
      console.log(`i = ${i}, j = ${j}`);
   }
}

/* 
 * # Output
 * i = 0, j = 0
 * i = 0, j = 1
 * i = 0, j = 2
 * i = 2, j = 0
 * i = 2, j = 1
 * i = 2, j = 2
 */
````
:::

:::slide
and blocks
````
foo: {
  console.log('one');
  break foo;
  console.log('this log will not be executed');
}
console.log('two');

/*
 * # Output
 * one
 * two
 */
````
:::


:::slide
## Browser support
all browsers
:::
::::

::::slide
:::slide
# "void" Operator
The void operator evaluates the given expression and then returns undefined
````
void function iife() {
	console.log('hello');
}();

// is the same as...

(function iife() {
    console.log('hello');
})()

````
:::

:::slide
One cavaet with void is the evaluation of the expression is... void (undefined)!
````
const word = void function iife() {
	return 'hello';
}();

// word is "undefined"

const word = (function iife() {
	return 'hello';
})();

// word is "hello"
Copy

````
:::

:::slide
You can also use void with async, you could then use it as an asynchronous entry point to your code:
````
void async function() { 
    try {
        const response = await fetch('air.ghost.io'); 
        const text = await response.text();
        console.log(text);
    } catch(e) {
        console.error(e);
    }
}()

// or just stick to this :)

(async () => {
    try {
        const response = await fetch('air.ghost.io'); 
        const text = await response.text();
        console.log(text);
    } catch(e) {
        console.error(e);
    }
})();
````
:::


:::slide
## Browser support
all browsers
:::

::::


::::slide
:::slide
# Comma Operator
The comma operator evaluates each of its operands (from left to right) and returns the value of the last operand
````
function myFunc() {
  let x = 0;
  return (x += 1, x); // same as return ++x;
}

y = false, true; // returns true in console
console.log(y); // false (left-most)

z = (false, true); // returns true in console
console.log(z); // true (right-most)
````
:::

:::slide
## With Conditional Operator
````
const type = 'man';

const isMale = type === 'man' ? (
    console.log('Hi Man!'),
    true
) : (
    console.log('Hi Lady!'),
    false
);

console.log(`isMale is "${isMale}"`);

````
:::

:::slide
## Browser support
all browsers
:::

::::

::::slide
:::slide
# I11n API
````
const date = new Date();

const options = {
  year: 'numeric', 
  month: 'long', 
  day: 'numeric'
};

const formatter1 = new Intl.DateTimeFormat('es-es', options);
console.log(formatter1.format(date)); // 22 de diciembre de 2017

const formatter2 = new Intl.DateTimeFormat('en-us', options);
console.log(formatter2.format(date)); // December 22, 2017
````
:::

:::slide
## Plural rules
````
var pr = new Intl.PluralRules();
pr.select(0);
// → 'other' if in US English locale
pr.select(1); 
// → 'one' if in US English locale
pr.select(2);
// → 'other' if in US English locale
````

````
// Arabic has different plural rules
new Intl.PluralRules('ar-EG').select(0);
// → 'zero'
new Intl.PluralRules('ar-EG').select(1); 
// → 'one'
new Intl.PluralRules('ar-EG').select(2);
// → 'two'
new Intl.PluralRules('ar-EG').select(6);
// → 'few'
new Intl.PluralRules('ar-EG').select(18);
// → 'many'
````
:::

:::slide
## Browser support
all browsers, except Opera Mini
:::
::::


::::slide
:::slide


# Pipeline operator
````
const square = (n) => n * n;
const increment = (n) => n + 1;

// without pipeline operator
square(increment(square(2))); // 25

// with pipeline operator
2 |> square |> increment |> square; // 25
````
:::

:::slide
## Browser support
only Firefox 58+ behind a flag
:::
::::

::::slide
:::slide
# [].reduceRight
````
const flattened = [[0, 1], [2, 3], [4, 5]]
    .reduceRight(function(a, b) {
        return a.concat(b);
    }, []);

// flattened array is [4, 5, 2, 3, 0, 1]
````
:::

:::slide
## Browse support
all browsers, IE9+
:::
::::

::::slide
:::slide
# setTimeout() Parameters
````
setTimeout(alert, 1000, 'Hello world!');

/*
 * # Output (alert)
 * Hello World!
 */

function log(text, textTwo) {
    console.log(text, textTwo);
}

setTimeout(log, 1000, 'Hello World!', 'And Mars!');

/*
 * # Output
 * Hello World! And Mars!
 */
````
:::

:::slide
## Browser support
all browsers
:::
::::

::::slide
:::slide
# dataset
````
<div id='person' data-name='john' data-birth-planet='earth'></div>
````
````
let personEl = document.querySelector('#person');

console.log(personEl.dataset) 
// DOMStringMap {name: "john", birthPlanet: "earth"}
console.log(personEl.dataset.name) // john
console.log(personEl.dataset.birthPlanet) // earth

// you can programmatically add more too
personEl.dataset.foo = 'bar';
console.log(personEl.dataset.foo); // bar

// with destructuring
const {name, birthDate} = person.dataset
````
:::

:::slide
## Browser support
all browsers, IE11+
:::
::::