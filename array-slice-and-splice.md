# Array Slice and Splice method


**Slice:** This method returns a shallow copy of a portion of an array into a new array object. It does not modify the original array.


```js

const fruits = ['apple', 'banana', 'cherry', 'date', 'elderberry'];

// Extract a portion of the array from index 1 to 3 (not including 3)
const slicedFruits = fruits.slice(1, 3);

console.log(slicedFruits); // Output: ['banana', 'cherry']
console.log(fruits); // Original array is unchanged: ['apple', 'banana', 'cherry', 'date', 'elderberry']

```

**Splice:** This method changes the contents of an array by removing or replacing existing elements and/or adding new elements in place.

```js

const months = ['January', 'February', 'April', 'May'];

// Remove 'April' from index 2 and insert 'March'
months.splice(2, 1, 'March');

console.log(months); // Output: ['January', 'February', 'March', 'May']


```

<hr>
