# Regular Expression in Java Script

### What's Regex?

Regular expressions are used in programming languages to match parts of strings. You create patterns to help you do that matching.

### Use `.test()` method to test whether matches

The `.test()` method takes the regex, applies it to a string (which is placed inside the parentheses), and returns `true` or `false` if your pattern finds something or not.

The string in `//` is case sensitive. This is called Literal Match.

```js
let testStr = "SomethingCode";
let testRegex = /Code/;
testRegex.test(testStr);    // here returns true

```

To search for multiple patterns, use `|` the `OR` operator.

```js
let petString = "James has a pet cat.";
let petRegex = /cat|dog|fish/;   // search for cat or dog or fish in petString
let result = petRegex.test(petString);
```

To ignore case difference, use `i` flag.

```js
let testStr = "Somethingcode";
let testRegex = /Code/i;
testRegex.test(testStr);    // here returns true, even C is capitalized
```

### Use `.match()` method to extract matches in an array

```js
"Hello, World!".match(/Hello/);   // return ["Hello"]


let ourStr = "Regular expressions";
let ourRegex = /expressions/;
ourStr.match(ourRegex);       // return ["expressions"]
```

To extract a pattern more than once, you can use the `g` flag.

```js
let testStr = "Repeat, Repeat, Repeat";
let ourRegex = /Repeat/;
testStr.match(ourRegex);   // here will return  ["Repeat"]


let repeatRegex = /Repeat/g;
testStr.match(repeatRegex);  //here returns ["Repeat", "Repeat", "Repeat"]
```

> can also use flags together `/search/gi`





































