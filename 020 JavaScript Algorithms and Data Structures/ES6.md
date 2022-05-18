# ES6

#### `var` vs. `let`

  - When you declare a variable with the `var` keyword, it is declared globally, or locally if declared inside a function (not block).

  - The `let` keyword behaves similarly, but with some extra features. When you declare a variable with the let keyword inside a **block, statement, or expression**, its scope is limited to that block, statement, or expression.

```javascript

function checkScope() {
  let i = 'function scope';
  if (true) {
    let i = 'block scope';
    console.log('Block scope i is: ', i);
  }
  console.log('Function scope i is: ', i);
  return i;
}

// two `i` are different, one is function scope, one is block scope.
// to aviod confusion, should use different name.

```

#### `const` 

Some developers prefer to assign all their variables using `const` by default, unless they know they will need to reassign the value. Only in that case, they use `let`.

Objects (including arrays and functions) assigned to a variable using `const` are still **mutable/changeable**. Using the `const` declaration only prevents reassignment of the variable identifier.

#### Prevent Object Mutation use `Object.freeze(objname)`

To ensure your data doesn't change, use function `Object.freeze()` to prevent data mutation.

Any attempt at changing the object will be rejected, with an error thrown if the script is running in strict mode.

### Arrow Function

In JavaScript, we often don't need to name our functions, especially when passing a function as an argument to another function. Instead, we create inline functions. We don't need to name these functions because we do not reuse them anywhere else.

```js
const myFunc = function() {
  const myVar = "value";
  return myVar;
}

// Above function can be rewritten as below
const myFunc = () => {
  const myVar = "value";
  return myVar;
}

//if there's no function body and only a return value, then it can be rewritten like below.

const myFunc = () => "value";
```

- Set default parameters for your function

```js
const greeting = (name = "Anyone") => "Hello " + name;

console.log(greeting("John"));  // return "Hello John"
console.log(greeting());    // return "Hello Anyone"
```


### `...args` (rest parameter) in js like `*args` in python

To create functions that take a variable number of arguments. 

These arguments are stored in an **array** that can be accessed later from inside the function.

```js
function howMany(...args) {
  return "You have passed " + args.length + " arguments.";
}
console.log(howMany(0, 1, 2));
console.log(howMany("string", null, [1, 2, 3], { }));
```

### `...arr` (spread operator)

`...arr` returns an unpacked array. In other words, it spreads the array. However, the spread operator only works in-place, like in an argument to a function or in an array literal.

```js
const arr = [6, 89, 3, 45];
const maximus = Math.max(...arr);


// below code will not work
const spreaded = ...arr;
```

### Destructuring Assignment 

- For extracting and reassign values in object.

```js
const user = { name: 'John Doe', age: 34 };
const { name, age } = user;

//above is equal to
const user = { name: 'John Doe', age: 34 };

const name = user.name;
const age = user.age;
```

- Reassgin a new variable name:

```js
const user = { name: 'John Doe', age: 34 };
const { name: userName, age: userAge } = user;

// above is equal to 
const userName = user.name;
const userAge = user.age;
```

- Use destructuring Assignment in Nested Objects

```js
const user = {
  johnDoe: { 
    age: 34,
    addr: '201 baker street'
  }
};

// extract and assgin with the same name
const { johnDoe: { age, addr }} = user;

// extract and assign with new name
const { johnDoe: { age: userAge, addr: userAddr }} = user;
```

- Use destructuring assignment in Arrays

One key difference between the spread operator and array destructuring is that the spread operator unpacks all contents of an array into a comma-separated list. Consequently, you cannot pick or choose which elements you want to assign to variables.

Destructuring will allow you to choose which element to reassign.

```js
const [a, b] = [1, 2, 3, 4, 5, 6];
console.log(a, b);  //return 1,2

// use comma to access the value at any index in array

const [a, b,,, c] = [1, 2, 3, 4, 5, 6];
console.log(a, b, c);   // return 1,2,5

```

- Use rest parameter

The rest element only works correctly as the last variable in the list. Cannot use the rest parameter in the middle of the array, as don't know how many elements `...arr` represents.

```js
const [a, b, ...arr] = [1, 2, 3, 4, 5, 7];
console.log(a, b);   // return 1,2
console.log(arr);   // return array [3,4,5,7]
```

- Use destructuring assignment to Pass an Object as a Function's Parameters

When object is passed to the above function, the values are destructured from the function parameter for use within the function, no need to sepcify the name of the object.

```js
const stats = {
  max: 56.78,
  standard_deviation: 4.34,
  median: 34.54,
  mode: 23.87,
  min: -0.75,
  average: 35.85
};

const statsUpdate=({mode, average})=>{}; 

const half = ({ max, min }) => (max + min) / 2.0;
```

### Template Literal

- use `${variable name}` so that no need to use `+` for concat
- use ` instead of single or double quotes
- the result will be a mutli-line string, even though no `\n` used

```js
const person = {
  name: "Kate",
  age: 56
};

const greeting = `Hello, my name is ${person.name}!
I am ${person.age} years old.`;

console.log(greeting);

/* return
Hello, my name is Kate!
I am 56 years old.
*/
```


- Declare object use shorthand

```js
const createPerson = (name, age, gender) => ({name,age,gender});
```

- function within object use shorthand


```js
const bicycle = {
  gear: 2,
  setGear(newGear) {
    this.gear=newGear;
  }
};

bicycle.setGear(3);
console.log(bicycle.gear);
```


### Class/object

Pascal case should be used in class name.

Use `class` rather than a function to create class in ES6.

```js
class SpaceShuttle {
  constructor(targetPlanet) {
    this.targetPlanet = targetPlanet;
  }
}
const zeus = new SpaceShuttle('Jupiter');
```

- **Getter functions** are meant to simply return (get) the value of an object's private variable to the user without the user directly accessing the private variable.

- **Setter functions** are meant to modify (set) the value of an object's private variable based on the value passed into the setter function. This change could involve calculations, or even overwriting the previous value completely.

```js
class Book {
  constructor(author) {
    this._author = author;
  }
  // getter
  get writer() {
    return this._author;
  }
  // setter
  set writer(updatedAuthor) {
    this._author = updatedAuthor;
  }
}
const novel = new Book('anonymous');
console.log(novel.writer);   // return 'anonymous'
novel.writer = 'newAuthor';
console.log(novel.writer);  // return 'newAuthor'
```

>  It is convention to precede the name of a private variable with an underscore `_`. 


#### Import and export codes

First, create a script in your **HTML** document with a `type` of `module`. Here’s an example:

```js
<script type="module" src="filename.js"></script>
```

`export` the named functions/variables you need in the js file.

```js
export const add = (x, y) => {
  return x + y;
}

//or below way, both works

const add = (x, y) => {
  return x + y;
}

export { add };

// export multiple variable or functions
export { add, subtract };
```

`import` the part you need in js.

```js
import { add, subtract } from './math_functions.js';

//import everything from file

import * as myMathModule from "./math_functions.js";

myMathModule.add(2,3);
myMathModule.subtract(5,3);
```

use `export default` if only **one** value is being exported from a file. It is also used to create a fallback value for a file or module.

```js
// this is an example of export default a named function
export default function add(x, y) {
  return x + y;
}

// this is an example of export anonymous function
export default function(x, y) {
  return x + y;
}
```

> ❗️Since `export default` is used to declare a fallback value for a module or file, you can only have one value be a default export in each module or file. Additionally, you cannot use export default with `var`, `let`, or `const`

To `import` an `export default`

```js
import add from "./math_functions.js";

/* add here is not in curly barces {}. add here is simply a variable name for whatever the default export of the math_functions.js file is. You can use any name here when importing a default.*/
```

#### JavaScript Promise

A promise in JavaScript is exactly what it sounds like - you use it to make a promise to do something, usually asynchronously. When the task completes, you either fulfill your promise or fail to do so. 

`Promise` is a constructor function, so you need to use the `new` keyword to create one. It takes a function, as its argument, with two parameters - `resolve` and `reject`. These are methods used to determine the outcome of the promise.

```js
const myPromise = new Promise((resolve, reject) => {
  if(condition here) {
    resolve("Promise was fulfilled");
  } else {
    reject("Promise was rejected");
  }
});
// if no condition in {}, the promise will stuck in pending state
```

Promises are most useful when you have a process that takes an unknown amount of time in your code (i.e. something asynchronous), often a server request. When you make a server request it takes some amount of time, and after it completes you usually want to do something with the response from the server. This can be achieved by using the `then` method, which executed immediately after your promise is fulfilled with resolve.

`catch` is the method used when your promise has been rejected. It is executed immediately after a promise's `reject` method is called. 

```js
const makeServerRequest = new Promise((resolve, reject) => {
  // responseFromServer is set to true to represent a successful response from a server
  let responseFromServer = true;
	
  if(responseFromServer) {
    resolve("We got the data");
  } else {	
    reject("Data not received");
  }
});

makeServerRequest.then(result => {
  console.log(result);
});


makeServerRequest.catch(error => {
  console.log(error);
});
```














