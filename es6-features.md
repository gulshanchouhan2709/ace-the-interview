# ES6 features

- Arrow Functions
- let and const
- Template Literals
- Destructuring Assignment
- Spread and Rest Operators
- Modules
- Default parameter


**Arrow Functions:** Arrow functions provide a more concise syntax for writing anonymous functions.

```js

// ES5
function add(a, b) {
    return a + b;
}

// ES6 (Arrow Function)
const add = (a, b) => a + b;

```

```js

// Normal function as a constructor
function NormalConstructor() {
  this.value = 10;
}
const normalInstance = new NormalConstructor();
console.log(normalInstance.value); // Output: 10

```

- Arrow functions do not have their own arguments object, while normal functions do.
- Arrow functions cannot be used as constructors, while normal functions can.
- Arrow function implicitly return values if the body consists of a single expression, while normal functions require explicit return statements.


**let and const:** let and const allow block-scoped variable declarations, improving variable scoping in JavaScript.

```js

// ES5
var x = 10;
if (true) {
    var x = 20;
}
console.log(x); // Output: 20

// ES6 (let and const)
let y = 10;
if (true) {
    let y = 20;
}
console.log(y); // Output: 10

```

**Template Literals:** Template literals provide an easy way to create multi-line strings and interpolate variables.

```js

// ES5
var name = 'Alice';
console.log('Hello, ' + name + '!');

// ES6 (Template Literals)
const name = 'Alice';
console.log(`Hello, ${name}!`);

```

**Destructuring Assignment:** Destructuring assignment allows for extracting values from arrays or objects and assigning them to variables.

Object Destructuring

```js
// ES5
var person = { name: 'Bob', age: 30 };
var name = person.name;
var age = person.age;

// ES6 (Destructuring Assignment)
const person = { name: 'Bob', age: 30 };
const { name, age } = person;

```

Array Destructuring

```js
const numbers = [1, 2, 3, 4, 5];
const [first, second, ...rest] = numbers;

console.log(first); // Output: 1
console.log(second); // Output: 2
console.log(rest); // Output: [3, 4, 5]
```

Swap variable (Via Array Destructuring)

```js
let a = 1;
let b = 2;

[a, b] = [b, a];

console.log(a); // Output: 2
console.log(b); // Output: 1
```


**Spread and Rest Operators:** The spread operator (...) allows for expanding arrays or objects, while the rest parameter syntax also uses ... to represent an indefinite number of arguments as an array.

```js

// Spread Operator
const numbers = [1, 2, 3];
const newNumbers = [...numbers, 4, 5];

// Rest Parameter
const sum = (...args) => args.reduce((acc, val) => acc + val, 0);
console.log(sum(1, 2, 3)); // Output: 6

```

**Default Parameters:** Default parameters allow you to specify default values for function parameters.

```js

// ES5
function greet(name) {
    name = name || 'Guest';
    console.log(`Hello, ${name}!`);
}

greet(); // Output: Hello, Guest!

// ES6 (Default Parameters)
const greet = (name = 'Guest') => {
    console.log(`Hello, ${name}!`);
};

greet(); // Output: Hello, Guest!

```

**Modules:** ES6 introduced a module system for JavaScript, allowing for better code organization and encapsulation.

```js

// ES6 Module Syntax (export)
export const add = (a, b) => a + b;

// ES6 Module Syntax (import)
import { add } from './math';
console.log(add(2, 3)); // Output: 5

```

<hr>
