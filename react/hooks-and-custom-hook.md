# Refs & ForwardRef

Refs provide a way to directly access and interact with DOM nodes of html elements

```js

import React, { useRef } from 'react';

function TextInputWithFocusButton() {
  const inputRef = useRef(null);

  const handleClick = () => {
    inputRef.current.focus();
  };

  return (
    <div>
      <input type="text" ref={inputRef} />
      <button onClick={handleClick}>Focus the input</button>
    </div>
  );
}

export default TextInputWithFocusButton;


```

**forwardRef:**

forwardRef is a function that allows a parent component to pass a ref to a child component.

```js

import React, { forwardRef, useRef } from 'react';

// A simple button component that forwards its ref to the button element
const FancyButton = forwardRef((props, ref) => (
  <button ref={ref} className="fancy-button">
    {props.children}
  </button>
));

function App() {
  const buttonRef = useRef(null);

  const handleClick = () => {
    alert('Button clicked!');
  };

  return (
    <div>
      <FancyButton ref={buttonRef} onClick={handleClick}>
        Click me!
      </FancyButton>
    </div>
  );
}

export default App;

```


<hr>