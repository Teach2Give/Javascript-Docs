# Let-vs-Const

## Variable Declarations: `let` and `const`

In JavaScript, `let` and `const` are used to declare variables. They are part of the ES6 (ECMAScript 2015) specification and offer block-scoping, which provides better control over variable scope compared to `var`.

### `let`

- **Block-Scoped**: Variables declared with `let` are limited to the block (enclosed by `{}`) in which they are defined. This prevents variables from leaking out of their intended scope.
- **Reassignable**: Variables declared with `let` can be reassigned new values.

#### Example:

```javascript
function example() {
  if (true) {
    let x = 10;
    console.log(x); // 10
  }
  console.log(x); // ReferenceError: x is not defined
}

example();
```
### Explanation

- The `let x = 10;` is in the global scope.
- Inside the `if` block, a new `let x` is declared, which shadows the outer `x`.
- The inner `x` is `20`, while the outer `x` remains `10`.

### `const`

- **Block-Scoped**: Like `let`, `const` is also block-scoped.
- **Immutable Binding**: Once a variable is assigned with `const`, it cannot be reassigned. However, this does not make the value itself immutable if it’s an object or an array; only the binding to that value is immutable.

#### Example:

```Javascript
const y = 20;
console.log(y); // 20

// Reassigning will cause an error
// y = 30; // TypeError: Assignment to constant variable

const obj = { key: 'value' };
obj.key = 'newValue'; // Allowed
console.log(obj.key); // 'newValue'
```

## Example 2 
```Javascript
const z = 10; // Global scope

if (z === 10) {
    const z = 20; // Block scope (inside the if block)
    console.log(z); // 20
}

console.log(z); // 10

```
### Explanation

- The `const z = 10;` is in the global scope.
- Inside the `if` block, a new `const z` is declared, which shadows the outer `z`.
- The inner `z` is `20`, while the outer `z` remains `10`.

### `var` (for Comparison)

- **Function-Scoped**: Variables declared with `var` are scoped to the function in which they are defined, or global if defined outside any function.
- **Hoisting**: `var` declarations are hoisted to the top of their scope, but the initialization stays in place.

#### Example:

```Javascript
var y = 10; // Global scope

if (y === 10) {
    var y = 20; // Function or global scope (not block scoped)
    console.log(y); // 20
}

console.log(`The value at y is now: ${y}`); // 20

```
### Explanation

- The `var y = 10;` is in the global scope.
- The `var y = 20;` inside the `if` block affects the global `y`, leading to `y` being `20` everywhere.

### Scope in Functions

- Variables declared with `let` and `const` are block-scoped, while `var` is function-scoped.

#### Example with Function Scope:
```Javascript
var length = 12; // Global variable

function area() {
    return length * length; // Uses global length
}

console.log(area()); // 144

```

## Example with Block Scope
```Javascript
### Explanation

- In the `area` function, the global `length` variable is used.
- In the `parameter` function, `length` and `width` are local to the function, so they do not affect the global `length`.

### Key Points to Remember

- **Block Scope**: `let` and `const` provide block-level scope, making them more predictable and avoiding issues related to variable hoisting and scoping found with `var`.
- **Reassignability**:
  - **`let`**: Variables declared with `let` can be reassigned.
  - **`const`**: Variables declared with `const` cannot be reassigned. However, if the value is an object or array, its contents can still be modified.
- **Function Scope vs. Block Scope**: `var` is function-scoped, while `let` and `const` are block-scoped.

```
### Explanation

- In the `area` function, the global `length` variable is used.
- In the `parameter` function, `length` and `width` are local to the function, so they do not affect the global `length`.

### Key Points to Remember

- **Block Scope**: `let` and `const` provide block-level scope, making them more predictable and avoiding issues related to variable hoisting and scoping found with `var`.
- **Reassignability**:
    - **`let`**: Variables declared with `let` can be reassigned.
    - **`const`**: Variables declared with `const` cannot be reassigned. However, if the value is an object or array, its contents can still be modified.
- **Function Scope vs. Block Scope**: `var` is function-scoped, while `let` and `const` are block-scoped.
