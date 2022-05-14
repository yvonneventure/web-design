# JavaScript

- Comment in js:


 ```javascript
        // this is in-line comment
        
        /* this is 
        multiline comment*/
  ```
  
- 8 Data types in JS 

  - undefined: without initial value, variables are undefined and cannot perform manipulation on it.
  - number: no quotes
  - boolean
  - string: use double or single quotes
  - symbol
  - bigint
  - null
  - object

- Declare a **Variable** first then assign value to variable


 ```javascript
        var a;
        a =7;
        
        var a = 9;  //or create the variable with initial value
  ```      
> Best practice: Write variable names in JavaScript in camelCase. 
> 
> In camelCase, multi-word variable names have the first word in lowercase and the first letter of each subsequent word is capitalized.
 
 ```javascript
 var someVariable;
var anotherVariableName;
var thisVariableNameIsSoLong;
```

> - Declaration of Variables
> 
>  - use `var` can easily overwrite variables declaration and no errors. In some cases, the variable got overwritten in later and it's hard to debug.
>  - use `let myName= "x";` then this variable can only be declared once, and if declare again, wills how error. But you can change the value by reassign value;
>  - use `const` to declare constant variables, usually in capital case: eg. `const HEADER = "sss";`


- increment a number
  - `i++;` equals to `i=i+1;`
  - `i--;` equals to `i=i-1;`

- Calculation in number :`+`,`-`,`*`,`/`,`%`for remainder

- use `+=`,`-=`,`*=`,`/=` like in python

- use `\` to escape

        \'	single quote
        \"	double quote
        \\	backslash
        \n	newline
        \r	carriage return
        \t	tab
        \b	word boundary
        \f	form feed


- get length of the string use `.length` property

```javascript
lengthOfLastName = LastName.length
firstLetterOfLastName = lastName[0]

lastLetter = firstName[firstName.length - 1]
```

### Array in JS is like list in python

   - Append array use `.push()`


   ```javascript
   const arr2 = ["Stimpson", "J", "cat"];
   arr2.push(["happy", "joy"]);   //arr2 has the value ["Stimpson", "J", "cat", ["happy", "joy"]]
   ```
   
   - `.pop()` removes the last element from an array and returns that element.
   
   - `.shift()` removes the first element from an array and returns that element

   -  `.unshift()` adds the element at the beginning of the array.



### function in js

```javascript

//--- Basic function-----//

function functionName() {
  do something;
}

functionName();          // call function

// ----function with arguments-----//

function functionWithArgs(param1, param2) {
  console.log(param1 + param2);
}
functionWithArgs(1,2);

//--- function with output-----//

function plusThree(num) {
  return num + 3;
}

const answer = plusThree(5);
```

### Global vs. Local scope

   - Variables which are defined outside of a function block have Global scope.
   - Variables which are declared without the let or const keywords are automatically created in the global scope whether they are in function or not
   - Variables which are declared within a function, as well as the function parameters, have local scope. 


- if statement: `true` or `false`

```javascript
if (condition is true) {
  statement is executed
}

//-------for example--------//

function test (myCondition) {
  if (myCondition) {
    return "It was true";
  }
  return "It was false";
}

test(true);
test(false);
```

- difference between `==` and `===` (same with `!=` and `!==`)
     - `==` is equlity, and it attempts to convert both values being compared to a common type
     - `===` does not do type conversion

> `>`, `>=`, `<`, `<=` will also convert data types

```javascript
1   ==  1  // true
1   ==  2  // false
1   == '1' // true
"3" ==  3  // true

///-----------///

3 ===  3  // true
3 === '3' // false
```

- `typeof "3" ` to see the data type

- `&&` is and, `||` is or in js

- if, else if, else statements


```javascript
if (num > 15) {
  return "Bigger than 15";
} 
else if (num < 5) {
  return "Smaller than 5";
} 
else {
  return "Between 5 and 15";
}
```

- `switch()` function to make choices/options

```javascript
function caseInSwitch(val) {
  let answer = "";
 
 switch(val) {
  case 1:                           // when val===1, then answer="alpha"
    answer ="alpha";
    break;
    case 2:
    answer ="beta";
    break;
case 3:
    answer ="gamma";
    break;
case 4:
    answer ="delta";
    break;
 }
  return answer;
}

caseInSwitch(1);

//--------------use defualt option---------//
function switchOfStuff(val) {
  let answer = "";
 
switch(val) {
  case "a":                       
    answer ="apple";
    break;
    case "b":
    answer ="bird";
    break;
case "c":
    answer ="cat";
    break;
default:
    answer ="stuff";
    break
}
  return answer;
}

switchOfStuff(1);


//-------------- multiple same options------//
function sequentialSizes(val) {
  let answer = "";
 
switch(val) {
  case 1:
  case 2:
  case 3:
  answer="Low";
  break;
  case 4:
  case 5:
  case 6:
  answer="Mid";
  break;
  case 7:
  case 8:
  case 9:
  answer="High";
  break;
  }
  return answer;
  }
  
  sequentialSizes(1);
```


### Object

- object data type in js is like dictionary in python
 - get value of the key
 - update property
 - add property
 - delete property
 - checking if property exits `.hasOwnProperty()`

```javascript
const myObj = {
  prop1: "val1",
  prop2: "val2"
};

const prop1val = myObj.prop1;
const prop2val = myObj.prop2;

//----or-------//
const prop1val = myObj["prop1"]
const prop2val= myObj["prop1"]


//------delete property in object/dictionary ----//

const ourDog = {
  "name": "Camper",
  "legs": 4,
  "tails": 1,
  "friends": ["everything!"],
  "bark": "bow-wow"
};

delete ourDog.bark;

//----update and add property are same as in python----//

//--------check if property exists------//

const myObj = {
  top: "hat",
  bottom: "pants"
};

myObj.hasOwnProperty("top");
myObj.hasOwnProperty("middle");

```

### Loops

- Simple While loops

```javascript
const ourArray = [];
let i = 0;

while (i < 5) {
  ourArray.push(i);
  i++;
}
```

- simple For loops

 - `for (a; b; c)`, where a is the initialization statement, b is the condition statement, and c is the final expression.

```
// same as the while loop above

const ourArray = [];

for (let i = 0; i < 5; i+=1) {
  ourArray.push(i);
}
// ourArray will now have the value [0, 1, 2, 3, 4]

//--another example--//
const arr = [10, 9, 8, 7, 6];

for (let i = 0; i < arr.length; i++) {
   console.log(arr[i]);
}

```

- Do... while loops

 - run the do {} part first, then check for while condition
 - make sure the part in do {} run at least once

```javascript
const ourArray = [];
let i = 0;

do {
  ourArray.push(i);
  i++;
} while (i < 5);

```

- recursion

 - Recursion is the concept that a function can be expressed in terms of itself or call itself.
 - Recursive functions must have a base case(where n <= 0, it returns 1) when they return without calling the function again, otherwise they can never finish executing.

```javascript

//-------simple for loop--------//
  function multiply(arr, n) {
    let product = 1;
    for (let i = 0; i < n; i++) {
      product *= arr[i];
    }
    return product;
  }

//----replace for loop with recursion-----//

function multiply(arr, n) {
    if (n <= 0) {
      return 1;
    } else {
      return multiply(arr, n - 1) * arr[n - 1];
    }
  }
```

```javascript
//----use recursion create countdown-------//

function countdown(n) {
  if (n < 1) {
    return [];
  } else {
    const arr = countdown(n - 1);
    arr.unshift(n);
    return arr;
  }
}
//----------Use Recursion to Create a Range of Numbers--------//

function rangeOfNumbers(startNum, endNum) {
  if (endNum - startNum < =0) {
    return [startNum];
  } else {
    var numbers = rangeOfNumbers(startNum, endNum - 1);
    numbers.push(endNum);
    return numbers;
  }
}

```


- creat random numbers in js

 - `Math.random()` function that generates a random decimal number between 0 (inclusive) and 1 (exclusive) : `[0,1)`

```javascript
Math.floor(Math.random() * 20);  // give us a whole number between 0 and 19.

Math.floor(Math.random() * (max - min + 1)) + min;   // give us a whole number within range [min,max]

```

- `parseInt()` function to convert string to integer 

 - `const a = parseInt("007");`  a will be integer 7
 - `parseInt(string, radix);` radix specifies the base of the number in the string. 
 - The radix can be an integer between 2 and 36, default is 10.
 - `const a = parseInt("10011", 2);` will return 19

- Use the Conditional (Ternary) Operator

 - The conditional operator, also called the ternary operator, can be used as a one line if-else expression.

```javascript
//----simple if/else statement----//

function findGreater(a, b) {
  if(a > b) {
    return "a is greater";
  }
  else {
    return "b is greater or equal";
  }
}
//--- can be rewritten as ---//

function findGreater(a, b) {
  return a > b ? "a is greater" : "b is greater or equal";
}

//----------for muliple checks------//

function findGreaterOrEqual(a, b) {
  return (a === b) ? "a and b are equal" 
    : (a > b) ? "a is greater" 
    : "b is greater";
}
```























