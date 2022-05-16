# Object Oriented Programming (OOP) in JavaScript

Think about things people see every day, like cars, shops, and birds. These are all objects: tangible things people can observe and interact with.

What are some qualities of these objects? A car has wheels. Shops sell items. Birds have wings.

These qualities, or properties, define what makes up an object. Note that similar objects share the same properties, but may have different values for those properties. For example, all cars have wheels, but not all cars have the same number of wheels.

Objects in JavaScript are used to model real-world objects, giving them properties and behavior just like their real-world counterparts. Here's an example using these concepts to create a `duck` object:

```js
let duck = {
  name: "Aflac",
  numLegs: 2
};
```

Objects can have a special type of property, called a method.

Methods are properties that are functions. This adds different behavior to an object.

```js
let duck = {
  name: "Aflac",
  numLegs: 2,
  sayName: function() {return "The name of this duck is " + this.name + ".";}
};
duck.sayName();
```

### Constructor function to create new object

Constructors are functions that create new objects. They define properties and behaviors that will belong to the new object. Think of them as a blueprint for the creation of new objects.

```js
function Bird(name, color) {
  this.name = name;
  this.color = color;
  this.numLegs = 2;
}

let cardinal = new Bird("Bruce", "red");
```

Anytime a constructor function creates a new object, that object is said to be an instance of its constructor.

`instanceof` allows you to compare an object to a constructor, returning true or false based on whether or not that object was created with the constructor.

```js
let crow = new Bird("Alexis", "black");
crow instanceof Bird;  // return true

// below not use constructor
let canary = {
  name: "Mildred",
  color: "Yellow",
  numLegs: 2
};

canary instanceof Bird;  // return false

```

You can **not** add a new property to an existing object constructor by how you normally add property in object `object.newProperty=""`

To add a new property or method to a constructor, you can either add it directly to constructor function or use `prototype`.

```js
function Person(first, last, age, eyecolor) {
  this.firstName = first;
  this.lastName = last;
  this.age = age;
  this.eyeColor = eyecolor;
}

Person.prototype.nationality = "English";

Person.prototype.name = function() {
  return this.firstName + " " + this.lastName;
};
```

Now all the objects created from constructor will have these added property and method.

When we have more than one instances created from the constructor and they have same preporty, instead of using their own property seperately, they can also use this `prototype` property to reduce line of codes.

- Own properties vs prototype property

```js
function Bird(name) {
  this.name = name;                //own property
}
Bird.prototype.numLegs = 2;       // prototype property
let duck = new Bird("Donald");

let ownProps = [];
let prototypeProps = [];

for (let property in duck) {
  if(duck.hasOwnProperty(property)) {
    ownProps.push(property);
  } else {
    prototypeProps.push(property);
  }
}

console.log(ownProps);   // return ["name"]
console.log(prototypeProps);  // return ["numLegs"]
```

Adding prototype properties individually can be tedious, we can use an new object to set prototype all at once. 



```js
Bird.prototype = {
  numLegs: 2, 
  eat: function() {
    console.log("nom nom nom");
  },
  describe: function() {
    console.log("My name is " + this.name);
  }
};
```

❗️this will erases `constructor` property.

To fix this, whenever a prototype is manually set to a new object, remember to define the constructor property:

```js
Bird.prototype = {
  constructor: Bird,   //!!!
  numLegs: 2,
  eat: function() {
    console.log("nom nom nom");
  },
  describe: function() {
    console.log("My name is " + this.name); 
  }
};
```

`duck` inherits its `prototype` from the `Bird` constructor function. You can show this relationship with the `isPrototypeOf` method:

```js
Bird.prototype.isPrototypeOf(duck);  // return true
``` 

#### Prototype Chain

All objects in JavaScript (with a few exceptions) have a `prototype`. Also, an object’s `prototype` itself is an object.

The prototype of `Bird.prototype` is `Object.prototype`. `Object.prototype` is on the top of the prototype inheritance chain, Bird objects inherit from `Object.prototype`.

❗️ Object> Bird > Duck

Object is the supertype for all objects in js. `Bird` is the supertype for `duck`, while `duck` is the subtype. `Object` is a supertype for both `Bird` and `duck`.


> ❗️There's a principle in programming called **Don't Repeat Yourself (DRY)**. The reason repeated code is a problem is because any change requires fixing code in multiple places. This usually means more work for programmers and more room for errors.


If a method or property shared by multiple objects, then it's better to create a supertype or parent.

```js

unction Cat(name) {
  this.name = name;
}

Cat.prototype = {
  constructor: Cat
};

function Bear(name) {
  this.name = name;
}

Bear.prototype = {
  constructor: Bear
};

function Animal() {}

Animal.prototype = {
  constructor: Animal,
  eat: function() {
    console.log("nom nom nom");
  }
};

// for inheritance, first create an instance of supertype
function Bird() { }
Bird.prototype = Object.create(Animal.prototype);
Bird.prototype.constructor = Bird;  // set all instances of Bird were constructed by Bird not Animal
let duck = new Bird();
duck.constructor
```

To override inherited methods, simpley set the prototype

```js
function Animal() { }
Animal.prototype.eat = function() {
  return "nom nom nom";
};
function Bird() { }

Bird.prototype = Object.create(Animal.prototype);

Bird.prototype.eat = function() {
  return "peck peck peck";
};

let duck = new Bird();
duck.eat()
```

This is how JavaScript looks for the method on the prototype chain of duck:

1. duck => Is eat() defined here? No.
2. Bird => Is eat() defined here? => Yes. Execute it and stop searching.
3. Animal => eat() is also defined, but JavaScript stopped searching before reaching this level.
4. Object => JavaScript stopped searching before reaching this level.


### Use *Mixin* for unrelated Objects

As you have seen, behavior is shared through inheritance. However, there are cases when inheritance is not the best solution. Inheritance does not work well for unrelated objects like Bird and Airplane. They can both fly, but a Bird is not a type of Airplane and vice versa.

For unrelated objects, it's better to use mixins. A mixin allows other objects to use a collection of functions.

```js
let flyMixin = function(obj) {
  obj.fly = function() {
    console.log("Flying, wooosh!");
  }
};

let bird = {
  name: "Donald",
  numLegs: 2
};

let plane = {
  model: "777",
  numPassengers: 524
};

flyMixin(bird);
flyMixin(plane);

// now bird and plane can both fly, both return " Flying, wooosh!"

bird.fly();
plane.fly();
```

#### Prevent properties in object from being modified

- Below `this.hatchedEgg` can be accessed and changed later

```js
function Bird() {
  this.hatchedEgg = 10;
  }
 ```

- To make this public property private is by creating a variable within the constructor function. This changes the scope of that variable to be within the constructor function versus available globally. This way, the variable can only be accessed and changed by methods also within the constructor function.

function Bird() {
  let hatchedEgg = 10;

  this.getHatchedEggCount = function() { 
    return hatchedEgg;
  };
}
let ducky = new Bird();
ducky.getHatchedEggCount();
```

Here `getHatchedEggCount` is a privileged method, because it has access to the private variable `hatchedEgg`. This is possible because `hatchedEgg` is declared in the same context as `getHatchedEggCount`. In JavaScript, a function always has access to the context in which it was created. This is called `closure`.


#### Immediately Invoked Function Expression (IIFE)

```js
(function () {
  console.log("Chirp, chirp!");
})();
```

This is an anonymous function expression that executes right away, and outputs `Chirp, chirp!` immediately.

Note that the function has no name and is not stored in a variable. The two parentheses () at the end of the function expression cause it to be immediately executed or invoked. This pattern is known as an immediately invoked function expression or IIFE.

An immediately invoked function expression (IIFE) is often used to group related functionality into a single object or module.

```js
// group two mixins into a module
let motionModule = (function () {
  return {
    glideMixin: function(obj) {
      obj.glide = function() {
        console.log("Gliding on the water");
      };
    },
    flyMixin: function(obj) {
      obj.fly = function() {
        console.log("Flying, wooosh!");
      };
    }
  }
})();
motionModule.glideMixin(duck);
duck.glide();
```

This returned object contains all of the mixin behaviors as properties of the object. The advantage of the module pattern is that all of the motion behaviors can be packaged into a single object that can then be used by other parts of your code. 





















