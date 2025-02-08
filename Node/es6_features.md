ES6, or ECMAScript 2015, introduced several new features and improvements to JavaScript. Below is an overview of key ES6 features:

---

## **1. Block-Scoped Declarations: `let` and `const`**
- **`let`**: Declares variables that are block-scoped and can be reassigned.
- **`const`**: Declares variables that are block-scoped and immutable (though objects and arrays can have their properties updated).

Example:
```javascript
let x = 10;
if (true) {
  let x = 20; // Different scope
  console.log(x); // 20
}
console.log(x); // 10

const y = 30;
// y = 40; // Error: Assignment to constant variable
```

---

## **2. Arrow Functions**
- Shorter syntax for defining functions.
- Lexical `this` binding (no re-binding of `this`).

Example:
```javascript
const add = (a, b) => a + b;
console.log(add(2, 3)); // 5
```

---

## **3. Template Literals**
- Strings enclosed by backticks (`` ` ``) that support interpolation and multiline strings.

Example:
```javascript
const name = "John";
console.log(`Hello, ${name}!`); // Hello, John!
```

---

## **4. Default Parameters**
- Function parameters can have default values.

Example:
```javascript
function greet(name = "Guest") {
  return `Hello, ${name}!`;
}
console.log(greet()); // Hello, Guest!
```

---

## **5. Destructuring Assignment**
- Extract values from arrays or objects and assign them to variables.

Example:
```javascript
// Arrays
const [a, b] = [1, 2];
console.log(a, b); // 1 2

// Objects
const person = { name: "Alice", age: 25 };
const { name, age } = person;
console.log(name, age); // Alice 25
```

---

## **6. Spread and Rest Operators**
- **Spread (`...`)**: Expands elements of an array or object.
- **Rest (`...`)**: Gathers remaining elements into an array.

Example:
```javascript
// Spread
const arr1 = [1, 2];
const arr2 = [...arr1, 3, 4];
console.log(arr2); // [1, 2, 3, 4]

// Rest
function sum(...nums) {
  return nums.reduce((total, n) => total + n, 0);
}
console.log(sum(1, 2, 3)); // 6
```

---

## **7. Enhanced Object Literals**
- Shorthand for defining properties and methods in objects.

Example:
```javascript
const x = 10, y = 20;
const obj = { x, y, greet() { return "Hello!"; } };
console.log(obj); // { x: 10, y: 20, greet: [Function: greet] }
```

---

## **8. Promises**
- Native support for asynchronous programming.

Example:
```javascript
const fetchData = () => new Promise((resolve, reject) => {
  setTimeout(() => resolve("Data fetched"), 1000);
});
fetchData().then(data => console.log(data)); // Data fetched
```

---

## **9. Classes**
- A cleaner syntax for creating objects and inheritance.

Example:
```javascript
class Animal {
  constructor(name) {
    this.name = name;
  }
  speak() {
    console.log(`${this.name} makes a noise.`);
  }
}
class Dog extends Animal {
  speak() {
    console.log(`${this.name} barks.`);
  }
}
const dog = new Dog("Rex");
dog.speak(); // Rex barks.
```

---

## **10. Modules**
- Native support for importing and exporting code.

Example:
```javascript
// module.js
export const greet = () => console.log("Hello!");

// main.js
import { greet } from './module.js';
greet(); // Hello!
```

---

## **11. Iterators and Generators**
- Iterators: Objects that allow sequential access to elements.
- Generators: Functions that can pause and resume execution.

Example:
```javascript
function* generator() {
  yield 1;
  yield 2;
  yield 3;
}
const gen = generator();
console.log(gen.next().value); // 1
console.log(gen.next().value); // 2
console.log(gen.next().value); // 3
```

---

## **12. `Map` and `Set`**
- **`Map`**: Key-value pairs.
- **`Set`**: Unique values.

Example:
```javascript
const map = new Map();
map.set('a', 1);
console.log(map.get('a')); // 1

const set = new Set([1, 2, 2, 3]);
console.log(set.size); // 3
```

---

## **13. Symbols**
- Unique, immutable values.

Example:
```javascript
const sym = Symbol('description');
console.log(sym); // Symbol(description)
```

---

These features provide cleaner syntax, improved functionality, and better performance for JavaScript development. Let me know if you'd like detailed examples or explanations of any specific feature!