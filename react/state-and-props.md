# State and Props

In ReactJS, components go through various stages in their lifecycle, from initialization to destruction.


**State:** State is a JavaScript object that represents the dynamic data managed by a component.

```js

class Counter extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      count: 0
    };
  }

  incrementCount() {
    this.setState({ count: this.state.count + 1 });
  }

  render() {
    return (
      <div>
        <p>Count: {this.state.count}</p>
        <button onClick={() => this.incrementCount()}>Increment</button>
      </div>
    );
  }
}


```

**Props:** are used to pass data from a parent component to a child component and Props are immutable, meaning they cannot be changed by the component that receives them. They are read-only.

```js

function Greeting(props) {
  return <h1>Hello, {props.name}!</h1>;
}

const App = () => {
  return <Greeting name="John" />;
}

```

State vs. Props:
	State:
		Used for managing dynamic data within a component.
		Controlled and updated internally by the component.


	Props:
		Used for passing data from parent components to child components.
		Read-only for the child component.

<hr>