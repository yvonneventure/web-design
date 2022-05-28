# React

React is a popular JavaScript library for building reusable, component-driven user interfaces for web pages or applications. React is an Open Source view library created and maintained by Facebook. It's a great tool to render the User Interface (UI) of modern web applications.

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
















