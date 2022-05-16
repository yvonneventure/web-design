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



































