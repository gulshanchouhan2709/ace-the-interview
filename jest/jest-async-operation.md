# JEST (Asynchronous operation)

There are several ways to test asynchronous code in Jest, such as using callbacks, promises, or async/await.


**Using Promises:**

```js

test('fetches data successfully', () => {
  return fetchData().then(data => {
    expect(data).toBe('some data');
  });
});

```

**Using async/await:**

```js

test('fetches data successfully', async () => {
  const data = await fetchData();
  expect(data).toBe('some data');
});

```

<hr>