# Rest and Spread operators

## Rest Parameters ( ... )
The rest operator (...) in JavaScript allows functions to accept an indefinite number of arguments as an array. This is particularly 
useful when you don't know how many arguments will be passed into
the function.

#### Example 1: Using Rest Parameters
```Javascript
function say(a, b, c, d, ...params) {
  // 'params' is an array holding all remaining arguments after the first four (a, b, c, d)
}

```
Here, say() is a function that takes four defined parameters (a, b, c, and d) and uses ...params to capture any additional arguments as an array.

#### Example 2: Rest Parameters with Filtering
The function sum below uses the rest operator to collect all the arguments passed to it, then filters only the numbers and sums them up:
```Javascript
function sum(...args) {
  return args.filter((elem) => typeof elem === 'number')
             .reduce((prev, next) => prev + next);
}

let result = sum(1, "Pamela", "hello", 90, undefined, null);
console.log(result); // Output: 91
```

##### Explanation: 
1. The `sum` function accepts an infinite number of arguments using the rest operator `...args`.
    1. The rest operator gathers the arguments into an array.
    2. It can handle any number of arguments passed into the function.

2. It filters out all non-numeric values.
    1. The `filter()` method is used to identify numbers.
    2. Only values that are of type `number` are kept.

3. Then, it uses `reduce()` to sum up all the numbers.
    1. The `reduce()` method iterates over the filtered numbers.
    2. It accumulates the sum of the remaining numeric values.

4. The final output is `91`, as only the numbers `1` and `90` are summed.
    1. Non-numeric values like `"Pamela"`, `"hello"`, `undefined`, and `null` are excluded from the sum.
    2. The remaining numbers, `1` and `90`, are added to produce the final result.


## Spread Operator ( ... )
The spread operator is used to "spread" or unpack elements of an array (or properties of an object). It allows for concise copying, concatenation, and adding new elements to arrays or objects.

#### Example 1: Copying Arrays
The spread operator can be used to create a shallow copy of an array:
```Javascript
const arr1 = ['a', 2, 'hello', 67849];
const arr2 = [...arr1]; 
console.log(arr2); // Output: ['a', 2, 'hello', 67849]
```
#### Explanation:
We use ...arr1 to copy the elements of arr1 into arr2. This method creates a shallow copy of the original array.

#### Example 2: Adding Elements to a Copied Array
You can copy an array and add new elements to it:
```Javascript
const arr3 = [...arr1, 45, undefined, null];
console.log(arr3); // Output: ['a', 2, 'hello', 67849, 45, undefined, null]
```
#### Explanation:
Here, we are copying arr1 into arr3 and appending additional elements (45, undefined, null).

#### Example 3: Merging Arrays
You can merge two or more arrays easily with the spread operator:
```Javascript
const num1 = [1, 2, 3];
const num2 = [4, 5, 6];
const num3 = [...num1, ...num2];
console.log(num3); // Output: [1, 2, 3, 4, 5, 6]
```

#### Explanation:
We merged two arrays num1 and num2 by spreading their elements into num3.

## Without the Spread Operator (Manual Array Merging)
Before the spread operator, you'd have to manually push elements from one array into another:
```Javascript
let emptyArr = [];

function pushArrVals1() {
    num1.map((value) => emptyArr.push(value));
}

function pushArrVals2() {
    num2.map((value) => emptyArr.push(value));
}

pushArrVals1();
pushArrVals2();
console.log(emptyArr); // Output: [1, 2, 3, 4, 5, 6]

```

#### Explanation: 
1. We create an empty array emptyArr.
    1. The pushArrVals1 function iterates through num1 and pushes its values into emptyArr.
    2. Similarly, pushArrVals2 does the same for num2.

## Unique Keys in Objects
JavaScript objects must have unique keys. If you try to merge two objects with the same key, the later object will overwrite the earlier one for that key.

#### Example: Merging Objects with Duplicate Keys
```Javascript
const objStd1 = {
    username: "Joseph",
    age: 23,
};
const objStd2 = {
    username: "Paul",
};

const objStd3 = { ...objStd1, ...objStd2 };
console.log(objStd3); // Output: { username: 'Paul', age: 23 }
```

#### Explanation: 
Both objStd1 and objStd2 have the key username. When we merge them using the spread operator (...objStd1, ...objStd2), the value for username from objStd2 ("Paul") overwrites the value from objStd1 ("Joseph"), but the age key remains intact.

#### Handling Multiple Values for a Key
If you want to store multiple values for a key, an array is a useful solution:

```Javascript
var obj = {
  key: ["value1", "value2"],
};

for (var i in obj) {
  if (obj[i] instanceof Array) {
    for (var k = 0; k < obj[i].length; k++) {
      console.log(obj[i][k]); // Output: value1, value2
    }
  } else {
    console.log(obj[i]);
  }
}

```

#### Explanation:
1. The object obj stores an array under the key key.
   1. We iterate through the object and check if the value is an array.
   2. If it is, we iterate through the array and print each element. This method allows us to store and access multiple values for a single key.