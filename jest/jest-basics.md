# JEST

Jest is a JavaScript testing framework developed by Facebook. It's often used for testing React applications, but it can be used with any JavaScript project. Jest is known for its ease of use, built-in assertions, and features like snapshot testing and code coverage.


**Install Jest in a project**

```js

npm install --save-dev jest

OR 

yarn add --dev jest

```

Now we can run Jest tests by adding a script to your package.json

```js

"scripts": {
  "test": "jest"
}

```

and then run

```js

npm test 

OR 

yarn test

```

**How do we write a simple test case in Jest**

```js

// sum.js
function sum(a, b) {
  return a + b;
}
module.exports = sum;

// sum.test.js
const sum = require('./sum');

test('adds 1 + 2 to equal 3', () => {
  expect(sum(1, 2)).toBe(3);
});

```

Advantages

- Perform snapshot testing but Jest lacks full support for ECMAScript Modules (ESM)

<hr>