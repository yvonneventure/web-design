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


### Use wildcard `.` match any single character 

For example, if you wanted to match `hug, huh, hut, and hum`, you can use the regex `/hu./` to match all four words.

```js
let humStr = "I'll hum a song";
let hugStr = "Bear hug";
let huRegex = /hu./;
huRegex.test(humStr);   // return true
huRegex.test(hugStr);   // return true
```

### Match Single Character with Multiple Possibilities use `[]`

For example, you want to match `bag, big, and bug but not bog`. You can create the regex `/b[aiu]g/` to do this.

```js
let bigStr = "big";
let bagStr = "bag";
let bugStr = "bug";
let bogStr = "bog";
let bgRegex = /b[aiu]g/;
bigStr.match(bgRegex);   // return ["big"]
bagStr.match(bgRegex);   // return ["bag"]
bugStr.match(bgRegex);   // return ["bug"]
bogStr.match(bgRegex);  // return null
```

Inside a character set, you can define a range of characters to match using a hyphen character: `-`. For example, to match lowercase letters a through e you would use `[a-e]`.

#### match any numbers and characters use `/[a-z0-9]/gi`

```js
let jennyStr = "Sam867";
let myRegex = /[a-z0-9]/ig;
jennyStr.match(myRegex); 
// return ["S","a","m","8","6","7"]
```

#### Characters don't want to match `[^]`

For example, `/[^aeiou]/gi` matches all characters that are not a vowel. Note that characters like `., !, [, @, /` and *white space* are matched too.

```js
let quoteSample = "3 blind mice.";
let myRegex = /[^aeiou0-9]/gi; // match charaters not vowels not numbers
quoteSample.match(myRegex);  
// return [ ' ', 'b', 'l', 'n', 'd', ' ', 'm', 'c', '.' ]
```





































