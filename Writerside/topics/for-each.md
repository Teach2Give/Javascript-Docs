# JavaScript `forEach` Method

## Overview

The `forEach` method is used to execute a provided function once for each element in an array. It’s ideal for performing operations on array elements without creating a new array.

### Characteristics
- **Purpose**: Iterates over each element and performs a given operation.
- **No Return Value**: Unlike `map` or `filter`, `forEach` does not return a new array.
- **Modifies Original Array**: Operations are applied to each element directly.

## Syntax

```javascript
array.forEach(callbackfn, thisArg);
```

### `callbackfn`

A function that is executed on each element of the array.

**Parameters:**

- **`value`**: The current element being processed.
- **`index`** *(optional)*: The index of the current element.
- **`array`** *(optional)*: The array on which `forEach` was called.
- **`thisArg`** *(optional)*: Value to use as `this` when executing `callbackfn`.

```Javascript
let runners = ['Kiplimo', 'Kipchumba', 'Koskei'];
runners.forEach(function(runner) {
    console.log(`${runner} runs a 100 meters`);
});

[//]: # (Kiplimo runs a 100 meters)

[//]: # (Kipchumba runs a 100 meters)

[//]: # (Koskei runs a 100 meters)

```

**Explanation:**

- `runners` is an array of names.
- `forEach` iterates through each name and logs a message.

```Javascript
let total = 0;
let marks = [23, 45, 56, 67, 78, 90];
let size = marks.length;

marks.forEach((mark) => {
    total += mark;
    console.log(`Your average mark is ${total / size}`);
});

[//]: # (Your average mark is 3.8333333333333335)

[//]: # (Your average mark is 6.5)

[//]: # (Your average mark is 8.666666666666666)

[//]: # (Your average mark is 10.5)

[//]: # (Your average mark is 12.833333333333334)

[//]: # (Your average mark is 15)


```

**Explanation:**

- `marks` is an array of numbers representing student marks.
- `total` accumulates the sum of all marks.
- `size` is the total number of elements in the array.
- The average is recalculated and logged after each mark is added.

**Note:** Logging the average after each addition may not be ideal. Typically, you would log the average once, after all marks have been processed.

**Key Points to Remember:**

- **Side Effects:** Use `forEach` for operations with side effects (e.g., updating external variables). For transformations, use methods like `map`, `filter`, or `reduce`.
- **No Early Exit:** `forEach` does not support breaking out of the loop early. For early exit, use a traditional `for` loop or methods like `some` or `every`.
- **Callback Function:** Can be a named function, an anonymous function, or an arrow function. It’s executed for each array element in order.
- **Performance:** `forEach` is generally slower than traditional `for` loops for large arrays but is suitable for smaller arrays or non-performance-critical tasks.
- **Error Handling:** Include `try-catch` blocks inside the callback function for error handling if needed.
