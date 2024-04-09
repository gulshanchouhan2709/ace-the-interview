# Generator functions

Generator functions in JavaScript are special functions that can pause execution and return intermediate results using the yield keyword. They are defined using the function* syntax.

The `yield` keyword is used within generator functions to pause and resume the execution of the function. When yield is encountered, it pauses the generator function and returns the yielded value.


```js

function* countFrom(start, end) {
    for (let i = start; i <= end; i++) {
        yield i;
    }
}

const generator = countFrom(1, 5);

console.log(generator.next()); // Output: { value: 1, done: false }
console.log(generator.next()); // Output: { value: 2, done: false }
console.log(generator.next()); // Output: { value: 3, done: false }
console.log(generator.next()); // Output: { value: 4, done: false }
console.log(generator.next()); // Output: { value: 5, done: false }
console.log(generator.next()); // Output: { value: undefined, done: true }

```

Another example:

```js

function* iterateArray(arr) {
    for (let i = 0; i < arr.length; i++) {
        yield arr[i];
    }
}

const arr = ['apple', 'banana', 'orange'];
const arrayIterator = iterateArray(arr);

console.log(arrayIterator.next().value); // Output: 'apple'
console.log(arrayIterator.next().value); // Output: 'banana'
console.log(arrayIterator.next().value); // Output: 'orange'
console.log(arrayIterator.next().value); // Output: undefined

```

In summary, Generators allow for lazy evaluation, meaning values are computed only when needed, which can be useful for dealing with large datasets or infinite sequences.

<hr>
