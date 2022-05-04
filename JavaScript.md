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





































