# JavaScript

- Comment in js:

        // this is in-line comment
        
        /* this is 
        multiline comment*/
        
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

        var a;
        a =7;
        
        var a = 9;  //or create the variable with initial value
        
> Best practice: Write variable names in JavaScript in camelCase. 
> 
> In camelCase, multi-word variable names have the first word in lowercase and the first letter of each subsequent word is capitalized.
 
 ```
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

```
lengthOfLastName = LastName.length
firstLetterOfLastName = lastName[0]

lastLetter = firstName[firstName.length - 1]
```

- Array in JS is like list in python
   - Append array use `.push()`
   ```
   const arr2 = ["Stimpson", "J", "cat"];
   arr2.push(["happy", "joy"]);   //arr2 has the value ["Stimpson", "J", "cat", ["happy", "joy"]]
   ```
   
   - `.pop()` removes the last element from an array and returns that element.
   
   - `.shift()` removes the first element from an array and returns that element

   -  `.unshift()` adds the element at the beginning of the array.

- function in js

```

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

- Global vs. Local scope
   - Variables which are defined outside of a function block have Global scope.
   - Variables which are declared without the let or const keywords are automatically created in the global scope whether they are in function or not
   - Variables which are declared within a function, as well as the function parameters, have local scope. 


- if statement: `true` or `false`

```
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

```
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


```
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

```
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

- object data type in js is like dictionary in python
- 



























