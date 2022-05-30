# Redux

As applications grow in size and scope, managing shared data becomes much more difficult. Redux is defined as a "predictable state container for JavaScript apps" that helps ensure your apps work predictably, and are easier to test.

**Redux** is a **state management framework** that can be used with a number of different web technologies, including React.


### Create a Redux Store and Get State

In Redux, there is a single state object that holds and manages the entire state of your application. This means if you had a React app with ten components, and each component had its own local state, the entire state of your app would be defined by a single state object housed in the Redux `store`. 

This is the first important principle to understand when learning Redux: the Redux store is the ***single source of truth*** when it comes to application state.

This also means that any time any piece of your app wants to update state, it **must** do so through the Redux store. The ***unidirectional data flow*** makes it easier to track state management in your app.

```js
const reducer = (state = 5) => {

return state;

}


// Define the store here:

const store = Redux.createStore(reducer)

// get current state from store

let currentState = store.getState();

```

### Define a Redux Action

Since Redux is a state management framework, updating state is one of its core tasks. 

In Redux, all state updates are triggered by dispatching actions. An action is simply a JavaScript object that contains information about an action event that has occurred. The Redux store receives these action objects, then updates its state accordingly. 

Sometimes a Redux action also carries some data. For example, the action carries a username after a user logs in. While the data is optional, actions must carry a `type` property that specifies the 'type' of action that occurred.

Think of Redux actions as messengers that deliver information about events happening in your app to the Redux store. The store then conducts the business of updating state based on the action that occurred.


```js
let action={
  type: 'LOGIN'
}
```

After creating an action, the next step is sending the action to the Redux store so it can update its state. 

In Redux, you define action creators to accomplish this. An action creator is simply a JavaScript function that returns an action. In other words, action creators create objects that represent action events.

```js
// define an action
let action={
  type: 'LOGIN'
}

//create action creator to represnet action events
function actionCreator() {
  return action;
}
```

### Dispatch an Action Event

`dispatch` method is what you use to dispatch actions to the Redux store. Calling `store.dispatch()` and passing the value returned from an action creator sends an action back to the store.

```js
// create store with initial state of the object property "login" set to false
const store = Redux.createStore(
  (state = {login: false}) => state
);

// action creator
const loginAction = () => {
  return {
    type: 'LOGIN'
  }
};

// Dispatch the action here:
store.dispatch(loginAction());

// store.dispatch({ type: 'LOGIN' }); also works, and will dispath loginAction
```

### Handle an Action in the Store

After an action is created and dispatched, the Redux store needs to know how to respond to that action. This is the job of a reducer function. 

Reducers in Redux are responsible for the state modifications that take place in response to actions. A `reducer` takes `state` and `action` as arguments, and it always returns a new `state`. 

It is important to see that this is the only role of the reducer. It has no side effects — it never calls an API endpoint and it never has any hidden surprises. The reducer is simply a pure function that takes state and action, then returns new state.

Another key principle in Redux is that `state` is read-only. In other words, the `reducer` function **must always** return a new copy of state and never modify state directly. ❗️Redux does not enforce state immutability, however, you are responsible for enforcing it in the code of your reducer functions.

```js
const defaultState = {
  login: false
};
// don't modify state
const reducer = (state = defaultState, action) => {
  
  if (action.type === "LOGIN") {
    return {
      login: true
    };
  } else {
    return state;
  }
  
};

const store = Redux.createStore(reducer);

const loginAction = () => {
  return {
    type: "LOGIN"
  };
};
```

### Use a Switch Statement to Handle Multiple Actions

You can tell the Redux store how to handle multiple action types. Say you are managing user authentication in your Redux store. You want to have a state representation for when users are logged in and when they are logged out. You represent this with a single state object with the property `authenticated`. You also need action creators that create actions corresponding to user login and user logout, along with the action objects themselves.

The `reducer` function handle multiple authentication actions. Use a JavaScript `switch` statement in the `reducer` to respond to different action events. 

```js
const defaultState = {
  authenticated: false
};

const authReducer = (state = defaultState, action) => {
  
  switch (action.type) {
    case "LOGIN":
      return {
        authenticated: true
      };

    case "LOGOUT":
      return {
        authenticated: false
      };
// important to set default state
    default:
      return defaultState;
  }
  
};

const store = Redux.createStore(authReducer);

const loginUser = () => {
  return {
    type: "LOGIN"
  };
};

const logoutUser = () => {
  return {
    type: "LOGOUT"
  };
};
```

> Always write a default case in your switch statement that returns the current `state`. This is important because once your app has multiple reducers, they are all run any time an action dispatch is made, even when the action isn't related to that reducer. In such a case, you want to make sure that you return the current `state`.

### Use `const` for Action Types

A common practice when working with Redux is to assign **action types** as read-only constants, then reference these constants wherever they are used. You can refactor the code you're working with to write the action types as `const` declarations.

It's generally a convention to write constants in all **uppercase**, and this is standard practice in Redux as well.

```js

// declare const
const LOGIN = 'LOGIN';
const LOGOUT = 'LOGOUT';


const defaultState = {
  authenticated: false
};

const authReducer = (state = defaultState, action) => {

  switch (action.type) {

    case LOGIN:
      return {
        authenticated: true
      }

    case LOGOUT:
      return {
        authenticated: false
      }

    default:
      return state;

  }

};

const store = Redux.createStore(authReducer);

const loginUser = () => {
  return {
    type: LOGIN
  }
};

const logoutUser = () => {
  return {
    type: LOGOUT
  }
};
```

### Register a Store Listener

`store.subscribe()` allows you to subscribe listener functions to the store, which are called whenever an action is dispatched against the store. One simple use for this method is to subscribe a function to your store that simply logs a message every time an action is received and the store is updated.

Write a callback function that increments the global variable `count` every time the store receives an action, and pass this function in to the `store.subscribe()` method. You'll see that `store.dispatch()` is called three times in a row, each time directly passing in an action object. Watch the console output between the action dispatches to see the updates take place.

```js
const ADD = 'ADD';

const reducer = (state = 0, action) => {
  switch(action.type) {
    case ADD:
      return state + 1;
    default:
      return state;
  }
};

const store = Redux.createStore(reducer);

// Global count variable:
let count = 0;
// action of addOne
const addOne = () => {
  return {
    type: ADD
  }
};
// function of counter add 1
const addCounter = () => (count += 1);

// subscribe to the call back function
store.subscribe(addCounter);


store.dispatch({type: ADD});
console.log(count);  //return 1
store.dispatch({type: ADD});
console.log(count); //return 2
store.dispatch({type: ADD});
console.log(count); //return 3
```

### Combine Multiple Reducers







































