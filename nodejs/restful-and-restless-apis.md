# RestFull & Restless APIs


**RestFul APIs:** RESTful API uses multiple endpoints and standard HTTP methods and URL structure.


```js

// GET all users
app.get('/users', (req, res) => {
  res.json(users);
});

// GET a single user by ID
app.get('/users/:id', (req, res) => {
  const user = users.find(u => u.id === parseInt(req.params.id));
  if (!user) return res.status(404).send('User not found');
  res.json(user);
});

// POST a new user
app.post('/users', (req, res) => {
  const newUser = {
    id: users.length + 1,
    name: req.body.name,
    email: req.body.email
  };
  users.push(newUser);
  res.status(201).json(newUser);
});

// PUT (update) a user by ID
app.put('/users/:id', (req, res) => {
  const user = users.find(u => u.id === parseInt(req.params.id));
  if (!user) return res.status(404).send('User not found');
  
  user.name = req.body.name;
  user.email = req.body.email;
  res.json(user);
});

// DELETE a user by ID
app.delete('/users/:id', (req, res) => {
  const userIndex = users.findIndex(u => u.id === parseInt(req.params.id));
  if (userIndex === -1) return res.status(404).send('User not found');
  
  users.splice(userIndex, 1);
  res.status(204).send();
});

```

**RESTless APIs:** RESTless API uses custom routes and methods that don't strictly follow REST principles.

```js

// Custom route to get user by email
app.post('/getUserByEmail', (req, res) => {
  const user = users.find(u => u.email === req.body.email);
  if (!user) return res.status(404).send('User not found');
  res.json(user);
});

// Custom route to update user email by ID
app.post('/updateUserEmail', (req, res) => {
  const user = users.find(u => u.id === req.body.id);
  if (!user) return res.status(404).send('User not found');
  
  user.email = req.body.email;
  res.json(user);
});

// Custom route to delete user by email
app.post('/deleteUserByEmail', (req, res) => {
  const userIndex = users.findIndex(u => u.email === req.body.email);
  if (userIndex === -1) return res.status(404).send('User not found');
  
  users.splice(userIndex, 1);
  res.status(204).send();
});

```

<hr>
