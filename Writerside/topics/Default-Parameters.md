# Default Parameters

## Overview

Default parameters allow you to specify default values for function parameters. If a parameter is not provided or is `undefined`, the default value is used. This feature enhances code readability and reduces the need for manual checks and assignments inside functions.

### Basic Syntax

**Traditional Function (Pre-ES6):**

Before ES6, default parameter values had to be handled manually inside the function.

```javascript
function say(message) {
   message = typeof message !== 'undefined' ? message : 'hi';
   console.log(message);
}

say(); // Output: hi
```
## ES6 Default Parameters

With ES6, you can directly assign default values in the function declaration.

```javascript
function say(message = 'hi') {
   console.log(message);
}

say(); // Output: hi
```

## Default Parameters in Functions

### Single Parameter with Default Value

```javascript
function sum(numA, numB = 5) {
    console.log(numA + numB);
}

sum(10);  // Output: 15 (numB defaults to 5)
sum(5, 15); // Output: 20 (numB is set to 15)
```

### Explanation

- `numB = 5` provides a default value for `numB`. If no value is passed for `numB`, it defaults to `5`.

### Multiple Parameters with Default Values

```javascript
function greet(greeting = 'Hello', name = 'World') {
    console.log(`${greeting}, ${name}!`);
}

greet(); // Output: Hello, World!
greet('Hi'); // Output: Hi, World!
greet('Hi', 'Dan'); // Output: Hi, Dan!
```

### Explanation

- Both `greeting` and `name` have default values, and they are used when the corresponding arguments are not provided.

### Arrow Functions with Default Parameters

**Basic Example:**

```javascript
const sayHi = (message = 'Hi') => {
    console.log(message);
}

sayHi(); // Output: Hi
```

