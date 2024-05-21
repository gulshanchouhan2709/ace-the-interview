# Controlled & Uncontrolled Components

In controlled components, the form data is handled by the state within the React component. This means the value of the form element is controlled by the React state, and any changes to the form element are handled via event handlers that update the state.


```js

import React, { useState } from 'react';

function ControlledForm() {
  const [name, setName] = useState('');

  const handleChange = (event) => {
    setName(event.target.value);
  };

  const handleSubmit = (event) => {
    event.preventDefault();
    alert(`Name submitted: ${name}`);
  };

  return (
    <form onSubmit={handleSubmit}>
      <label>
        Name:
        <input type="text" value={name} onChange={handleChange} />
      </label>
      <button type="submit">Submit</button>
    </form>
  );
}

export default ControlledForm;


```

**Uncontrolled components:**

In uncontrolled components, form data is handled by the DOM itself. React does not manage the value of the form element directly. Instead, you can access the form values using refs

```js

import React, { useRef } from 'react';

function UncontrolledForm() {
  const nameRef = useRef(null);

  const handleSubmit = (event) => {
    event.preventDefault();
    alert(`Name submitted: ${nameRef.current.value}`);
  };

  return (
    <form onSubmit={handleSubmit}>
      <label>
        Name:
        <input type="text" ref={nameRef} />
      </label>
      <button type="submit">Submit</button>
    </form>
  );
}

export default UncontrolledForm;

```


<hr>