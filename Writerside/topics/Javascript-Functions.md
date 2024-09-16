# Javascript Functions
Definition: A function is a reusable block of code designed to perform a specific task. 
It can be defined using the function keyword and can be called whenever needed.

Creating a Function
```Javascript
function fetchSalesData() {
// code to fetch sales data
}
```

## Components of a Function
 - Function Name: Descriptive of the functionality. E.g., fetchSalesData.
 - Parameters (Arguments): Variables passed into the function to provide inputs. E.g., function average(marks).
 - Return Statement: Used to return a value from the function. E.g., return average

 - inside the paranthesis {} you put your code that needs to be executed for that functionality
```Javascript
const sales = require("./data.json")
function fecthSales() {
    // this is where our code will go
    console.log(sales)
}
 ```


## Creating a basic functions
```Javascript
function fetchSales() {
    const sales = require("./data.json");
    console.log(sales);
}
// every function needs to be called into the stack (call stack) to actually await execution
// they follow the LIFO - flow

fecthSales()

```
 - Explanation: This function imports sales data from a JSON file and logs it to the console.

Function Execution and the Call Stack
![](callstack.png)

1. What is the Call Stack?
   The Call Stack is a stack data structure that keeps track of function calls in JavaScript. It operates on a Last In, First Out (LIFO) principle, meaning that the last function called is the first one to finish executing and return.

2. How Does Function Execution Work?
   Here’s a step-by-step breakdown of how function execution occurs:

Function Declaration: When a function is defined, it is not immediately executed. It is merely declared and stored in memory.

Function Call: When a function is called, a new stack frame is created for that function and pushed onto the Call Stack.

Execution: The JavaScript engine executes the code within the function. If the function calls another function, a new frame is pushed onto the Call Stack for the called function.

Return: Once a function completes its execution, its stack frame is popped off the Call Stack, and control returns to the calling function.

Completion: The execution of the top function in the Call Stack is completed, and control moves to the next function in the stack, if any.

## code example of call stack execution
```Javascript
function one() {
    two();
}

function two() {
    three();
}

function three() {
    console.trace("Call Stack");
}

```
 - Function one() calls two(), which in turn calls three().
 - three() triggers a console.trace("Call Stack"), which logs the current state of the call stack.

## Call Stack Execution Step-by-Step:
 - Initial State: The call stack is empty before any function is called.

 - Step 1 - one() is called: When one() is invoked, a stack frame for one() is pushed onto the call stack.

  Call Stack: [one()]
 - Step 2 - two() is called inside one(): Inside one(), the function two() is called, which pushes a stack frame for two() onto the call stack, above one().

  Call Stack: [one(), two()]
 - Step 3 - three() is called inside two(): Inside two(), the function three() is called, and a stack frame for three() is pushed onto the call stack, above two() and one().

  Call Stack: [one(), two(), three()]
 - Step 4 - console.trace() inside three(): The console.trace() logs the current call stack. At this moment, the stack includes the following:

  Call Stack: [one(), two(), three()] After logging the trace, three() finishes execution and is popped off the stack.
 - Step 5 - Return from three() to two(): Once three() finishes, control goes back to two(), which completes execution. The two() frame is popped from the call stack.

  Call Stack: [one()]
 - Step 6 - Return from two() to one(): Finally, one() finishes execution, and its frame is popped from the stack, leaving the call stack empty again.

  Call Stack: []
  

## Function with Return Values
 - Purpose: To return a value from a function and terminate its execution.
```Javascript
/// syntax of a simple return on a function
function myFunctionality(argument) {
    return argument
}
 ```

```Javascript
//some time a function may have a reurn value
// we define a return value using a return keyword
// its used to return the output needed for that function
// an example is we create a function that takes all your marks and return their avarage or total

// also a function can contain an argument - that is a representation of the data type to be passed as an input later on
// when that function is called
// the argument is basically used to calculate the output needed isnide that function
//the argument can be callled anything, but be carefull to name is descriptive words
// dont call it coe, instead if its marks you can call that way

function average(marks) {
    let total = 0;
    for (let markIndex = 0; markIndex < marks.length; markIndex++) {
        total += marks[markIndex];
    }
    let average = total / marks.length;
    return average;
}
const myMarks = [45, 57, 78, 89, 34];
console.log(average(myMarks), "is your average mark from normal function");
```
 - Explanation: Computes the average of an array of marks and returns it.

## JavaScript Library Functions
 - JavaScript provides built-in functions and methods in its standard library.

```Javascript
let squareRoot = Math.sqrt(4); // Square root of 4
console.log("Square Root of 4 is", squareRoot); // Output: 2

let power = Math.pow(2, 3); // 2 raised to the power 3
console.log("2 to the power of 3 is", power); // Output: 8

let band = "Iron Maiden";
let bandUpper = band.toUpperCase(); // Convert to uppercase
console.log(`Favorite Band: ${bandUpper}`); // Output: IRON MAIDEN
```



## Functions parameters

1. Default Parameters
 - Default parameters allow you to set a default value for a function's parameter if no argument is passed when calling the function. This ensures that the function still works even if it's missing some arguments.

Why useful? Sometimes, you want to ensure that your function behaves a certain way even if not all inputs are provided.

```Javascript
function greet(name = "Guest") {
    return `Hello, ${name}!`;
}

console.log(greet());         
  // "Hello, Guest!"
console.log(greet("Elvis"));  
  // "Hello, Elvis!"
```
 - If the caller doesn’t pass a name when calling greet(), it uses the default "Guest". But if an argument is passed, that value replaces the default.

When would you use this?
 - When writing functions that don't always require a specific input, but you want to provide a sensible fallback. 
 - For example, a price calculator might default to calculating for a single item if no quantity is passed.

```Javascript
function calculatePrice(quantity = 1, pricePerUnit) {
    return quantity * pricePerUnit;
}

console.log(calculatePrice(undefined, 100));  // 100
console.log(calculatePrice(3, 100));          // 300
```
 - Here, we use undefined to trigger the default quantity of 1.


2. Rest Parameters
    - Rest parameters allow you to pass an indefinite number of arguments as an array to a function. This is helpful when you don’t know how many arguments the function will need to handle.

## Syntax
```Javascript
function sum(...numbers) {
    return numbers.reduce((acc, num) => acc + num, 0);
}

console.log(sum(1, 2, 3));        // 6
console.log(sum(4, 5, 6, 7, 8));  // 30
```
 - The ...numbers syntax collects all arguments into an array, making it easy to manipulate.

Why is this useful?
 - Imagine you have a function that can accept any number of items—like adding up scores, prices, or any other variable data set. Rest parameters provide flexibility without requiring you to define multiple function signatures.

```Javascript
function joinWords(separator, ...words) {
    return words.join(separator);
}

console.log(joinWords("-", "apple", "banana", "cherry"));  // "apple-banana-cherry"

```
 - The first parameter is a separator, and all subsequent parameters (...words) are joined together.

3. Destructuring Assignment
    - Destructuring assignment allows you to unpack values from arrays or properties from objects into distinct variables. This makes it easier to extract data from complex structures.

Array Destructuring:
```Javascript
const fruits = ["apple", "banana", "cherry"];
const [first, second] = fruits;

console.log(first);  // "apple"
console.log(second); // "banana"
```
 - You can pull values directly from an array into variables in one line.

Object Destructuring:
```Javascript
const user = { name: "Elvis", age: 25, location: "Kenya" };
const { name, location } = user;

console.log(name);     // "Elvis"
console.log(location); // "Kenya"
```
 - With objects, you extract properties by matching variable names to property names.

Using Destructuring with Functions:
 - Destructuring can also be used in function parameters for more readable code.

```Javascript
function displayUser({ name, age }) {
    console.log(`${name} is ${age} years old.`);
}

const user = { name: "Elvis", age: 25 };
displayUser(user);  // "Elvis is 25 years old."
```

 - Here, the function immediately pulls out the name and age properties from the user object passed as an argument.

Bringing It All Together
 - By combining default parameters, rest parameters, and destructuring, you can create flexible and powerful functions:
```Javascript
 function createUserProfile({ name = "Anonymous", age = 18, ...details }) {
   console.log(`${name} is ${age} years old.`);
   console.log("Additional Details:", details);
}

const user = {
   name: "Elvis",
   age: 25,
   location: "Kenya",
   profession: "Developer"
};

createUserProfile(user);  
// Output:
// Elvis is 25 years old.
// Additional Details: { location: 'Kenya', profession: 'Developer' } 
 ```

 - Default parameters ensure the function always has values to work with.
 - Rest parameters handle any extra properties (details).
 - Destructuring makes it easy to extract only what you need from the object.

## Other types of functions in Javascript

Arrow Functions (ES6)
```text
Syntax: (parameters) => { code }
```

```Javascript
const averageArrowFn = (marks) => {
    let total = 0;
    for (let markIndex = 0; markIndex < marks.length; markIndex++) {
        total += marks[markIndex];
    }
    let average = total / marks.length;
    return average;
}
console.log(averageArrowFn(myMarks), "is your average mark from arrow function");
```

 - Arrow Function with Immediate Return
```text
Syntax: (parameters) => expression
```
```Javascript
const areaCircle = (radius) => (
    console.log(radius * radius * 3.14, "area of circle of radius", radius)
);
areaCircle(7);

// Note: If the function body is a single expression, you can omit curly braces {} and return.

```

Immediately Invoked Function Expressions (IIFE)
 - An Immediately Invoked Function Expression (IIFE) is a design pattern in JavaScript that allows you to execute a function as soon as it is defined. The primary purpose of an IIFE is to create a new scope, thus avoiding the pollution of the global namespace and providing a way to encapsulate variables and functions.

## Syntax
```Javascript
// An IIFE is defined using function expressions and is immediately invoked using parentheses.
(function() {
  // Code to be executed immediately
})();

// Alternatively, you might see it with a named function expression:

(function namedFunction() {
  // Code to be executed immediately
})();

```

## How It Works
 - Function Expression: The function is defined within parentheses (), which turns the function declaration into a function expression. This prevents the function from being hoisted or treated as a declaration.

 - Immediate Invocation: The function expression is immediately executed by following it with another pair of parentheses ().

## Purpose and Benefits
 - Encapsulation: IIFEs help encapsulate code and avoid polluting the global scope. Variables and functions defined within an IIFE are not accessible from the outside, which helps prevent conflicts and potential bugs in larger codebases.

 - Avoiding Variable Hoisting Issues: By using IIFEs, you avoid issues related to variable hoisting. Variables declared inside an IIFE are local to that function and are not accessible from the outside.

 - Module Pattern: IIFEs were commonly used to create modules before ES6 introduced native modules. They allow you to create private variables and expose only specific parts of your code.

Here’s a more advanced example showing how IIFEs can encapsulate variables:
```Javascript
var counter = (function() {
// private variable
  var count = 0; 

  return {
    increment: function() {
      count++;
      console.log(count);
    },
    decrement: function() {
      count--;
      console.log(count);
    }
  };
})();

counter.increment(); 
// Output: 1
counter.increment(); 
// Output: 2
counter.decrement(); 
// Output: 1

// count is not accessible from outside
console.log(count); 
// ReferenceError: count is not defined

```

Explanation:
 - The IIFE creates a private scope with the count variable.
 - It returns an object with methods to manipulate the count variable.
 - The count variable is not accessible from the outside, providing encapsulation and protecting the internal state.

## MongoDB Integration with Node.js Using IIFE
A more practical use case - encapsulating database operations
 - Using an Immediately Invoked Function Expression (IIFE) in the context of MongoDB integration with Node.js can be quite beneficial. IIFEs provide a way to encapsulate and immediately execute code, which can be useful for tasks like performing operations on a database without polluting the global scope. Here's how you can use IIFEs effectively in your MongoDB operations:

1. Connecting to MongoDB
```Javascript
const { MongoClient } = require("mongodb");

// MongoDB connection string
const uri = "mongodb://localhost:27017/my_blogs";

// Connect to MongoDB
const client = new MongoClient(uri);
```
2. Performing Operations with an IIFE
 - Instead of having functions that are defined and then called separately, you can use an IIFE to immediately connect to the database, perform operations, and then close the connection. This helps in managing scope and ensuring that the database connection is handled efficiently.
```Javascript
(async function performMongoDBOperations() {
    try {
        // Connect to MongoDB
        await client.connect();
        console.log("Connected to DB");

        // Access the database and collection
        const database = client.db("my_blogs");
        const collection = database.collection("users");

        // Query: Find documents where age > 30
        const query = { age: { $gt: 30 } };
        const cursor = collection.find(query);
        await cursor.forEach(document => {
            console.log('Found the document:', document);
        });

        // Query: Find documents where hobbies include 'gaming'
        const queryArr = { hobbies: 'gaming' };
        const cursorArr = collection.find(queryArr);
        await cursorArr.forEach(docs => {
            console.log('Found all docs where gaming is a hobby', docs);
        });

        // Query with Logical Operators
        const queryLogical = {
            $or: [
                { age: { $gt: 30 } },  // Find documents where age is > 30
                { hobbies: 'reading' } // or documents where 'reading' is a hobby
            ]
        };
        const cursorLogical = collection.find(queryLogical);
        await cursorLogical.forEach(docs => {
            console.log('Found docs where reading is a hobby', docs);
        });
    } catch (error) {
        console.error('Error finding documents:', error);
    } finally {
        // Ensure the client is closed even if an error occurs
        await client.close();
        console.log('Disconnected from MongoDB');
    }
})();

```

Explanation:

 - Encapsulation: The entire database operation is encapsulated within the IIFE. This prevents any accidental pollution of the global scope with variables or functions specific to this operation.

 - Immediate Execution: The IIFE ensures that the code is executed immediately after its definition. This is particularly useful for scripts that should run once, like a database operation script.

 - Error Handling: The try...catch...finally structure is used within the IIFE to handle errors gracefully and ensure that the MongoDB client is properly closed, even if an error occurs.