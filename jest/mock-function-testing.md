# Mock function & Testing

Mock Testing is a technique where you create fake (mock) versions of functions or modules to test your code in isolation. It allows you to simulate the behavior of real functions or modules without relying on their actual implementation.


**Code Sample**


**Step 1: Create a Module**
First, create a simple module with a function that depends on another function:

```js

// math.js
export const add = (a, b) => a + b;

```

Next, create another module that uses this function:

```js

// calculator.js
import { add } from './math';

export const calculate = (a, b) => {
  return add(a, b);
};

```

**Step 2: Write a Test using Mock Functions**
Now, write a test for the calculate function, mocking the add function:

```js

// calculator.test.js
import { calculate } from './calculator';
import * as math from './math';

jest.mock('./math'); // Automatically mocks the entire module

test('calculate uses add function', () => {
  // Mock the add function
  math.add.mockImplementation((a, b) => a + b);

  const result = calculate(3, 2);

  // Verify the mocked function was called
  expect(math.add).toHaveBeenCalledWith(3, 2);

  // Check the result of the calculate function
  expect(result).toBe(5); // 3 + 2 = 5
});

```

Explanation

jest.mock('./math'): Jest automatically mocks all exports from the math module.

Mock Implementation: mockImplementation is used to define the behavior of the mocked add function.

Assertions: expect is used to verify that the mocked add function was called correctly and that the calculate function returns the expected result.


<hr>