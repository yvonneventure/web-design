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




























