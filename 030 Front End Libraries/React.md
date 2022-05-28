# React 

[React](https://reactjs.org/docs/getting-started.html) is a popular JavaScript library for building reusable, component-driven user interfaces for web pages or applications. React is an Open Source view library created and maintained by Facebook. It's a great tool to render the User Interface (UI) of modern web applications.

React combines HTML with JavaScript functionality into its own markup language called **JSX**, that allows you to **write HTML directly within JavaScript**. It lets you use the full programmatic power of JavaScript within HTML, and helps to keep your code readable. React also makes it easy to manage the flow of data throughout the application.


Since JSX is a syntactic extension of JavaScript, you can actually **write JavaScript directly within JSX**. To do this, you simply include the code you want to be treated as JavaScript within curly braces:` { 'this is treated as JavaScript code' }`. 

However, because JSX is not valid JavaScript, JSX code must be compiled into JavaScript. The transpiler Babel is a popular tool for this process. 


```js
// Create a simple JSX element

 const JSX = <h1>Hello JSX!</h1>;
 ```

One important thing to know about nested JSX is that it must return a single element. This one parent element (`div`) would wrap all of the other levels of nested elements.

```js
// create a complex JSX element
const JSX = 
<div>
  <h1>Heading.</h1>
  <p>Paragraph</p>
 <ul>
  <li>Coffee</li>
  <li>Tea</li>
  <li>Milk</li>
</ul>
</div>;  
```

### Commenting in JSX

You can comment as you used to do with code blocks in JavaScript `/* some JS code */` but they need to wrapped by curly braces to add comments in JSX:

```
{/*
<h1>Hanoi University of Science</h1>
<p>Falculty of Mathematics, Mechanics and Informatics</p>  
*/}
```

### Render HTML Elements to the DOM

JSX is a convenient tool to write readable HTML within JavaScript. With React, we can render this JSX directly to the HTML DOM using React's rendering API known as ReactDOM.

ReactDOM offers a simple method to render React elements to the DOM which looks like this: `ReactDOM.render(componentToRender, targetNode)`, where the first argument is the React element or component that you want to render, and the second argument is the DOM node that you want to render the component to. For example, 

```js
// render JSX element
const JSX = (
  <div id='challenge-node' >
    <h1>Hello World</h1>
    <p>Lets render this to the DOM</p>
  </div>
);
ReactDOM.render(JSX, document.getElementById("challenge-node"))
```

As you would expect, `ReactDOM.render()` must be called after the JSX element declarations, just like how you must declare variables before using them.


### Define an HTML Class in JSX

So far, it may seem that HTML and JSX are exactly the same.

One key difference in JSX is that you can no longer use the word `class` to define HTML classes. This is because class is a reserved word in JavaScript. Instead, JSX uses `className`.

In fact, the naming convention for all HTML attributes and event references in JSX become **camelCase**. For example, a click event in JSX is `onClick`, instead of `onclick`. Likewise, onchange becomes onChange. While this is a subtle difference, it is an important one to keep in mind moving forward.

```js
const JSX = (
  <div className='myDiv'>
    <h1>Add a class to this div</h1>
  </div>
);
```

### Self-Closing JSX Tags

Another important way in which JSX differs from HTML is in the idea of the self-closing tag.

In HTML, almost all tags have both an opening and closing tag: `<div></div>`;  However, there are special instances in HTML called “self-closing tags”.For example the line-break tag can be written as `<br>` or as `<br />`, but should never be written as `<br></br>`, since it doesn't contain any content.

In JSX, the rules are a little different. **Any JSX element can be written with a self-closing tag, and every element must be closed**. The line-break tag, for example, must always be written as `<br />` in order to be valid JSX that can be transpiled. A `<div>`, on the other hand, can be written as `<div />` or `<div></div>`. The difference is that in the first syntax version there is no way to include anything in the `<div />`. 

```js
const JSX = (
  <div>
    
    <h2>Welcome to React!</h2> <br />
    <p>Be sure to close all tags!</p>
    <hr />
        
  </div>
);
```

### React Component

Everything in React is a component.

There are two ways to create a React component. 

1. Use a JavaScript function. Defining a component in this way creates a **stateless functional component**. (For now, think of a stateless component as one that can receive data and render it, but does not manage or track changes to that data. )

To create a component with a function, you simply write a JavaScript function that returns either JSX or `null`. One important thing to note is that React requires your function name to begin with a **capital letter**. Here's an example of a stateless functional component that assigns an HTML class in JSX:

```js
const DemoComponent = function() {
  return (
    <div className='customClass'> 
    <h2>Welcome to React!</h2> <br />
    <p>Be sure to close all tags!</p>
    <hr />
       
    </div>
  );
};
```

Because a JSX component represents HTML, you could put several components together to create a more complex HTML page. This is one of the key advantages of the component architecture React provides. It allows you to compose your UI from many separate, isolated components. This makes it easier to build and maintain complex user interfaces.

2. Use ES6 `class` syntax to define a React component.

This creates an ES6 class `MyComponent` which extends the `React.Component` class. So the `MyComponent` class now has access to many useful React features, such as local state and lifecycle hooks. 

Also notice the `MyComponent` class has a `constructor` defined within it that calls `super()`. It uses `super()` to call the constructor of the parent class, in this case `React.Component`. The constructor is a special method used during the initialization of objects that are created with the class keyword. It is best practice to call a component's constructor with super, and pass props to both. This makes sure the component is initialized properly. 

```js
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
  }

  render() {
    return (
      <div>
       <h1>Hello React!</h1>
      </div>
    );
  }
}
```

### Create a Component with Composition

How we can compose multiple React components together.

To compose these components together, you could create an **parent component** which renders each of these three components as children. To render a component as a child in a React component, you include the component name written as a custom HTML tag in the JSX. 

When React encounters a custom HTML tag that references another component it should be wrapped in `< />`.

```js
const ChildComponent = () => {
  return (
    <div>
      <p>I am the child</p>
    </div>
  );
};


class ParentComponent extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return (
      <div>
        <h1>I am the parent</h1>
        <ChildComponent />
      </div>
    );
  }
}
```

### Use React to Render Nested Components

Component composition is one of React's powerful features. When you work with React, it is important to start thinking about your user interface. 

You break down your UI into its basic building blocks, and those pieces become the components. This helps to separate the code responsible for the UI from the code responsible for handling your application logic. It can greatly simplify the development and maintenance of complex projects.


```js
const TypesOfFruit = () => {
  return (
    <div>
      <h2>Fruits:</h2>
      <ul>
        <li>Apples</li>
        <li>Blueberries</li>
        <li>Strawberries</li>
        <li>Bananas</li>
      </ul>
    </div>
  );
};
const Fruits = () => {
  return (
    <div>
      { /* TypesOfFruit is nested within Fruits */ }
      <TypesOfFruit/>
      
    </div>
  );
};

class TypesOfFood extends React.Component {
  constructor(props) {
    super(props);
  }

  render() {
    return (
      <div>
        <h1>Types of Food:</h1>
        { /* Fruites is nested within TypesOfFood*/ }
          <Fruits/>
        
      </div>
    );
  }
};
```

### Render React Component to the DOM

React components are passed into `ReactDOM.render()` a little differently than JSX elements. 

For JSX elements, you pass in the name of the element that you want to render. 

For React components, you need to use the same syntax as if you were rendering a nested component, for example `ReactDOM.render(<ComponentToRender />, targetNode)`. 

❗️You use this syntax for both ES6 class components and functional components.

```js

class MyComponent extends React.Component{
  constructor(props){
    super(props);
  }
  render(){
    return(
          <div id="challenge-node">
                 <h1>My First React Component!</h1>
          </div>
    );
  }
};
ReactDOM.render(<MyComponent/>, document.getElementById("challenge-node"));
```

### Pass Props to a Stateless Functional Component

In React, you can pass `props`, or properties, to child components. 
 
It is standard to call this value props and when dealing with stateless functional components, you basically consider it as an argument to a function which returns JSX. 

Say you have an `div` component which renders a child component called `CurrentDate` which is a stateless functional component. You can pass `CurrentDate` a `date` property  like in the second half of below codes.

You use **custom HTML attributes** created by you and supported by React to be passed to the component. In this case, the created property `date` is passed to the component `CurrentDate`. Since `CurrentDate` is a stateless functional component, it has access to this value like ` {props.date}`:

```js
const CurrentDate = (props) => {
  return (
    <div>
      <p>The current date is: {props.date}</p>
    </div>
  );
};

class Calendar extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return (
      <div>
        <h3>What date is it?</h3>
        <CurrentDate date={Date()} />
      </div>
    );
  }
};
```

### Pass an Array as Props

```js
// for display, use comma to seperate items in list
const List = props => {
  return <p>{props.tasks.join(", ")}</p>;
};


class ToDo extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return (
    {/* Basic structure of UI*/}
      <div>
        <h1>To Do Lists</h1>
        <h2>Today</h2>
        {/* Passing in items of the list with tasks property*/}
        <List tasks={["Walk", "Cook", "Bake"]} />
        <h2>Tomorrow</h2>
        <List tasks={["Study", "Code", "Eat"]} />
      </div>
    );
  }
}
```

### Use Default Props

This allows you to specify what a prop value should be if no value is explicitly provided.

MyComponent.defaultProps = { prop1: 'value' }

```js
const ShoppingCart = props => {
  return (
    <div>
      <h1>Shopping Cart Component</h1>
    </div>
  );
};

ShoppingCart.defaultProps = {
  items: 0,
  names: 'cart'
};
```

### Override Default Props

Use `<Component propsName={Value}/>` to override default props value.

```js
const Items = (props) => {
  return <h1>Current Quantity of Items in Cart: {props.quantity}</h1>
}

Items.defaultProps = {
  quantity: 0
}

class ShoppingCart extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    { /* override default quantity of 0 to 10*/ }
    return <Items quantity={10}/>
   
  }
};
```

### Use PropTypes to Define the Props You Expect

React provides useful type-checking features to verify that components receive props of the correct type. For example, your application makes an API call to retrieve data that you expect to be in an `array`, which is then passed to a component as a prop. You can set `propTypes` on your component to require the data to be of type array. This will throw a useful warning when the data is of any other type.

It's considered a best practice to set `propTypes` when you know the type of a prop ahead of time. Doing this will check that props of a given key are present with a given type. 

```js
const Items = (props) => {
  return <h1>Current Quantity of Items in Cart: {props.quantity}</h1>
};

//require quantity as a prop and verify that it is of type number.
Items.propTypes = {
  quantity: PropTypes.number.isRequired
};

Items.defaultProps = {
  quantity: 0
};

class ShoppingCart extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return <Items />
  }
};
```

> Note: As of React v15.5.0, `PropTypes` is imported independently from React, like this: `import PropTypes from 'prop-types'`;

Other types at [here](https://reactjs.org/docs/typechecking-with-proptypes.html#proptypes)

### Access Props Using `this.props` for class component

If the child component that you're passing a prop to is an ES6 class component, rather than a stateless functional component? The ES6 class component uses a slightly different convention to access props.

Anytime you refer to a class component within itself, you use the `this` keyword. To access props within a class component, you preface the code that you use to access it with `this`. For example, if an ES6 class component has a prop called `data`, you write `{this.props.data}` in JSX.

```js
/*Render an instance of the Welcome component in the parent component App. Here, give Welcome a prop of name and assign it a value of a string. Within the child, Welcome, access the name prop within the strong tags.*/

class App extends React.Component {
  constructor(props) {
    super(props);

  }
  render() {
    return (
        <div>
            { /* child component welcome is rendered with prop value passed to welcome*/ }
            <Welcome name="Jessica"/>
            
        </div>
    );
  }
};

class Welcome extends React.Component {
  constructor(props) {
    super(props);

  }
  render() {
    return (
        <div>
          { /* Access it's value use this */ }
          <p>Hello, <strong>{this.props.name}</strong>!</p>
         
        </div>
    );
  }
};
```

### Stateless vs. Stateful | Functional Component vs. Compenent

Passing props to **stateless functional components** are like pure functions. They accept props as input and return the same view every time they are passed the same props. 

A **stateless functional component** is any function you write which accepts props and returns JSX. 

A **stateless component** is a class that extends React.Component, but does not use internal state. 

A **stateful component** is a class component that does maintain its own internal state. You may see stateful components referred to simply as components or React components.

> A common pattern is to try to minimize statefulness and to create **stateless functional components** wherever possible. This helps contain your state management to a specific area of your application. In turn, this improves development and maintenance of your app by making it easier to follow how changes to state affect its behavior.


```js
class CampSite extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return (
      <div>
        <Camper/>
      </div>
    );
  }
};

// stateless funtional component
const Camper = props => <p>{props.name}</p>;

Camper.defaultProps = {
  name: "CamperBot"
};

Camper.propTypes = {
  name: PropTypes.string.isRequired
};
```

### Create a Stateful Component

One of the most important topics in React is `state`. 

**State** consists of any data your application needs to know about, that can change over time. You want your apps to respond to state changes and present an updated UI when necessary. 

React offers a nice solution for the state management of modern web applications.

You create state in a React component by declaring a `state` property on the component class in its `constructor`. This initializes the component with `state` when it is created. The `state` property must be set to a JavaScript `object`. 

```js
class StatefulComponent extends React.Component {
  constructor(props) {
    super(props);
    // initialize state here
   
    this.state = {
      name : "Name"
    }

  }
  render() {
    return (
      <div>
        <h1>{this.state.name}</h1>
      </div>
    );
  }
};
```

### Render State in the User Interface

Once you define a component's initial state, you can display any part of it in the UI that is rendered. If a component is stateful, it will always have access to the data in `state` in its `render()` method. You can access the data with `this.state`.

If you want to access a state value within the `return` of the render method, you have to enclose the value in curly braces `{}`. ( In JSX, any code you write with curly braces { } will be treated as JavaScript. )

`state `is one of the most powerful features of components in React. It allows you to track important data in your app and render a UI in response to changes in this data. If your data changes, your UI will change. 

React uses what is called a virtual DOM, to keep track of changes behind the scenes. When state data updates, it triggers a re-render of the components using that data - including child components that received the data as a prop. React updates the actual DOM, but only where necessary. This means you don't have to worry about changing the DOM. You simply declare what the UI should look like.

Note that if you make a component stateful, no other components are aware of its `state`. Its `state` is completely encapsulated, or local to that component, unless you pass state data to a child component as `props`. This notion of encapsulated `state` is very important because it allows you to write certain logic, then have that logic contained and isolated in one place in your code

```js
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      name: 'initialState'
    }
  }
  render() {
    return (
      <div>
        { /* get state value in child use {}*/ }
        <h1>{this.state.name}</h1>
       
      </div>
    );
  }
};
```

There is another way to access `state` in a component. In the `render()` method, before the `return` statement, you can write JavaScript directly. For example, you could declare functions, access data from `state` or `props`, perform computations on this data, and so on. Then, you can assign any data to variables, which you have access to in the `return` statement.

```js
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      name: 'initialState'
    }
  }
  render() {
    // use js directly to get the state and assign to a var called "name"
    const name = this.state.name;
    // change code above this line
    return (
      <div>
        { /* Use var name directly here*/ }
          <h1>{name}</h1>
       
      </div>
    );
  }
};
```

### Set State with `this.setState`

You call the setState method within your component class on your props like so: `this.setState()`, passing in an object with key-value pairs. 

Use `bind(this)` when you call a function like `this.setState()` within your class method, this refers to the class and will not be undefined, as this can also refer to the class.

Syntax like this :
```js
class MyClass {
  constructor() {
    this.myMethod = this.myMethod.bind(this);
  }

  myMethod() {
    // whatever myMethod does
  }
}
```

For example:

```js
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      name: 'Initial State'
    };
    /* bind*/
    this.handleClick = this.handleClick.bind(this);
  }
  
  handleClick() {
    // set state here
    this.setState({
      name: 'React Rocks!'
    });
    
  }
  render() {
    return (
      <div>
        <button onClick={this.handleClick}>Click Me</button>
        <h1>{this.state.name}</h1>
      </div>
    );
  }
};
```

### Use State to Toggle an Element



















