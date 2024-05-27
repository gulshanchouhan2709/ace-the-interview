# Defining Props & State Types

In functional components in React with TypeScript, we can define the types of props & state using interfaces or types directly.


below is the simple example of functional component via typescript.


```js

import React from 'react';

// Define the functional component
const MyComponent: React.FC<> = () => {
  return (
    <div>
      <h2>Hello, World!</h2>
    </div>
  );
};

export default MyComponent;

```


Now let's take a look like how we can define a state and props types in typescrpit.


**1. Defining Props Types:**

```js

import React from 'react';

interface MyComponentProps {
  name: string;
  age: number;
  isStudent: boolean;
}

const MyComponent: React.FC<MyComponentProps> = ({ name, age, isStudent }) => {
  return (
    <div>
      <h2>Name: {name}</h2>
      <p>Age: {age}</p>
      <p>Is Student: {isStudent ? 'Yes' : 'No'}</p>
    </div>
  );
};

export default MyComponent;

```

**2. Defining State Types:**

```js

import React, { useState } from 'react';

interface MyComponentState {
  count: number;
  message: string;
}

const MyComponent: React.FC = () => {
  const [state, setState] = useState<MyComponentState>({
    count: 0,
    message: "Hello",
  });

  const { count, message } = state;

  return (
    <div>
      <p>Count: {count}</p>
      <p>Message: {message}</p>
    </div>
  );
};

export default MyComponent;

``` 

<hr>