# Pure and Impure Functions


**Pure function:** They do not modify variables outside their scope or modify external state.

```js

// Pure function example
function add(a, b) {
  return a + b;
}

const result = add(3, 5); // Output: 8

```

**Impure function:** They can modify variables outside their scope or modify external state.

```js

// Impure function example
let total = 0;

function addToTotal(number) {
  total += number;
  return total;
}

const result1 = addToTotal(5); // Output: 5
const result2 = addToTotal(3); // Output: 8

```

<hr>
