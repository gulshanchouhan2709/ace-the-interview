# Class and Functional Components

key differences between class components and functional components in React:

**Syntax:**

Class Components: Defined using ES6 classes and extend the React.Component class.
Functional Components: Defined as plain JavaScript functions.


**State:**

Class Components: Can have state managed using the this.state property and setState() method.
Functional Components: Cannot directly have state. However, you can use the useState hook introduced in React 16.8 to add state to functional components.


**Lifecycle Methods:**

Class Components: Support lifecycle methods like componentDidMount, componentDidUpdate, componentWillUnmount, etc.
Functional Components: Prior to React 16.8, functional components did not support lifecycle methods. However, with the introduction of hooks, functional components can now use lifecycle-like functionality with the useEffect hook.


**Use of 'this':**

Class Components: Require the use of this keyword to access props, state, and class methods.
Functional Components: Do not use this. Instead, props and state are passed as arguments to the function.


**Performance:**

Class Components: Slightly less performant due to the overhead of creating class instances and maintaining the this context.
Functional Components: Slightly more performant because they are just functions and do not have the overhead of class instantiation.


Below is the code sample of class and functional components.

```js

import React, { Component } from 'react';

class Greeting extends Component {
  render() {
    return <h1>Hello, {this.props.name}!</h1>;
  }
}

export default Greeting;

```


```js

import React from 'react';

const Greeting = (props) => {
  return <h1>Hello, {props.name}!</h1>;
}

export default Greeting;

```

<hr>