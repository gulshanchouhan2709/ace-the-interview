# Function Currying

Currying is a technique in JavaScript where a function with multiple arguments is transformed into a sequence of nested functions, each taking a single argument.

```js

// Normal function
function add(a, b) {
    return a + b;
}

// Curried function
function curriedAdd(a) {
    return function(b) {
        return a + b;
    };
}

// Using curried function
const add5 = curriedAdd(5); // Fixing 'a' to 5
console.log(add5(3)); // Output: 8 (5 + 3)

```

Example2:

```js

// Normal function
function greet(greeting, name) {
    return `${greeting}, ${name}!`;
}

// Curried function
function curriedGreet(greeting) {
    return function(name) {
        return `${greeting}, ${name}!`;
    };
}

// Using curried function
const greetHello = curriedGreet('Hello'); // Fixing 'greeting' to 'Hello'
console.log(greetHello('Alice')); // Output: Hello, Alice!
console.log(greetHello('Bob')); // Output: Hello, Bob!

const greetGoodMorning = curriedGreet('Good Morning'); // Fixing 'greeting' to 'Good Morning'
console.log(greetGoodMorning('Charlie')); // Output: Good Morning, Charlie!
console.log(greetGoodMorning('Diana')); // Output: Good Morning, Diana!

```

<hr>
