# Typescript

In TypeScript, type annotations allow you to explicitly specify the type of a variable, function parameter, return value, or any other entity in your code.

**1. Basic Types**

number: Represents numeric values.

string: Represents textual values.

boolean: Represents true/false values.

null and undefined: Represent absence of value.

any: Represents any type (opt-out of type checking).

void: Used as the return type of functions that do not return a value.


```js

let age: number = 25;
let name: string = "Alice";
let isStudent: boolean = true;
let nothing: void = undefined;

```

**2. Arrays**

You can specify the type of array elements using type[] or Array<type> notation.

```js

let numbers: number[] = [1, 2, 3];
let names: Array<string> = ["Alice", "Bob", "Charlie"];

```

**3. Objects**

You can annotate the types of object properties inline or using interfaces.

```js

let user: { name: string, age: number } = { name: "Bob", age: 30 };

interface Person {
  name: string;
  age: number;
}

let anotherUser: Person = { name: "Alice", age: 25 };


```

**4. Functions**

You can annotate function parameters and return types.

```js

function add(a: number, b: number): number {
  return a + b;
}

function add(a: number, b: number): void {
  console.log(a + b);
}

const add = (a: number, b: number): number => {
  return a + b;
}

const add = (a: number, b: number): void => {
  console.log(a + b);
}

```

**5. Type Aliases**

You can annotate function parameters and return types.

```js

type StringOrNumber = string | number;

let value: StringOrNumber;
value = "Hello"; // OK
value = 123;      // OK

```

**6. Enums**

Enums allow you to define a set of named constants.

```js

enum Direction {
  Up,
  Down,
  Left,
  Right
}

let direction: Direction = Direction.Up;

```

<hr>