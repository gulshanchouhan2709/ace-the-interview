# React Hooks and Custom Hooks

React Hooks are a powerful feature introduced in React 16.8 that allows you to use state and other React features in functional components.

**Common React Hooks**


- useState: Manages state in functional components.

- useEffect: It's basically used to acheive lifecycle methods of class components into functional components.

- useContext: Avoids prop drilling by providing a way to pass data through the component tree.

- useReducer: It's useful for complex state logic. below is the code example. 

```js

import React, { useReducer } from 'react';

const initialState = { count: 0 };

function reducer(state, action) {
  switch (action.type) {
    case 'increment':
      return { count: state.count + 1 };
    case 'decrement':
      return { count: state.count - 1 };
    default:
      return state;
  }
}

const Counter = () => {
  const [state, dispatch] = useReducer(reducer, initialState);

  return (
    <div>
      <p>Count: {state.count}</p>
      <button onClick={() => dispatch({ type: 'increment' })}>Increment</button>
      <button onClick={() => dispatch({ type: 'decrement' })}>Decrement</button>
    </div>
  );
};

export default Counter;


```

<hr>