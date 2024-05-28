# Snapshot Testing

Snapshot tests capture the rendered output of a React component. If the component's output changes in future runs, the test will fail, indicating that the output has changed. This helps ensure that UI changes are intentional.


**Step 1: Install Required Packages**

```js

npm install --save-dev jest react-test-renderer

```


**Step 2: Create a React Component**

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


**Step 3: Write a Snapshot Test**

Create a test file for your component. The convention is to place it in the __tests__ directory or next to the component file.

```js

import React from 'react';
import renderer from 'react-test-renderer';
import MyComponent from './MyComponent';

test('MyComponent renders correctly', () => {
  const tree = renderer.create(<MyComponent name="John Doe" age={25} isStudent={true} />).toJSON();
  expect(tree).toMatchSnapshot();
});

```

**Snapshot Update Workflow**

- Initial Snapshot Creation:
    When you run your tests for the first time, a snapshot file is created automatically.

- Snapshot Validation:
    On subsequent runs, Jest will compare the current output of the component with the stored snapshot. If they differ, the test will fail.

- Updating Snapshots:
    If the changes to the component are intentional, you can update the snapshot files by running:

```js

npx jest --updateSnapshot

```

<hr>