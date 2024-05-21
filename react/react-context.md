# React Context

React Context provides a way to pass data through the component tree without having to pass props down manually at every level. It's particularly useful for passing down global data that needs to be accessible by many components in an application, such as themes, user authentication status, or language preferences.

```js

// ThemeContext.js
import React, { createContext, useState } from 'react';

// Create the context
const ThemeContext = createContext();

// Create a provider component
const ThemeProvider = ({ children }) => {
  const [theme, setTheme] = useState('light');

  const toggleTheme = () => {
    setTheme(prevTheme => (prevTheme === 'light' ? 'dark' : 'light'));
  };

  return (
    <ThemeContext.Provider value={{ theme, toggleTheme }}>
      {children}
    </ThemeContext.Provider>
  );
};

export { ThemeProvider, ThemeContext };

```

```js

// App.js
import React from 'react';
import { ThemeProvider } from './ThemeContext';
import Header from './Header';
import MainContent from './MainContent';

function App() {
  return (
    <ThemeProvider>
      <div>
        <Header />
        <MainContent />
      </div>
    </ThemeProvider>
  );
}

export default App;

```

```js

// Header.js
import React, { useContext } from 'react';
import { ThemeContext } from './ThemeContext';

function Header() {
  const { theme, toggleTheme } = useContext(ThemeContext);

  return (
    <header style={{ background: theme === 'light' ? '#f0f0f0' : '#333', padding: '20px' }}>
      <h1>My App</h1>
      <button onClick={toggleTheme}>Toggle Theme</button>
    </header>
  );
}

export default Header;

```

<hr>