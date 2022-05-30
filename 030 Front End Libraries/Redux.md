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

When the state of your app begins to grow more complex, it may be tempting to divide state into multiple pieces. Instead, remember the first principle of Redux: ***all app state is held in a single state object in the store. ***

Therefore, Redux provides reducer composition as a solution for a complex state model. You define multiple reducers to handle different pieces of your application's state, then compose these reducers together into one root reducer. The root reducer is then passed into the Redux `createStore()` method.

In order to let us combine multiple reducers together, Redux provides the `combineReducers()` method. This method accepts an object as an argument in which you define properties which associate keys to specific reducer functions. The name you give to the keys will be used by Redux as the name for the associated piece of state.

Typically, it is a good practice to create a reducer for each piece of application state when they are distinct or unique in some way. For example, in a note-taking app with user authentication, one reducer could handle authentication while another handles the text and notes that the user is submitting. For such an application, we might write the `combineReducers()` method like this:

```js
const rootReducer = Redux.combineReducers({
  auth: authenticationReducer,
  notes: notesReducer
});
```

Now, the key `notes` will contain all of the state associated with our notes and handled by our `notesReducer`. This is how multiple reducers can be composed to manage more complex application state. In this example, the state held in the Redux store would then be a single object containing `auth` and `notes` properties.

Another example:

```js
const INCREMENT = 'INCREMENT';
const DECREMENT = 'DECREMENT';

const counterReducer = (state = 0, action) => {
  switch(action.type) {
    case INCREMENT:
      return state + 1;
    case DECREMENT:
      return state - 1;
    default:
      return state;
  }
};

const LOGIN = 'LOGIN';
const LOGOUT = 'LOGOUT';

const authReducer = (state = {authenticated: false}, action) => {
  switch(action.type) {
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

const rootReducer = Redux.combineReducers({
  count: counterReducer,
  auth: authReducer
});

const store = Redux.createStore(rootReducer);
```

### Send Action Data to the Store

By now you've learned how to dispatch actions to the Redux store, but so far these actions have not contained any information other than a `type`. You can also send specific data along with your actions. In fact, this is very common because actions usually originate from some user interaction and tend to carry some data with them. The Redux store often needs to know about this data.

```js
const ADD_NOTE = "ADD_NOTE";

const notesReducer = (state = "Initial State", action) => {
  switch (action.type) {
   // return note text as state
    case ADD_NOTE:
      return action.text;

    default:
      return state;
  }
};
// holds text data and type data now
const addNoteText = note => {

  return {
    type: ADD_NOTE,
    text: note
  };
};

const store = Redux.createStore(notesReducer);

console.log(store.getState());  // return "initial state"
store.dispatch(addNoteText("Hello!"));
console.log(store.getState());  // return "Hello!"
```

### Use Middleware to Handle Asynchronous Actions

So far these challenges have avoided discussing **asynchronous actions**, but they are an unavoidable part of web development. At some point you'll need to call asynchronous endpoints in your Redux app, so how do you handle these types of requests?

Redux provides middleware designed specifically for this purpose, called Redux Thunk middleware. To include Redux Thunk middleware, you pass it as an argument to `Redux.applyMiddleware()`. This statement is then provided as a second optional parameter to the `createStore()` function. Then, to create an asynchronous action, you return a function in the action creator that takes `dispatch` as an argument. Within this function, you can dispatch actions and perform asynchronous requests.

In this example, an asynchronous request is simulated with a `setTimeout()` call. It's common to dispatch an action before initiating any asynchronous behavior so that your application state knows that some data is being requested (this state could display a loading icon, for instance). Then, once you receive the data, you dispatch another action which carries the data as a payload along with information that the action is completed.

Remember that you're passing `dispatch` as a parameter to this special action creator. This is what you'll use to dispatch your actions, you simply pass the action directly to dispatch and the middleware takes care of the rest.

Write both dispatches in the `handleAsync()` action creator. Dispatch `requestingData()` before the `setTimeout()` (the simulated API call). Then, after you receive the (pretend) data, dispatch the `receivedData()` action, passing in this data. 

```js
const REQUESTING_DATA = "REQUESTING_DATA";
const RECEIVED_DATA = "RECEIVED_DATA";
// define actions
const requestingData = () => {
  return { type: REQUESTING_DATA };
};
const receivedData = data => {
  return { type: RECEIVED_DATA, users: data.users };
};

const handleAsync = () => {
  return function(dispatch) {
    // dispatch request action here

    dispatch(requestingData());

    setTimeout(function() {
      let data = {
        users: ["Jeff", "William", "Alice"]
      };
      // dispatch received data action here

      dispatch(receivedData(data));
    }, 2500);
  };
};
// defualt state
const defaultState = {
  fetching: false,
  users: []
};
// reducer: manage states
const asyncDataReducer = (state = defaultState, action) => {
  switch (action.type) {
    case REQUESTING_DATA:
      return {
        fetching: true,
        users: []
      };
    case RECEIVED_DATA:
      return {
        fetching: false,
        users: action.users
      };
    default:
      return state;
  }
};

// create store and call reducer and middleware
const store = Redux.createStore(
  asyncDataReducer,
  Redux.applyMiddleware(ReduxThunk.default)
);
```

### Never Mutate State

Immutable state means that you never modify state directly, instead, you return a new copy of state. If you took a snapshot of the state of a Redux app over time, you would see something like `state 1`, `state 2`, `state 3`,`state 4`, `...` and so on where each state may be similar to the last, but each is a distinct piece of data. This immutability, in fact, is what provides such features as **time-travel debugging** that you may have heard about.

Redux does not actively enforce state immutability in its store or reducers, that responsibility falls on the programmer. Fortunately, JavaScript (especially ES6) provides several useful tools you can use to enforce the immutability of your state, whether it is a `string`, `number`, `array`, or `object`. Note that strings and numbers are primitive values and are immutable by nature. In other words, 3 is always 3. You cannot change the value of the number 3. An `array` or `object`, however, is mutable. In practice, your state will probably consist of an array or object, as these are useful data structures for representing many types of information.

```js
const ADD_TO_DO = 'ADD_TO_DO';

// A list of strings representing tasks to do:
const todos = [
  'Go to the store',
  'Clean the house',
  'Cook dinner',
  'Learn to code',
];

const immutableReducer = (state = todos, action) => {
  switch(action.type) {
    case ADD_TO_DO:
      // Don't mutate state here or the tests will fail
      return state.concat(action.todo);
    // or return [...state, action.todo]
    default:
      return state;
  }
};

const addToDo = (todo) => {
  return {
    type: ADD_TO_DO,
    todo
  }
}

const store = Redux.createStore(immutableReducer);
```

- Use the Spread Operator `...` on Arrays

`let newArray = [...myArray];` . `newArray` is now a clone of `myArray`. Both arrays still exist separately in memory. 

To clone an array but add additional values in the new array, you could write `[...myArray, 'new value']`. This would return a new array composed of the values in myArray and the string new value as the last value. 

❗️It's important to note that it only makes a shallow copy of the array. That is to say, it only provides immutable array operations for **one-dimensional arrays**.




- Remove an Item from an Array

The spread operator can be used here as well. Other useful JavaScript methods include `slice()` and `concat()`.

```js
const immutableReducer = (state = [0, 1, 2, 3, 4, 5], action) => {
  switch (action.type) {
    case "REMOVE_ITEM":
      // don't mutate state here or the tests will fail
      return [
        ...state.slice(0, action.index),
        ...state.slice(action.index + 1, state.length)
      ];
    // or return state.slice(0, action.index).concat(state.slice(action.index + 1, state.length));
    default:
      return state;
  }
};

const removeItem = index => {
  return {
    type: "REMOVE_ITEM",
    index
  };
};

const store = Redux.createStore(immutableReducer);
```

- Copy an Object with `Object.assign`

`Object.assign()` takes a target object and source objects and maps properties from the source objects to the target object. Any matching properties are overwritten by properties in the source objects. This behavior is commonly used to make shallow copies of objects by passing an empty object as the first argument followed by the object(s) you want to copy. Here's an example: `const newObject = Object.assign({}, obj1, obj2);`. This creates `newObject` as a new `object`, which contains the properties that currently exist in `obj1` and `obj2`.

```js
const defaultState = {
  user: "CamperBot",
  status: "offline",
  friends: "732,982",
  
};

const immutableReducer = (state = defaultState, action) => {
  switch (action.type) {
    case "ONLINE":
      // adding state object and overwrite status to "online
      return Object.assign({}, state, { status: "online" });
    default:
      return state;
  }
};

const wakeUp = () => {
  return {
    type: "ONLINE"
  };
};

const store = Redux.createStore(immutableReducer);
```



















