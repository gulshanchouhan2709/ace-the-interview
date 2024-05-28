# React Router

React Router is a library for React that allows you to handle the navigation between different components, or "pages" in the React application, making it possible to build single-page applications (SPAs) that can dynamically update the UI without needing a full page refresh.

Below is the Simple Example:-

```js

// App.js
import React from 'react';
import { BrowserRouter as Router, Route, Routes } from 'react-router-dom';
import Home from './Home';
import About from './About';

const App = () => (
  <Router>
    <Routes>
      <Route path="/" element={<Home />} />
      <Route path="/about" element={<About />} />
    </Routes>
  </Router>
);

export default App;

```

In React Router, `BrowserRouter`, `HashRouter`, and `MemoryRouter` are different routing components that handle navigation in different ways.

BrowserRouter

BrowserRouter uses the HTML5 history API (pushState, replaceState, and the popstate event) to keep the UI in sync with the URL. This is the most common router used in web applications.


HashRouter

The URL will include a # character followed by the actual path. This approach is useful when you need to support older browsers or environments that do not support the HTML5 history API.


MemoryRouter

It's keeps the history of the "URL" in memory

<hr>