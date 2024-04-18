# First Order and First Class Functions


**First Order Function:** Regular JavaScript functions are considered as a first-order functions.

A first-order function is a function that doesn't accept other functions as arguments or return functions as its result.


```js

function add(a, b) {
    return a + b;
}

// In the add function, a and b are regular parameters, not functions.

```

**First Class Function:**

- If function is assigned to variables like arrow function so it's known as first class function.
- If function is passed as an arguments to other functions or returned from other functions is known as First class function.


Assigning functions to variables:

```js

const greet = function(name) {
    console.log(`Hello, ${name}!`);
};

greet('John'); // Output: Hello, John!

```

Passing functions as arguments:

```js

function operate(num1, num2, operation) {
    return operation(num1, num2);
}

function add(a, b) {
    return a + b;
}

operate(5, 3, add); // Output: 8

```

Returning functions from other functions:

```js

function createMultiplier(factor) {
    return function(number) {
        return number * factor;
    };
}

const double = createMultiplier(2);
console.log(double(5)); // Output: 10

```

<hr>
