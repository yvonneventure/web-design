# ES6

- `var` vs. `let`

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









