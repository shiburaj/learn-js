# 📘 Theory

## 1. **Introduction to JavaScript**

* JavaScript is a **high-level, interpreted programming language** used to make web pages dynamic.
* Runs in the browser and can also run on servers (Node.js).
* **Key features**:

  * Lightweight and interpreted
  * Dynamic typing
  * Object-oriented and functional
  * Client-side scripting for interaction

### Example:

```js
console.log("Hello, Students!");
let name = "Alice";
console.log("Welcome " + name);
```

---

## 2. **Conditional Statements**

* Conditional statements allow decision-making in code.
* **Types**:

  * `if…else`
  * `else if`
  * `switch`

### Example:

```js
let marks = 75;
if (marks >= 50) {
  console.log("Pass");
} else {
  console.log("Fail");
}
```

---

## 3. **Loops**

* Loops are used to repeat a block of code multiple times.
* **Types**:

  * `for`
  * `while`
  * `do…while`

### Example:

```js
for (let i = 1; i <= 5; i++) {
  console.log(i);
}
```

---

## 4. **Functions**

* Functions are reusable blocks of code.
* Can accept **parameters** and return values.

### Example:

```js
function greet(name){
  console.log("Hello " + name);
}
greet("Alice");
```

---

## 5. **Arrays**

* Arrays store multiple values in a single variable.
* Access elements using indices.

### Example:

```js
let fruits = ["Apple", "Banana", "Mango"];
console.log(fruits[0]); // Apple
fruits.push("Orange");
```

---

## 6. **Objects**

* Objects store **key-value pairs** representing related data.

### Example:

```js
let student = {name: "John", age: 20, course: "CS"};
console.log(student.name); // John
```

---

## 7. **Control Flow**

* Combination of **conditions + loops** to control execution.
* Example: print even numbers from 1–10.

```js
for (let i=1; i<=10; i++){
  if(i%2===0) console.log(i);
}
```

---

## 8. **Math Functions**

* JavaScript has built-in math functions:

  * `Math.random()` → random number
  * `Math.sqrt(num)` → square root
  * `Math.max(a,b,...)`, `Math.min(a,b,...)`
  * `Math.pow(a,b)` → a^b

### Example:

```js
console.log(Math.sqrt(64)); // 8
console.log(Math.max(3,7,2)); // 7
```

---

## 9. **Browser Object Model (BOM)**

* BOM represents **browser-related objects** outside the webpage.
* Main objects:

  * `window` → browser window
  * `navigator` → browser info
  * `location` → current URL
  * `history` → browser history
  * `screen` → screen info
* Dialog methods: `alert()`, `prompt()`, `confirm()`

### Example:

```js
alert("Welcome to BOM!");
console.log(window.location.href);
```

---

## 10. **Document Object Model (DOM)**

* DOM represents the **web page structure** as a tree of elements.
* JavaScript can **read and modify** elements.

### Access elements:

```js
document.getElementById("title");
document.querySelector(".class");
```

---

## 11. **DOM Manipulation**

* **Change content**: `element.innerHTML`, `element.textContent`
* **Change styles**: `element.style.color = "red";`
* **Add/remove elements**:

```js
let p = document.createElement("p");
p.textContent = "Hello";
document.body.appendChild(p);
```

* **Event handling**:

```js
button.addEventListener("click", function(){
  console.log("Button clicked!");
});
```

---

## 11. **Events in JavaScript**

* An **event** is an action that occurs in the browser, triggered by the user or the browser itself.
* Examples: clicking a button, moving the mouse, pressing a key, submitting a form, resizing the window.
* Events allow JavaScript to **react** dynamically to user actions.

---

## 12. **Event Flow**

* Event flow describes **how events propagate** through the DOM tree.
* Two main phases:

  1. **Capturing phase**: Event starts from the root element and moves down to the target element.
  2. **Bubbling phase**: Event starts from the target element and bubbles up to the root.
* Use `stopPropagation()` to prevent an event from propagating further.
* `addEventListener` allows specifying `{ capture: true }` to handle events during capturing.

---

## 13. **Event Handlers / Listeners**

* **Event Handlers** are functions executed when an event occurs.
* Two ways to attach handlers:

  1. **HTML attribute**: `<button onclick="myFunc()">Click</button>`
  2. **JavaScript**:

     ```js
     element.addEventListener("click", myFunc);
     ```
* Multiple listeners can be added to a single element without overwriting each other (advantage over HTML attributes).

---

## 14. **The Event Object**

* Every event handler receives an **event object** as a parameter.
* Provides useful properties and methods:

  * `event.type` → type of the event (`click`, `keydown`)
  * `event.target` → element that triggered the event
  * `event.preventDefault()` → prevent default browser behavior
  * `event.stopPropagation()` → stop event propagation
  * Mouse events: `event.clientX`, `event.clientY`
  * Keyboard events: `event.key`, `event.code`

---

## 15. **Types of Events**

* **Mouse Events**: `click`, `dblclick`, `mouseover`, `mouseout`, `mousemove`, `mousedown`, `mouseup`
* **Keyboard Events**: `keydown`, `keyup`, `keypress`
* **Form Events**: `submit`, `focus`, `blur`, `change`, `input`
* **Window Events**: `load`, `resize`, `scroll`, `unload`

---

## 16. **Cross-Browser Events**

* Older browsers like Internet Explorer used `attachEvent()` instead of `addEventListener()`.
* To support all browsers:

  ```js
  if(element.addEventListener){
      element.addEventListener("click", handler, false);
  } else if(element.attachEvent){
      element.attachEvent("onclick", handler);
  }
  ```
* Use `event.target || event.srcElement` for cross-browser access to the event target.

---

## 17. **HTTP Responses**

* JavaScript can interact with servers using **HTTP requests**.
* `fetch()` is the modern API to make requests.
* An HTTP response has:

  * **Status code**: 200 (success), 404 (not found), 500 (server error)
  * **Headers**: metadata about the response
  * **Body**: actual data sent by the server (often JSON)
* Example:

  ```js
  fetch("https://jsonplaceholder.typicode.com/posts")
      .then(response => console.log(response.status));
  ```

---

## 18. **Working with JSON Data**

* JSON = JavaScript Object Notation, a **text format for storing structured data**.
* Convert between JSON and JS objects:

  ```js
  let obj = JSON.parse('{"name":"John", "age":25}'); // JSON → JS
  let jsonStr = JSON.stringify({id:1, task:"Learn JS"}); // JS → JSON
  ```
* Useful for sending and receiving data from APIs.

---

## 19. **Fetch API**

* Modern way to make asynchronous HTTP requests.
* Returns a **Promise**, which resolves to a Response object.
* Example:

  ```js
  fetch("https://jsonplaceholder.typicode.com/users")
      .then(response => response.json())
      .then(data => console.log(data))
      .catch(error => console.log("Error:", error));
  ```
* Can handle success (`then`) and errors (`catch`).

---

## 20. **Callbacks**

* A **callback** is a function passed as an argument to another function.
* It is executed **after a task is completed** (synchronous or asynchronous).
* Useful for handling async operations like `setTimeout`, `fetch`, or events.
* Example:

  ```js
  function greet(name, callback){
      console.log("Hello " + name);
      callback();
  }
  greet("Alice", function(){ console.log("Welcome!"); });
  ```
* **Callback hell**: nesting multiple callbacks, can make code hard to read.

---
