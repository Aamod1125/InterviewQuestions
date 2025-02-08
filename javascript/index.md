1) ## Top 10 ES-6 feature 

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


2) ## JavaScript provides several types of functions based on how they are declared and used. Here’s a breakdown:


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




3) ## advanced JavaScript interview questions** along with **examples and explanations** to help you prepare:  

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
function debounce(func, delay) {
    let timer;
    return function (...args) {
        clearTimeout(timer);
        timer = setTimeout(() => func(...args), delay);
    };
}

const log = debounce(() => console.log("Debounced!"), 1000);
window.addEventListener("resize", log);
```
🔹 **Use case:** Avoid multiple function calls while typing in a search bar.

### **Throttling Example:**
```js
function throttle(func, limit) {
    let lastCall = 0;
    return function (...args) {
        let now = Date.now();
        if (now - lastCall >= limit) {
            lastCall = now;
            func(...args);
        }
    };
}

const log = throttle(() => console.log("Throttled!"), 2000);
window.addEventListener("scroll", log);
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