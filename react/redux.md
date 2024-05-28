# Redux

Redux is a state management library to help manage the state of your application at the root level.

**1. Core Concepts of Redux**

Let's understand the core concepts of Redux:

**Store:** The single source of truth that holds the state of your application.

**Action:** It's a plain javascript object that describes a change in the state. Actions have a type argument that indicates the type of action being performed and payload argument that defines the data needs to update in store.

**Reducer:** A pure function that takes the current state and an action as arguments and returns a new state.

**Dispatch:** A method used to send actions to the store.

**Selector:** A function that selects a specific part of the state from the store.

---------------

**2. Flow of Redux**

Here’s a step-by-step flow of how Redux works in a React application:

Step 1: Defining Actions

```js

// actions.js
export const INCREMENT = 'INCREMENT';
export const DECREMENT = 'DECREMENT';

export const increment = () => ({
  type: INCREMENT,
});

export const decrement = () => ({
  type: DECREMENT,
});


```

Step 2: Creating Reducers


```js

// reducers.js
import { INCREMENT, DECREMENT } from './actions';

const initialState = {
  count: 0,
};

const counterReducer = (state = initialState, action) => {
  switch (action.type) {
    case INCREMENT:
      return {
        ...state,
        count: state.count + 1,
      };
    case DECREMENT:
      return {
        ...state,
        count: state.count - 1,
      };
    default:
      return state;
  }
};

export default counterReducer;

```

Step 3: Creating the Store

```js

// store.js
import { createStore } from 'redux';
import counterReducer from './reducers';

const store = createStore(counterReducer);

export default store;


```

Step 4: Connecting React Components to the Store

```js

// Counter.js
import React from 'react';
import { useSelector, useDispatch } from 'react-redux';
import { increment, decrement } from './actions';

const Counter = () => {
  const count = useSelector((state) => state.count);
  const dispatch = useDispatch();

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={() => dispatch(increment())}>Increment</button>
      <button onClick={() => dispatch(decrement())}>Decrement</button>
    </div>
  );
};

export default Counter;


```

Step 5: Providing the Store to React

```js

// App.js
import React from 'react';
import { Provider } from 'react-redux';
import store from './store';
import Counter from './Counter';

const App = () => (
  <Provider store={store}>
    <Counter />
  </Provider>
);

export default App;


```

<hr>