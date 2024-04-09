# call, bind and apply


**call:** The call method is used to invoke a function with a specified this value and arguments provided individually.

Syntax: function.call(thisArg, arg1, arg2, ...)

```js

function greet(name) {
    return `Hello, ${name}! I am ${this.role}.`;
}

const person = { role: 'developer' };
console.log(greet.call(person, 'Alice'));

```

**bind:** The bind method creates a new function that, when called, has its this value set to a specific value, with a given sequence of arguments preceding any provided when the new function is called.

Syntax: function.bind(thisArg, arg1, arg2, ...)

```js

function greet(name) {
    return `Hello, ${name}! I am ${this.role}.`;
}

const person = { role: 'developer' };
const boundGreet = greet.bind(person);
console.log(boundGreet('Bob'));

```

**apply:** The apply method is similar to call, but it takes arguments as an array.

Syntax: function.apply(thisArg, [arg1, arg2, ...])

```js

function greet(name, age) {
    return `Hello, ${name}! I am ${this.role} and ${age} years old.`;
}

const person = { role: 'developer' };
console.log(greet.apply(person, ['Alice', 30]));

```

In summary, call and apply are used to invoke a function with a specific this context and arguments, while bind creates a new function with a fixed this context and arguments.

<hr>
