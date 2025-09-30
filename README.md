# JavaScript Interview Q&A

---

## Q1. Variables: `var`, `let`, and `const`

### 1. Simple Definition

* **`var`** → Function-scoped, can be re-declared & updated. (Old way, ES5 and earlier)
* **`let`** → Block-scoped, can be updated but not re-declared in the same scope.
* **`const`** → Block-scoped, cannot be reassigned. Used for constants or fixed references.

---

### 2. Real-World Use Case

* Use **`var`** only when maintaining **legacy JavaScript code**.
* Use **`let`** for variables that **change their value**, e.g., loop counters, temporary states.
* Use **`const`** when the **value should not change**, e.g., API keys, configuration values, or function references.

---

### 3. Full Example (with step-by-step explanation)

```javascript
// 1. var example
function oldWay() {
  var name = "Alice";  
  // 'var' is function-scoped → available in the whole function

  if (true) {
    var name = "Bob";  
    // Re-declared → overwrites previous value
    console.log("Inside if with var:", name); // Output: Bob
  }

  console.log("Outside if with var:", name); // Output: Bob (unexpected!)
}
oldWay();

// 2. let example
function modernWay() {
  let age = 25;  
  // 'let' is block-scoped → stays inside the nearest {}

  if (true) {
    let age = 30;  
    // New variable, only inside this block
    console.log("Inside if with let:", age); // Output: 30
  }

  console.log("Outside if with let:", age); // Output: 25 (original preserved)
}
modernWay();

// 3. const example
function constantWay() {
  const pi = 3.14159;  
  // Cannot be reassigned → ensures safety
  console.log("Value of pi:", pi);

  // pi = 3.15; ❌ Error: Assignment to constant variable

  // Note: const does not make objects fully immutable
  const user = { name: "Alice" };
  user.name = "Bob";  
  // Allowed: object property can change
  console.log("Updated user name:", user.name); // Output: Bob
}
constantWay();
```

---

### 4. Why Each Is Used

* **`var`** → Legacy support; avoid in modern code.
* **`let`** → Safer scoping rules for modern apps.
* **`const`** → Guarantees identifier can’t be reassigned, improves code reliability.

---
