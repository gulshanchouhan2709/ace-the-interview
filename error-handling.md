# Error handling

**Synchronous Error Handling:** Synchronous errors occur during the execution of regular JavaScript code. They can be caught using try...catch blocks.


```js

try {
    // Code that may throw an error
    throw new Error('Synchronous error occurred');
} catch (error) {
    // Handle the error
    console.error('Caught synchronous error:', error.message);
}

```

**Asynchronous Error Handling (Promises):** Errors in asynchronous code, such as promises, can be handled using .catch() method or try...catch blocks inside an async function.


```js

async function fetchData() {
    try {
        const data = await fetch('https://example.com/data');
        const jsonData = await data.json();
        console.log('Data:', jsonData);
    } catch (error) {
        console.error('Error fetching data:', error.message);
    }
}

```

**Asynchronous Error Handling (Callbacks):**  Error handling in asynchronous code using callbacks involves passing an error object as the first argument to the callback function.


```js

function readFile(path, callback) {
    // Asynchronous file reading
    if (errorCondition) {
        callback(new Error('Error reading file'));
    } else {
        callback(null, fileContent);
    }
}

readFile('example.txt', (error, data) => {
    if (error) {
        console.error('Error reading file:', error.message);
    } else {
        console.log('File content:', data);
    }
});

```

**Event Emitter Error Handling:**  In Node.js, error events emitted by an event emitter can be handled using the error event listener.


```js

const EventEmitter = require('events');

const emitter = new EventEmitter();

emitter.on('error', (error) => {
    console.error('Error occurred:', error.message);
});

emitter.emit('error', new Error('Custom error'));

```

In summary, error handling in JavaScript involves using try...catch blocks for synchronous code, .catch() method or try...catch blocks inside async functions for promises, passing error objects to callback functions for asynchronous callbacks, and listening for error events emitted by event emitters.

<hr>
