# High Order Components

A Higher-Order Component (HOC) in React is a function that takes a component as an argument and returns a new component with additional props or functionality. HOCs are used to share common functionality between components, enabling code reusability.


**Use Case: Authentication**

A common use case for an HOC is handling authentication. You might have multiple components in your application that should only be accessible to authenticated users. Instead of duplicating the authentication logic in each component, you can create an HOC that wraps the components and handles the authentication logic.

**Step 1: Create an HOC for Authentication**

```js

// withAuth.js
import React from 'react';
import { Redirect } from 'react-router-dom';

const withAuth = (WrappedComponent) => {
  return (props) => {
    const isAuthenticated = localStorage.getItem('isAuthenticated');

    if (isAuthenticated) {
      return <WrappedComponent {...props} />;
    } else {
      return <Redirect to="/login" />;
    }
  };
};

export default withAuth;

```

**Step 2: Wrap the Component with the HOC**

```js

// App.js
import React from 'react';
import { BrowserRouter as Router, Route, Routes } from 'react-router-dom';
import Dashboard from './Dashboard';
import Login from './Login';
import withAuth from './withAuth';

const ProtectedDashboard = withAuth(Dashboard);

const App = () => (
  <Router>
    <Routes>
      <Route path="/login" element={<Login />} />
      <Route path="/dashboard" element={<ProtectedDashboard />} />
    </Routes>
  </Router>
);

export default App;

```

<hr>