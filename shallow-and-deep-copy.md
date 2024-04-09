# shallow and deep copy

In JavaScript, when you copy an object or an array, you can create either a shallow copy or a deep copy, depending on whether nested objects or arrays are also copied.

**Shallow Copy:** A shallow copy creates a new object or array, but it only copies the references of nested objects or arrays, not the nested objects or arrays themselves.

We can use `Object.assign({}, object)` and `Spread Operator (...object)` to make a shallow copy.

```js

// Shallow copy of an array
const originalArray = [1, 2, { a: 3 }];
const shallowCopyArray = [...originalArray];

originalArray[2].a = 4;
console.log(shallowCopyArray[2].a); // Output: 4 (both arrays share the same reference to the nested object)

```

**Deep Copy:** A deep copy creates a completely new object or array with its own copies of all nested objects or arrays.

We can use `JSON.parse(JSON.stringify(object))` and `const _ = require('lodash'); _.cloneDeep(object)` to make a deep copy.

```js

// Deep copy of an array
const originalArray = [1, 2, { a: 3 }];
const deepCopyArray = JSON.parse(JSON.stringify(originalArray));

originalArray[2].a = 4;
console.log(deepCopyArray[2].a); // Output: 3 (the nested object in the deep copy remains unchanged)

```

In summary, In the shallow copy example, changes to the nested object in the original array also affect the nested object in the shallow copy. However, in the deep copy example, changes to the nested object in the original array do not affect the nested object in the deep copy because it's an entirely separate object.

<hr>
