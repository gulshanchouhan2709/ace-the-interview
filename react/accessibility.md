# Accessibility

Accessibility in React.js refers to making your web application usable by as many people as possible, including those with disabilities.


Key practices include using semantic HTML, ARIA attributes, ensuring keyboard navigation, managing focus, maintaining color contrast, providing text alternatives, and making forms accessible.

```js

import React from 'react';

const AccessibleComponent = () => {
  return (
    <div>
      <header>
        <h1>Welcome to My Accessible Site</h1>
      </header>
      <nav>
        <ul>
          <li><a href="#home">Home</a></li>
          <li><a href="#about">About</a></li>
          <li><a href="#contact">Contact</a></li>
        </ul>
      </nav>
      <main>
        <section aria-labelledby="section1-title">
          <h2 id="section1-title">Section 1</h2>
          <p>This is the first section of the page.</p>
        </section>
        <section aria-labelledby="section2-title">
          <h2 id="section2-title">Section 2</h2>
          <p>This is the second section of the page.</p>
        </section>
      </main>
      <footer>
        <p>&copy; 2024 My Accessible Site</p>
      </footer>
    </div>
  );
};

export default AccessibleComponent;


```

```js
import React, { useState } from 'react';

const AccessibleForm = () => {
  const [name, setName] = useState('');
  const [email, setEmail] = useState('');

  const handleSubmit = (e) => {
    e.preventDefault();
    // Handle form submission
  };

  return (
    <form onSubmit={handleSubmit}>
      <div>
        <label htmlFor="name">Name:</label>
        <input
          type="text"
          id="name"
          name="name"
          value={name}
          onChange={(e) => setName(e.target.value)}
          aria-required="true"
        />
      </div>
      <div>
        <label htmlFor="email">Email:</label>
        <input
          type="email"
          id="email"
          name="email"
          value={email}
          onChange={(e) => setEmail(e.target.value)}
          aria-required="true"
        />
      </div>
      <button type="submit">Submit</button>
    </form>
  );
};

export default AccessibleForm;
```

<hr>