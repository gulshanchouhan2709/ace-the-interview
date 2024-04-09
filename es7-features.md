# ES7 features

- Exponentiation Operator (**)
- Array.prototype.includes()
- Async/Await
- Object.values() 
- String.prototype.trimStart() and String.prototype.trimEnd()


**Exponentiation Operator (**)** The exponentiation operator computes the result of raising the left operand to the power of the right operand.

```js

// ES7
const result = 2 ** 3; // Equivalent to 2 * 2 * 2
console.log(result); // Output: 8


```

**Array.prototype.includes():** The includes() method checks whether an array includes a certain element, returning true or false.

```js

// ES7
const numbers = [1, 2, 3, 4, 5];
console.log(numbers.includes(3)); // Output: true
console.log(numbers.includes(6)); // Output: false

```

**Async/Await:** Async functions and the await keyword provide a more concise syntax for working with asynchronous code, especially Promises.

```js

// ES7
async function fetchData() {
    const response = await fetch('https://api.example.com/data');
    const data = await response.json();
    return data;
}

fetchData().then(data => console.log(data));

```

**Object.values()** Object.values() returns an array of a given object's own enumerable property values.

```js

// ES7
const obj = { a: 1, b: 2, c: 3 };
console.log(Object.values(obj)); // Output: [1, 2, 3]

```

**String.prototype.trimStart() and String.prototype.trimEnd()** These methods remove whitespace from the beginning (trimStart()) or end (trimEnd()) of a string.

```js

// ES7
const str = '   Hello   ';
console.log(str.trimStart()); // Output: 'Hello   '
console.log(str.trimEnd()); // Output: '   Hello'

```

<hr>
