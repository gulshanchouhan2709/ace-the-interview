# Modules

In JavaScript, modules are reusable pieces of code that encapsulate related functionality, allowing developers to organize their code into separate files or components.

Example:
Suppose you have a module called math.js that contains functions for performing mathematical operations:

```js

// math.js
export function add(a, b) {
    return a + b;
}

export function subtract(a, b) {
    return a - b;
}

```

You can then import and use these functions in another file:

```js

// main.js
import { add, subtract } from './math.js';

console.log(add(5, 3)); // Output: 8
console.log(subtract(10, 4)); // Output: 6

```

<hr>
