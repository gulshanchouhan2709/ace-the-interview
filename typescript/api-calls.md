# API Calling with TypeScript

Handling asynchronous operations like API calls in a React component with TypeScript involves using React hooks, such as useEffect for side effects and useState for managing state. TypeScript adds type safety to these operations, ensuring the data fetched and managed is correctly typed.

**Define the Data Type:**

```js

interface User {
  id: number;
  name: string;
  username: string;
  email: string;
}

```


**Step 2: Define the Child Component**

```js

import React, { useEffect, useState } from 'react';
import axios from 'axios';

const UserList: React.FC = () => {
  const [users, setUsers] = useState<User[]>([]);
  const [loading, setLoading] = useState<boolean>(true);
  const [error, setError] = useState<string | null>(null);

  useEffect(() => {
    const fetchUsers = async () => {
      try {
        const response = await axios.get<User[]>('https://jsonplaceholder.typicode.com/users');
        setUsers(response.data);
      } catch (error) {
        setError('Failed to fetch users');
      } finally {
        setLoading(false);
      }
    };

    fetchUsers();
  }, []);

  if (loading) return <p>Loading...</p>;
  if (error) return <p>{error}</p>;

  return (
    <div>
      <h1>User List</h1>
      <ul>
        {users.map(user => (
          <li key={user.id}>{user.name} - {user.email}</li>
        ))}
      </ul>
    </div>
  );
};

export default UserList;

```

Additional Tips:-

  TypeScript Generics: When using axios or fetch, you can use TypeScript generics to type the response data.
  Error Handling: Ensure proper error handling, especially when dealing with network requests.
  Cleanup: If necessary, clean up any asynchronous operations in useEffect to avoid memory leaks.

<hr>