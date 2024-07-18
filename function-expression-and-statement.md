# Function Expression VS Function Statement


**Function Statement/ Function Declaration:** It's defines a function with the specified parameters and it's hoisted.


```js

function functionName(parameters) {
  // function body
}

```

**Function Expression:** It can be anonymous or named, and are typically assigned to a variable..

```js

// This will result in an error because function expressions are not hoisted
// greet();

const greet = function() {
  console.log('Hi there!');
};

// This is valid
greet();


```

<hr>
