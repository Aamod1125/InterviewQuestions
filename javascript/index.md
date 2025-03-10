
$${\color{red}Top-10-ES6-feature }$$

https://medium.com/@shubham3480/features-introduced-in-es6-e8b10bd93150

https://medium.com/@kavisha.talsania/top-10-es6-features-every-javascript-developer-must-know-4c81ec54bbcd

[text](https://medium.com/@wilsen.tjhung/es5-vs-es6-syntax-6c8350fa6998)

`
1. let and const keywords
2. arrow functions
3. multiline string
4. templete literals 
4. defauly parameeter object
5. destractring assignment 
6. enhanced object literal
7. Promissis
8. class 
9. modules 
`

 ### **Difference Between Arrow Function and Normal Function in JavaScript**


| Feature            | **Arrow Function** (`=>`) | **Normal Function** (`function`) |
|--------------------|--------------------------|------------------------------|
| **Syntax**         | More concise, uses `=>` | Uses `function` keyword |
| **`this` Binding** | Lexically inherits `this` from surrounding scope | Has its own `this`, depends on how it's called |
| **Arguments Object** | Does **not** have `arguments` object | Has `arguments` object |
| **Usage in Methods** | Not suitable as an object method (`this` refers to outer scope) | Works fine as an object method (`this` refers to the object) |
| **Constructors** | Cannot be used as a constructor (throws an error if used with `new`) | Can be used with `new` to create objects |
| **Implicit Return** | Can return values implicitly (if one expression is used) | Must use `return` for returning values |

---

### **Benefits of Arrow Functions**
1. **Shorter Syntax**  
   - Makes code cleaner and more readable.
   ```js
   const add = (a, b) => a + b;  // Shorter than function add(a, b) { return a + b; }
   ```

2. **Lexical `this`** (No Binding Required)  
   - Useful when dealing with event listeners, callbacks, and promises.
   ```js
   function normalFunction() {
       console.log(this);  // `this` depends on how function is called
   }

   const arrowFunction = () => {
       console.log(this);  // `this` refers to surrounding scope
   };
   ```

3. **No `arguments` Object** (Encourages Use of Rest Parameters)  
   ```js
   function normalFunction() {
       console.log(arguments);  // Works
   }

   const arrowFunction = () => {
       console.log(arguments);  // Throws an error
   };
   ```

4. **Implicit Return for One-liners**  
   ```js
   const square = x => x * x;  // No need for return keyword
   ```

5. **Better for Callbacks and Promises**  
   ```js
   setTimeout(() => console.log("Hello!"), 1000);
   ```

### **When to Use Arrow Functions?**
✅ For **short, simple functions** (e.g., callbacks, array methods like `map`, `filter`, `reduce`)  
✅ When you want **`this` to refer to the surrounding scope**  
❌ Avoid using them as **object methods** or **constructors**  

Would you like some real-world examples? 🚀




$${\color{red}JavaScript-provides-several-types-of-functions-based-on how-they-are-declared-and-used- Here’s a breakdown:}$$


---

### **1. Named Function**
A function with a specific name, which can be reused and called multiple times.
```js
function greet(name) {
    return `Hello, ${name}!`;
}
console.log(greet("Alice")); // Output: Hello, Alice!
```

---

### **2. Anonymous Function**
A function without a name, typically assigned to a variable or used as a callback.
```js
const greet = function(name) {
    return `Hello, ${name}!`;
};
console.log(greet("Bob"));
```

---

### **3. Arrow Function** (`=>`)
A concise function syntax with automatic lexical binding of `this`.
```js
const greet = (name) => `Hello, ${name}!`;
console.log(greet("Charlie"));
```
> ✅ Best for callbacks, array methods, and when you don't need `this`.

---

### **4. Immediately Invoked Function Expression (IIFE)**
A function that runs immediately after being defined.
```js
(function() {
    console.log("I run immediately!");
})();
```
> ✅ Useful for avoiding global scope pollution.

---

### **5. Higher-Order Function**
A function that takes another function as an argument or returns a function.
```js
function applyFunction(fn, value) {
    return fn(value);
}

const double = x => x * 2;
console.log(applyFunction(double, 5)); // Output: 10
```
> ✅ Useful for functional programming.

---

### **6. Callback Function**
A function passed as an argument to another function.
```js
function fetchData(callback) {
    setTimeout(() => {
        callback("Data received");
    }, 1000);
}

fetchData(console.log);
```
> ✅ Used in event listeners, `setTimeout`, and API calls.

---

### **7. Generator Function** (`function*`)
A function that can pause execution and resume later using `yield`.
```js
function* numbers() {
    yield 1;
    yield 2;
    yield 3;
}

const gen = numbers();
console.log(gen.next().value); // Output: 1
console.log(gen.next().value); // Output: 2
```
> ✅ Used for handling asynchronous tasks and iterators.

---

### **8. Recursive Function**
A function that calls itself to solve problems like factorial, Fibonacci, etc.
```js
function factorial(n) {
    if (n === 1) return 1;
    return n * factorial(n - 1);
}
console.log(factorial(5)); // Output: 120
```
> ✅ Useful for solving problems with recursive structures.

---

### **9. Constructor Function**
A function used to create objects with the `new` keyword.
```js
function Person(name, age) {
    this.name = name;
    this.age = age;
}

const alice = new Person("Alice", 25);
console.log(alice.name); // Output: Alice
```
> ✅ Used to create multiple objects with the same properties and methods.

---

### **10. Async Function (`async/await`)**
A function that works with Promises to handle asynchronous code in a readable way.
```js
async function fetchData() {
    return "Data fetched";
}

fetchData().then(console.log); // Output: Data fetched
```
> ✅ Used for fetching API data, database queries, etc.

---

### **Conclusion**
| Function Type | Use Case |
|--------------|----------|
| Named Function | Reusable and easy to debug |
| Anonymous Function | Used as a variable or callback |
| Arrow Function | Shorter syntax, no `this` binding |
| IIFE | Avoids global scope pollution |
| Higher-Order Function | Functional programming |
| Callback Function | Async operations, event handling |
| Generator Function | Handles large data or async flow |
| Recursive Function | Solves problems recursively |
| Constructor Function | Creates multiple objects |
| Async Function | Works with `await` and Promises |

Would you like a deep dive into any of these? 🚀




 


$${\color{red}advanced-JavaScript-interview-questions}$$

---

## **1. What is Event Loop in JavaScript?**

### **Question:** Explain the event loop mechanism in JavaScript.

### **Answer:**
JavaScript is single-threaded but can handle asynchronous operations using the **Event Loop**.  
The event loop ensures that the **Call Stack** executes synchronously, while handling asynchronous operations (callbacks, promises, setTimeout, etc.) via the **Callback Queue** and **Microtask Queue**.

### **Example:**
```js
console.log("Start");

setTimeout(() => {
    console.log("Inside setTimeout");
}, 0);

Promise.resolve().then(() => console.log("Inside Promise"));

console.log("End");
```
### **Output:**
```
Start
End
Inside Promise
Inside setTimeout
```
**Explanation:**  
1. **"Start"** & **"End"** execute first (synchronous).  
2. The **setTimeout** goes to the **Callback Queue** (executed in the next Event Loop cycle).  
3. The **Promise** goes to the **Microtask Queue** (executed before the callback queue).  
4. The event loop processes the **Microtask Queue** before the **Callback Queue**.  

---

## **2. Explain Closures in JavaScript**

### **Question:** What is a closure? How does it work?

### **Answer:**
A **closure** is a function that retains access to variables from its parent scope, even after the parent function has finished execution.

### **Example:**
```js
function outerFunction(outerValue) {
    return function innerFunction(innerValue) {
        console.log(`Outer: ${outerValue}, Inner: ${innerValue}`);
    };
}

const closureFunc = outerFunction("Hello");
closureFunc("World"); 
```
### **Output:**
```
Outer: Hello, Inner: World
```
**Explanation:**  
- `innerFunction` is returned from `outerFunction`, but it **remembers** the value of `outerValue`, forming a **closure**.

---

## **3. What is Debouncing and Throttling?**

### **Question:** Explain Debouncing and Throttling with examples.

### **Answer:**  
- **Debouncing:** Limits function execution until after a specified delay.  
- **Throttling:** Ensures function execution occurs at most once in a given time interval.

### **Debouncing Example:**
```js
// Debounce function
function debounce(func, delay) {
    let timer;
    return function (...args) {
        clearTimeout(timer);
        timer = setTimeout(() => func(...args), delay);
    };
}

// Function to handle search input
function handleSearchInput(event) {
    const query = event.target.value;
    console.log(`Searching for: ${query}`);
    // Add your search logic here (e.g., API call)
}

// Get the search input element
const searchInput = document.getElementById('search-input');

// Attach the debounced event handler to the input event
searchInput.addEventListener('input', debounce(handleSearchInput, 300));


```
🔹 **Use case:** Avoid multiple function calls while typing in a search bar.

### **Throttling Example:**
```js
// Throttle function
function throttle(func, limit) {
    let lastCall = 0;
    return function (...args) {
        const now = Date.now();
        if (now - lastCall >= limit) {
            lastCall = now;
            func(...args);
        }
    };
}

// Function to handle API call
function fetchMoreData() {
    console.log("Fetching more data...");
    // Add your API call logic here
    // Example: fetch('/api/data').then(response => response.json()).then(data => console.log(data));
}

// Attach the throttled event handler to the scroll event
window.addEventListener('scroll', throttle(() => {
    if (window.innerHeight + window.scrollY >= document.body.offsetHeight) {
        fetchMoreData();
    }
}, 2000)); // Throttle limit set to 2000 milliseconds (2 seconds)

```
🔹 **Use case:** Controlling API calls on infinite scroll.

---

## **4. Explain Hoisting in JavaScript**

### **Question:** How does hoisting work?

### **Answer:**  
Hoisting moves **function** and **variable declarations** to the top of their scope **before execution**.

### **Example:**
```js
console.log(a); // undefined
var a = 10;

foo(); // Works
function foo() {
    console.log("Function Hoisted!");
}
```
**Explanation:**  
- **`var a`** is hoisted but **not initialized**, so it logs `undefined`.  
- **`foo()`** is hoisted **with its definition**, so it executes normally.  

🔹 **Note:** `let` and `const` are also hoisted but are in a **Temporal Dead Zone (TDZ)** and cannot be accessed before declaration.

---

## **5. What is the Difference Between `==` and `===`?**

### **Question:** Explain type coercion with examples.

### **Answer:**  
- **`==` (Abstract Equality):** Converts operands to the same type before comparison.  
- **`===` (Strict Equality):** Does not perform type conversion.

### **Example:**
```js
console.log(5 == "5");  // true  (type coercion: "5" -> 5)
console.log(5 === "5"); // false (different types)
console.log(false == 0); // true (false -> 0)
console.log(null == undefined); // true (special case)
```
🔹 **Best practice:** Always use `===` to avoid unexpected results.

---

## **6. Explain `call()`, `apply()`, and `bind()`**

### **Question:** What is the difference between `call()`, `apply()`, and `bind()`?

### **Answer:**  
These methods **explicitly bind `this`** in JavaScript.

| Method  | Usage |
|---------|-------|
| `call()`  | Calls a function with `this` and arguments passed individually. |
| `apply()` | Calls a function with `this` and arguments as an array. |
| `bind()`  | Returns a new function with `this` permanently bound. |

### **Example:**
```js
const person = {
    name: "Alice",
    greet: function (city) {
        console.log(`Hello, I'm ${this.name} from ${city}`);
    }
};

const person2 = { name: "Bob" };

person.greet.call(person2, "New York"); // Using call()
person.greet.apply(person2, ["London"]); // Using apply()

const boundGreet = person.greet.bind(person2, "Paris"); // Using bind()
boundGreet();
```
**Output:**
```
Hello, I'm Bob from New York
Hello, I'm Bob from London
Hello, I'm Bob from Paris
```
🔹 **Use `bind()`** when you need a function later with a fixed `this`.

---

## **7. What are WeakMap and WeakSet?**

### **Question:** How are WeakMap and WeakSet different from Map and Set?

### **Answer:**  
- **WeakMap:** Holds key-value pairs where **keys must be objects** and are **weakly referenced**.
- **WeakSet:** Stores **only objects** and allows weak references.

### **Example:**
```js
let obj = { name: "Alice" };

const weakMap = new WeakMap();
weakMap.set(obj, "Value");

obj = null; // Now the object is garbage collected
```
🔹 **Why use it?** Prevents memory leaks because **garbage collection** automatically removes unused objects.

---

## **8. What is the Output of This Code?**
```js
console.log(typeof NaN);  
console.log(0.1 + 0.2 === 0.3);
console.log([] == false);
console.log("5" - 3);
```
### **Answer:**
```
"number"    // NaN is of type number
false       // Due to floating-point precision issues
true        // [] is coerced to "", which is falsy
2           // "5" is converted to a number
```
🔹 **Takeaway:** Be aware of type coercion in JavaScript.

---

## **Final Thoughts**
These **advanced JavaScript questions** test your knowledge of **core concepts**, including:
✔ **Closures**  
✔ **Event Loop**  
✔ **Hoisting**  
✔ **Call, Apply, Bind**  
✔ **WeakMap & WeakSet**  
✔ **Debouncing & Throttling**  

Would you like more **hands-on coding challenges** or **real-world scenarios**? 🚀




### $${\color{red} WeakMap-and-WeakSet-in-JavaScript-details}$$

JavaScript provides two special collection objects, **WeakMap** and **WeakSet**, which are similar to `Map` and `Set` but have some important differences, primarily related to garbage collection and memory management.

---

## **1. WeakMap**
A `WeakMap` is a collection of key-value pairs where **keys must be objects**, and values can be any type. The key-value pairs are weakly held, meaning if there are no other references to the key object, the key-value pair will be removed from memory automatically.

### **Key Characteristics of WeakMap**
1. **Keys must be objects** (not primitive values).
2. **Weak references** – If an object key has no other references, it gets garbage collected.
3. **No size property** – Cannot check the number of elements.
4. **No iteration** – Cannot iterate over its elements (e.g., using `forEach` or `for...of` loops).
5. **Supports only `set`, `get`, `has`, and `delete` methods.**

### **Syntax and Methods**
```javascript
let weakMap = new WeakMap();

// Creating objects
let obj1 = { name: "Alice" };
let obj2 = { name: "Bob" };

// Adding key-value pairs
weakMap.set(obj1, "Developer");
weakMap.set(obj2, "Designer");

// Retrieving values
console.log(weakMap.get(obj1)); // "Developer"

// Checking if a key exists
console.log(weakMap.has(obj2)); // true

// Deleting an entry
weakMap.delete(obj1);
console.log(weakMap.has(obj1)); // false
```

### **Use Case of WeakMap**
- **Memory-efficient caching**: Storing metadata or temporary data about objects without preventing garbage collection.
- **DOM elements handling**: Useful when associating metadata with DOM nodes, ensuring automatic cleanup when nodes are removed.

```javascript
let cache = new WeakMap();

function processData(obj) {
    if (!cache.has(obj)) {
        cache.set(obj, `Processed: ${obj.name}`);
    }
    return cache.get(obj);
}

let user = { name: "Charlie" };
console.log(processData(user)); // "Processed: Charlie"

user = null; // If there are no references to user, it will be garbage collected
```

---

## **2. WeakSet**
A `WeakSet` is a collection of **objects only**, where each object is stored weakly. If no other references exist for an object, it will be automatically removed.

### **Key Characteristics of WeakSet**
1. **Only objects can be added** (no primitives like numbers or strings).
2. **Weak references** – Objects are garbage collected when there are no other references.
3. **No size property** – Cannot check the number of elements.
4. **No iteration** – Cannot loop through its elements.
5. **Supports only `add`, `has`, and `delete` methods.**

### **Syntax and Methods**
```javascript
let weakSet = new WeakSet();

// Creating objects
let objA = { id: 1 };
let objB = { id: 2 };

// Adding objects to WeakSet
weakSet.add(objA);
weakSet.add(objB);

// Checking if objects exist in WeakSet
console.log(weakSet.has(objA)); // true

// Removing an object
weakSet.delete(objB);
console.log(weakSet.has(objB)); // false
```

### **Use Case of WeakSet**
- **Tracking live objects**: Useful for marking objects that should not be duplicated or processed again.
- **Temporary object storage**: Keeping a reference to objects while they are in use but allowing automatic cleanup when no longer needed.

```javascript
let seenObjects = new WeakSet();

function checkObject(obj) {
    if (seenObjects.has(obj)) {
        console.log("Already processed:", obj);
    } else {
        seenObjects.add(obj);
        console.log("Processing:", obj);
    }
}

let data = { value: 42 };
checkObject(data); // Processing: { value: 42 }
checkObject(data); // Already processed: { value: 42 }

data = null; // If no other references exist, it will be garbage collected
```

---

## **Comparison: WeakMap vs WeakSet**
| Feature      | WeakMap                          | WeakSet                        |
|-------------|----------------------------------|--------------------------------|
| **Key Type** | Only objects (keys are weakly held) | Only objects (values are weakly held) |
| **Value Type** | Any type                         | No values (just objects)       |
| **Iteration** | ❌ Not iterable                  | ❌ Not iterable                |
| **Size Property** | ❌ Not available              | ❌ Not available               |
| **Methods** | `set`, `get`, `has`, `delete` | `add`, `has`, `delete` |
| **Garbage Collection** | ✅ Removes key-value pairs when keys are no longer referenced | ✅ Removes objects when no longer referenced |

---

## **When to Use WeakMap and WeakSet?**
- **Use `WeakMap`** when you need to associate data with an object while allowing garbage collection.
- **Use `WeakSet`** when you need to keep track of objects without preventing their garbage collection.

Would you like an example of how these can be used in a real-world scenario? 🚀




### $${\color{red} Types-of-for-loop}$$

JavaScript provides several types of `for` loops for iterating over arrays, objects, and other iterable structures. Here’s a breakdown of each type and when to use them:

---

## **1. for Loop (Traditional)**
This is the most common and flexible loop, mainly used for iterating over arrays or when the number of iterations is known.

### **Syntax:**
```javascript
for (initialization; condition; update) {
    // Code to execute
}
```

### **Example:**
```javascript
for (let i = 0; i < 5; i++) {
    console.log("Iteration:", i);
}
```
### **Use Case:**
- When you need a counter.
- When iterating through an array using an index.

---

## **2. for...in Loop**
Used for iterating over the properties (keys) of an object.

### **Syntax:**
```javascript
for (let key in object) {
    // Code to execute
}
```

### **Example:**
```javascript
let person = { name: "Alice", age: 25, city: "New York" };

for (let key in person) {
    console.log(key, ":", person[key]);
}
```
### **Use Case:**
- Iterating over object properties.
- **Avoid using `for...in` for arrays** because it may iterate over inherited properties.

---

## **3. for...of Loop**
Used for iterating over iterable objects like arrays, strings, maps, and sets.

### **Syntax:**
```javascript
for (let value of iterable) {
    // Code to execute
}
```

### **Example:**
```javascript
let fruits = ["Apple", "Banana", "Cherry"];

for (let fruit of fruits) {
    console.log(fruit);
}
```
### **Use Case:**
- Iterating over arrays, strings, maps, sets, and other iterable objects.
- Preferred over `for...in` for arrays since it directly accesses values.

---

## **4. forEach() Method (Array Method)**
Used to iterate over arrays but does not support `break` or `continue`.

### **Syntax:**
```javascript
array.forEach((element, index, array) => {
    // Code to execute
});
```

### **Example:**
```javascript
let numbers = [1, 2, 3, 4];

numbers.forEach((num, index) => {
    console.log(`Index: ${index}, Value: ${num}`);
});
```
### **Use Case:**
- When you need to execute a function on each array element.
- **Cannot be stopped using `break` or `continue`** (use `for` or `for...of` if needed).

---

## **Comparison Table**
| Loop Type      | Use Case | Can Break/Continue? | Works on Objects? | Works on Arrays? |
|---------------|---------|--------------------|------------------|-----------------|
| `for`         | General iteration | ✅ Yes | ❌ No | ✅ Yes |
| `for...in`    | Iterating object properties | ✅ Yes | ✅ Yes | 🚫 Avoid (may iterate over prototype) |
| `for...of`    | Iterating iterable objects | ✅ Yes | ❌ No | ✅ Yes |
| `forEach()`   | Running a function on array elements | ❌ No | ❌ No | ✅ Yes |

Would you like more detailed examples or real-world scenarios? 😊




$${\color{red}The- rest- and -spread- operators -in -JavaScript }$$

The rest and spread operators in JavaScript both use the three-dot syntax (...), but they serve different purposes.

1. Rest Operator (...)

* The rest operator is used in function parameters to collect multiple arguments into an array.

* It helps handle variable numbers of arguments.

* It must be the last parameter in a function.

# Example of Rest Operator:

```
function sum(...numbers) {
    return numbers.reduce((acc, curr) => acc + curr, 0);
}

console.log(sum(1, 2, 3, 4)); // Output: 10

```

2. Spread Operator (...)

* The spread operator is used to expand elements of an iterable (like arrays or objects).
* It helps copy or merge arrays/objects.

```
const arr1 = [1, 2, 3];
const arr2 = [...arr1, 4, 5, 6]; // Expanding arr1 into arr2

console.log(arr2); // Output: [1, 2, 3, 4, 5, 6]
```


$${\color{red} Deep - Copy - vs - Shallow - Copy - in- JavaScript }$$

### **Deep Copy vs Shallow Copy in JavaScript**  

When copying objects in JavaScript, we can create a **shallow copy** or a **deep copy**. The difference lies in how they handle nested objects.

---

## **1. What is a Shallow Copy?**  

A **shallow copy** only copies **references** to nested objects instead of duplicating them. If the original object is modified, the shallow copy will reflect those changes.

### **Example:**
```javascript
let obj1 = { 
    name: "Alice", 
    details: { age: 25, city: "New York" } 
};

// Shallow Copy using spread operator
let obj2 = { ...obj1 };

obj2.details.age = 30; // Modifying the nested object

console.log(obj1.details.age); // Output: 30 (Original object is affected)
console.log(obj2.details.age); // Output: 30
```
🔹 **Why?**  
- `details` is a reference, so both `obj1` and `obj2` point to the **same memory location**.  
- Changes in `obj2.details` affect `obj1.details`.

### **Other Ways to Create a Shallow Copy:**
```javascript
let obj2 = Object.assign({}, obj1);
```

---

## **2. What is a Deep Copy?**  

A **deep copy** creates a completely new object, duplicating all properties and **nested objects**, so modifications do not affect the original object.

### **Example using `JSON.parse(JSON.stringify())`:**
```javascript
let obj1 = { 
    name: "Alice", 
    details: { age: 25, city: "New York" } 
};

// Deep Copy
let obj2 = JSON.parse(JSON.stringify(obj1));

obj2.details.age = 30; // Modifying the nested object

console.log(obj1.details.age); // Output: 25 (Original object is NOT affected)
console.log(obj2.details.age); // Output: 30
```
🔹 **Why?**  
- `JSON.stringify()` converts the object into a string.  
- `JSON.parse()` creates a completely new object.  

⚠️ **Limitation**:  
- **Does not support functions, `undefined`, `Date`, `RegExp`, or `Map/Set`.**  

---

## **3. Modern Way to Deep Copy (`structuredClone`)**

```javascript
let obj1 = { 
    name: "Alice", 
    details: { age: 25, city: "New York" } 
};

// Deep Copy using structuredClone
let obj2 = structuredClone(obj1);

obj2.details.age = 30;

console.log(obj1.details.age); // Output: 25 (Original object is NOT affected)
console.log(obj2.details.age); // Output: 30
```
✅ **Supports objects with functions, arrays, and nested structures.**  
✅ **Faster than `JSON.parse(JSON.stringify())`.**  

---

## **4. Deep Copy Using Lodash (`_.cloneDeep`)**
Lodash provides an easy way to create deep copies.

```javascript
let _ = require("lodash");

let obj1 = { 
    name: "Alice", 
    details: { age: 25, city: "New York" } 
};

// Deep Copy using lodash
let obj2 = _.cloneDeep(obj1);

obj2.details.age = 30;

console.log(obj1.details.age); // Output: 25
console.log(obj2.details.age); // Output: 30
```
🔹 **Why Use Lodash?**  
- Handles `Date`, `RegExp`, `Map`, `Set`, etc.  
- More reliable for complex objects.

---

## **Summary Table**
| Copy Type | Nested Objects | Methods |
|-----------|---------------|---------|
| **Shallow Copy** | Shared reference (changes affect original) | `Object.assign()`, `{ ...obj }` |
| **Deep Copy** | Completely new object (independent) | `JSON.parse(JSON.stringify())`, `structuredClone()`, `_.cloneDeep()` |

---

## **When to Use?**
✅ Use **shallow copy** if you only need to copy **top-level properties**.  
✅ Use **deep copy** when working with **nested objects** to prevent unintended modifications.  












