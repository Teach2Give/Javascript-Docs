# JavaScript `map` Method

## Overview

The `map` method creates a new array populated with the results of calling a provided function on every element in the calling array. Unlike `forEach`, `map` returns a new array and does not modify the original array.

## Syntax

```javascript
array.map(callbackfn, thisArg);
```

## `callbackfn`

A function that will be executed on each element of the array.

**Parameters:**

- **`value`**: The current element being processed.
- **`index`** *(optional)*: The index of the current element.
- **`array`** *(optional)*: The array on which `map` was called.
- **`thisArg`** *(optional)*: Value to use as `this` when executing `callbackfn`.

## Key Characteristics

- **Returns a New Array**: The `map` method returns a new array containing the results of the callback function. The original array remains unchanged.
- **Requires `return`**: The callback function must use the `return` keyword to provide the new value for the new array. Omitting `return` will result in `undefined` values in the new array.
- **Immutable**: The `map` method does not modify the original array.

## Examples

### Basic Example: Transforming Array Elements

```javascript
let runners = ["Kiplimo", "Kipchumba", "Koskei"];
let newRunnerMsg = runners.map(function (runner) {
  return `${runner} runs a 100 meters`;
});

console.log(runners);         // ["Kiplimo", "Kipchumba", "Koskei"]
console.log(newRunnerMsg);    // ["Kiplimo runs a 100 meters", "Kipchumba runs a 100 meters", "Koskei runs a 100 meters"]
```
## Explanation {id="explanation_1"}

- `runners` is an array of names.
- `map` creates a new array where each name is transformed into a message string.
- The original `runners` array is unchanged.

## Accessing Properties from Objects

```javascript
const initialFoodPrices = [
  { image: "🍕", name: "pizza", price: 1000 },
  { image: "🍔", name: "burger", price: 800 },
  { image: "🥪", name: "sandwich", price: 600 },
];

initialFoodPrices.map((foodObj) => {
    console.log(foodObj.price);
});
```
## Explanation {id="explanation_2"}

- `initialFoodPrices` is an array of objects, each representing a food item with properties: `image`, `name`, and `price`.
- `map` is used to iterate through each `foodObj`, and the `price` of each item is logged to the console.

## Extracting and Summing Prices

```javascript
let foodPrices = initialFoodPrices.map(foodObj => foodObj.price);
console.log(foodPrices);  // [1000, 800, 600]

let total = 0;
foodPrices.map(price => total += price);
console.log(total);      // 2400
```
## Explanation

- `map` is used to create an array of prices from the `initialFoodPrices` array.
- Another `map` is used to accumulate the total price from the `foodPrices` array.

**Note:**
- In the arrow function `foodObj => foodObj.price`, parentheses `()` around `foodObj.price` implicitly return the value, so no `return` keyword is needed.
- Using `{}` in the arrow function requires an explicit `return`.

## Key Points to Remember

- **Return Value**: Always use the `return` keyword inside the callback function to specify the new value for the new array. Without `return`, the result will be `undefined` in the new array.
- **Callback Function**: Can be a named function, an anonymous function, or an arrow function. Arrow functions provide a concise syntax.
- **Chaining**: `map` can be chained with other array methods like `filter` and `reduce` for more complex operations.
- **Performance**: `map` is suitable for transforming arrays but may not be the fastest option for large arrays or performance-critical code.
- **Immutability**: The `map` method does not alter the original array, ensuring that the original data remains unchanged.

