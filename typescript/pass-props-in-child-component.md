# Pass props to a child component in React with TypeScript

Passing props to a child component in React with TypeScript involves defining the type of the props using an interface or type alias and then using those props in the child component. Here’s a step-by-step guide with examples:

**1. Step 1: Define the Props Type**

```js

// Define the type of props using an interface
interface ChildComponentProps {
  name: string;
  age: number;
  isStudent: boolean;
}

```


**Step 2: Define the Child Component**

```js

import React from 'react';

// Child component
const ChildComponent: React.FC<ChildComponentProps> = ({ name, age, isStudent }) => {
  return (
    <div>
      <h2>Name: {name}</h2>
      <p>Age: {age}</p>
      <p>Is Student: {isStudent ? 'Yes' : 'No'}</p>
    </div>
  );
};

export default ChildComponent;

```

**Step 3: Use the Child Component in a Parent Component**

```js

import React from 'react';
import ChildComponent from './ChildComponent';

// Parent component
const ParentComponent: React.FC = () => {
  return (
    <div>
      <h1>Parent Component</h1>
      <ChildComponent name="Alice" age={30} isStudent={true} />
    </div>
  );
};

export default ParentComponent;

``` 

<hr>