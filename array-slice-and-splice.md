# Array Slice and Splice method


**Slice:** If we want to get a portion of the array from specific indexing so we can use "Slice" method and it does not modify the original array.


```js

const fruits = ['apple', 'banana', 'cherry', 'date', 'elderberry'];

// Extract a portion of the array from index 1 to 3 (not including 3)
const slicedFruits = fruits.slice(1, 3);

console.log(slicedFruits); // Output: ['banana', 'cherry']
console.log(fruits); // Original array is unchanged: ['apple', 'banana', 'cherry', 'date', 'elderberry']

```

**Splice:** This method is used to  removing or replacing existing elements and/or adding new elements in place.

```js

const months = ['January', 'February', 'April', 'May'];

// Remove 'April' from index 2 and insert 'March'
months.splice(2, 1, 'March');

console.log(months); // Output: ['January', 'February', 'March', 'May']


```

<hr>
