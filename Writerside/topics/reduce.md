# JavaScript `reduce` Method

## Overview
The `reduce` method is used to apply a function to each element of an array, reducing the array to a single value. It’s particularly useful for accumulating results, performing calculations, or combining data from an array into a single output.

### Syntax

```javascript
array.reduce((accumulator, currentValue, currentIndex, array) => {
  // Function body
}, initialValue);
```

### Callback Function

- **callbackfn**: A function that will be executed on each element of the array.

#### Parameters:

- **previousValue**: The accumulated value from the previous iteration. On the first iteration, it is equal to the `initialValue` (if provided) or the first element of the array.
- **currentValue**: The current element being processed.
- **currentIndex** (optional): The index of the current element.
- **array** (optional): The array on which `reduce` was called.
- **initialValue** (optional): The initial value to use as the first argument to the first call of the `callbackfn`. If not provided, the first element of the array will be used as the initial value and the iteration will start from the second element.

### Key Characteristics

- **Returns a Single Value**: Unlike `map` or `filter`, `reduce` returns a single value after processing all elements.
- **Accumulation**: `reduce` is often used to accumulate values or perform aggregations on array elements.
- **Initial Value**: If no `initialValue` is provided, the first element of the array will be used as the initial `previousValue`, and iteration will start with the second element.

### Examples

- **Basic Example**: Summing Numbers

```Javascript
const reducedVals = [1, 2, 3, 4, 5, 6].reduce((prev, next) => {
    console.log(`prev: ${prev} next: ${next}`);
    return prev + next;
});

console.log(reducedVals);  // 21

```

### Explanation

The array `[1, 2, 3, 4, 5, 6]` is reduced to a single value by summing all its elements.
- `prev` accumulates the sum of the elements, while `next` represents the current element.
- The final result is `21`.

### Calculating Total Prices Using `map` and `reduce`

````Javascript
const myDinner = [
    { image: "🍕", name: "pizza", price: 1000 },
    { image: "🍔", name: "burger", price: 800 },
    { image: "🥪", name: "sandwich", price: 600 },
];

// Extract prices using map
const totalArray = myDinner.map(foodObj => foodObj.price);
console.log(totalArray);  // [1000, 800, 600]

// Calculate total bill using reduce
const totalBil = totalArray.reduce((prev, next) => prev + next);
console.log(totalBil);  // 2400

````

### Explanation

- `map` is used to create an array of prices from the `myDinner` array.
- `reduce` then sums up all the prices to calculate the total bill.

### Combining `map` and `reduce`

````Javascript
const totalBill2 = myDinner
                    .map(foodObj => foodObj.price)
                    .reduce((prev, next) => prev + next);

console.log(`My total bill is: ${totalBill2}`);  // My total bill is: 2400

````

### Explanation

- `map` extracts prices from the `myDinner` array.
- `reduce` calculates the total bill in a single chained operation.

### Key Points to Remember

- **Return Value**: The callback function passed to `reduce` must return the accumulated value. Without a return, the result will be `undefined`.
- **Initial Value**: If no `initialValue` is provided, the first element of the array will be used as the initial `previousValue`, and the iteration will start with the second element.
- **Callback Function**: Can be a named function, an anonymous function, or an arrow function. It’s executed for each element in the array.
- **Chaining**: `reduce` can be chained with other array methods like `map`, `filter`, etc., for more complex operations.
- **Performance**: `reduce` is efficient for aggregating results, but its performance should be considered for large arrays or performance-critical code.
    