# Prototype

When we are creating any object or array or function then javascript engine will automatically add some predifined property and methods into it, which is called its prototype.

So if we are trying to access a property of an object: if the property can't be found in the object itself, the prototype is searched for the property. If the property still can't be found, then the prototype's prototype is searched, and so on until either the property is found, or the end of the chain is reached, in which case undefined is returned.

Let's see the below example images to make it more understandable.


![Prototype Example1](/assets/prototype1.png)


![Prototype Example2](/assets/prototype2.png)


![Prototype Example3](/assets/prototype3.png)

In the above scenario, we are attempting to assign the object as the prototype of object2 using object2.__proto__ = object. However, this approach is no longer recommended. 

![Prototype Example4](/assets/prototype4.png)


"In the above image, we have created objects named arr, object and fun. When accessing their properties and methods, we use the dot notation (.). These properties and methods are internally added by the JavaScript engine."

If we want to view those properties and methods, we can write:

- `arr.__proto__`
 - It returns the array prototype, which can also be accessed via arr.__proto__.__proto__. This will return the object prototype, which in turn has another prototype accessible via arr.__proto__.__proto__.__proto__. Eventually, this chain ends with a return value of null. This process is known as 'Prototype Chaining'.


- `object.__proto__`
 - It returns the object prototype, which also has its own prototype accessible via object.__proto__.__proto__. Eventually, this chain ends with a return value of null.


- `fun.__proto__` 
 - It returns the function prototype, which also has its own prototype accessible via fun.__proto__.__proto__. This will return the function prototype, which in turn has another prototype accessible via fun.__proto__.__proto__.__proto__. Eventually, this chain ends with a return value of null.

```js
arr.__proto__ === Array.prototype // true
arr.__proto__.__proto__ === Object.prototype // true
arr.__proto__.__proto__.__proto__ === null // true

object.__proto__ === Object.prototype // true
object.__proto__.__proto__ === null // true

fun.__proto__ === Function.prototype // true
fun.__proto__.__proto__ === Object.prototype // true
fun.__proto__.__proto__.__proto__ === null // true
```


Here's a another simple example in JavaScript to demonstrate the use of prototypes:

```js
// Constructor function for creating Person objects
function Person(name, age) {
  this.name = name;
  this.age = age;
}

// Adding a method to the prototype of Person objects
Person.prototype.introduce = function() {
  return `Hello, my name is ${this.name} and I am ${this.age} years old.`;
};

// Creating a new Person object
let person1 = new Person('Alice', 30);

// Calling the introduce method on the person1 object
console.log(person1.introduce()); // Output: Hello, my name is Alice and I am 30 years old.
```

In the above example:

- We define a constructor function Person to create Person objects with name and age properties.
- We add a method introduce to the prototype of Person objects using Person.prototype. This method returns a greeting message.
- We create a new Person object person1 with the name "Alice" and age 30 using the new keyword.
- We call the introduce method on the person1 object, which accesses the method from its prototype and returns the greeting message.


Note - We can add prototype method or value to `Number`, `Object`, `Function`, `Array` etc. See it below

```js
Number.prototype.getNo = function() { return; } // Using this, we can access `getNo` function into any number prototypes.
Function.prototype.getFunc = function() { return; } // Using this, we can access `getFunc` function into any function prototypes.
Object.prototype.getObj = function() { return; } // Using this, we can access `getObj` function into any object prototypes.
```
<hr>