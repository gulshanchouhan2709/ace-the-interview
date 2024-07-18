# Authentication & Authorization

Authentication and authorization are two fundamental concepts in the security domain


**Authentication:** Authentication is the process of verifying the identity of a user. It ensures that the requesting access user is valid or not.

Example:
Login process where a user provides credentials (username and password) which are then verified by the system.

```js

const express = require('express');
const jwt = require('jsonwebtoken');
const app = express();

app.use(express.json());

const users = [
  { id: 1, username: 'user1', password: 'pass1' },
  { id: 2, username: 'user2', password: 'pass2' }
];

app.post('/login', (req, res) => {
  const { username, password } = req.body;
  const user = users.find(u => u.username === username && u.password === password);
  
  if (user) {
    const token = jwt.sign({ id: user.id }, 'your_jwt_secret');
    res.json({ token });
  } else {
    res.status(401).send('Invalid credentials');
  }
});

app.listen(3000, () => console.log('Server running on port 3000'));

```

**Authorization:** Authorization is the process of determining whether an authenticated user has permission to access a specific resource or perform a specific action.

```js

const express = require('express');
const jwt = require('jsonwebtoken');
const app = express();

app.use(express.json());

const users = [
  { id: 1, username: 'user1', password: 'pass1', role: 'user' },
  { id: 2, username: 'user2', password: 'pass2', role: 'admin' }
];

const authenticateToken = (req, res, next) => {
  const token = req.headers['authorization'];
  if (!token) return res.sendStatus(401);

  jwt.verify(token, 'your_jwt_secret', (err, user) => {
    if (err) return res.sendStatus(403);
    req.user = user;
    next();
  });
};

const authorizeRole = (role) => {
  return (req, res, next) => {
    if (req.user.role !== role) {
      return res.sendStatus(403);
    }
    next();
  };
};

app.post('/login', (req, res) => {
  const { username, password } = req.body;
  const user = users.find(u => u.username === username && u.password === password);
  
  if (user) {
    const token = jwt.sign({ id: user.id, role: user.role }, 'your_jwt_secret');
    res.json({ token });
  } else {
    res.status(401).send('Invalid credentials');
  }
});

app.get('/admin', authenticateToken, authorizeRole('admin'), (req, res) => {
  res.send('Welcome, admin!');
});

app.listen(3000, () => console.log('Server running on port 3000'));

```

<hr>
