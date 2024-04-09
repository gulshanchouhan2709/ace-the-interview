# Call by Value and Call by Reference

In JavaScript, primitive data types like numbers, strings, and booleans are passed to functions by value, while objects (including arrays and functions) are passed by reference.

**Call by Value:** When a primitive data type is passed to a function, a copy of the value is created, and changes made to the parameter inside the function do not affect the original value outside the function.

```js
function changeValue(x) {
    x = 10; // This changes the value of 'x' inside the function
}

let num = 5;
changeValue(num);
console.log(num); // Output: 5 (original value remains unchanged)
```

**Call by Reference:** When an object is passed to a function, a reference to the object is passed, not a copy of the object itself. This means changes made to the object inside the function will affect the original object outside the function.

```js
function changeObject(obj) {
    obj.property = 'new value'; // This changes the object's property inside the function
}

let obj = { property: 'old value' };
changeObject(obj);
console.log(obj.property); // Output: 'new value' (original object is modified)
```

<hr>
