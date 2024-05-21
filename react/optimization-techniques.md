# Optimization Techniques (ReactJS)

Here are some necessary optimization techniques for React.js

**Use React.memo for Functional Components:**

React.memo is a higher-order component that memoizes the result, preventing unnecessary re-renders when the props haven't changed.

```js

const MyComponent = React.memo((props) => {
  return <div>{props.value}</div>;
});

```

**Implement shouldComponentUpdate in Class Components:**

For class components, implement the shouldComponentUpdate lifecycle method to prevent unnecessary re-renders.

```js

class MyComponent extends React.Component {
  shouldComponentUpdate(nextProps, nextState) {
    // Only update if the props or state have changed
    return nextProps.value !== this.props.value || nextState.someState !== this.state.someState;
  }

  render() {
    return <div>{this.props.value}</div>;
  }
}

```

**Use useMemo and useCallback Hooks**

useMemo: Memoize expensive calculations to avoid recalculating them on every render.
useCallback: Memoize functions to prevent them from being recreated on every render.

```js

const MyComponent = ({ items }) => {
  const expensiveCalculation = useMemo(() => {
    return items.reduce((acc, item) => acc + item.value, 0);
  }, [items]);

  const handleClick = useCallback(() => {
    console.log('Button clicked');
  }, []);

  return (
    <div>
      <p>{expensiveCalculation}</p>
      <button onClick={handleClick}>Click me</button>
    </div>
  );
};

```

**Lazy Loading with React.lazy and Suspense**

Split your code into smaller chunks and load them on demand using React.lazy and Suspense.

```js

import React, { Suspense } from 'react';

const LazyComponent = React.lazy(() => import('./LazyComponent'));

const App = () => (
  <Suspense fallback={<div>Loading...</div>}>
    <LazyComponent />
  </Suspense>
);

```

**Optimize Component Mounting and Unmounting Event Listener**

Clean up side effects: Use useEffect cleanup functions to clean up side effects.
Remove listeners: Ensure event listeners and subscriptions are removed when components unmount.

```js

useEffect(() => {
  const handleScroll = () => {
    console.log('scrolling');
  };
  window.addEventListener('scroll', handleScroll);

  return () => {
    window.removeEventListener('scroll', handleScroll);
  };
}, []);

```

**Avoid Inline Styles and Use CSS-in-JS Libraries**

Inline styles can cause unnecessary re-renders. Use CSS-in-JS libraries like styled-components or emotion to optimize styling.

```js

import styled from 'styled-components';

const Button = styled.button`
  background: palevioletred;
  color: white;
  font-size: 1em;
  margin: 1em;
  padding: 0.25em 1em;
  border: 2px solid palevioletred;
  border-radius: 3px;
`;

const MyComponent = () => <Button>Click me</Button>;

```

<hr>