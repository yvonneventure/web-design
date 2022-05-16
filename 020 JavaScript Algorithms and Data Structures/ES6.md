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



























