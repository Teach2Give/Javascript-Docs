# JavaScript Iterations

Iteration in JavaScript refers to the process of repeatedly executing a block of code. JavaScript offers several types of loops to facilitate this, each suited to different use cases. Here, we'll explore the key types of loops, including their syntax and practical examples.

## 1. The `while` Loop

The `while` loop executes a block of code as long as a specified condition evaluates to `true`. The syntax is:

```javascript
while (condition) {
  // code to be executed
}

let x = 0;
while (x < 10) {
  console.log(x); // Outputs numbers from 0 to 9
  x++;
}
console.log("The program has been stopped"); // Executes after x is no longer less than 10
```

## 2. The do...while Loop
The do...while loop is similar to the while loop, but it guarantees that the code block is executed at least once before the condition is tested. The syntax is:

```Javascript
do {
  // code to be executed
} while (condition);

let actualPassword = "pa$$w0rd";
let myInputPassword;
do {
  let passwordInputValue = prompt("Enter a password");
  myInputPassword = passwordInputValue;
} while (myInputPassword !== actualPassword);
alert("Correct password");
```

## 3. The for Loop
The for loop is used when you know in advance how many times you want to execute a block of code. The syntax is:

```Javascript
for (initialization; condition; increment) {
  // code to be executed
}

const marks = [12, 34, 45, 56, 78, 79];
console.log('The length of the array is ', marks.length);

for (let index = 0; index < marks.length; index++) {
  console.log(marks[index]); // Outputs all values in the marks array
  if (index >= 5) {
    console.log('The program will break if index is greater or equal to 5');
    break; // Exits the loop if index is 5 or more
  }
}

```

## 4. The for...in Loop
The for...in loop is used to iterate over the enumerable properties of an object. The syntax is:

```Javascript
for (variable in object) {
  // code to be executed
}

const person = {
  name: "GUVI",
  age: 10,
  city: "Chennai, Tamil Nadu"
};

for (let key in person) {
  console.log(`${key}: ${person[key]}`);
}

```

## 5. The for...of Loop
The for...of loop is used to iterate over iterable objects such as arrays, strings, and other built-in iterable objects. The syntax is:

```Javascript
for (variable of iterable) {
  // code to be executed
}

const languages = ["JavaScript", "Python", "HTML"];

for (let lang of languages) {
  console.log(lang); // Outputs each language in the array
}

```

## 6. Labeled Statements
Labeled statements provide a way to label a loop or a block of code, allowing you to break or continue out of multiple nested loops. The syntax is:
```Javascript
label: statement

outerLoop: for (let i = 0; i < 5; i++) {
  innerLoop: for (let j = 0; j < 5; j++) {
    if (i === 2 && j === 2) {
      break outerLoop; // Breaks out of the outer loop
    }
    console.log(`i = ${i}, j = ${j}`);
  }
}

```

## 7. The break Statement
The break statement exits a loop or switch statement prematurely. It is used when you need to stop the execution of the loop before the condition is false.

```Javascript
for (let i = 0; i < 7; i++) {
  if (i === 5) {
    break; // Exits the loop when i is 5
  }
  console.log(i); // Outputs values from 0 to 4
}

```

## 8. The continue Statement
The continue statement skips the current iteration of a loop and proceeds to the next iteration. It does not terminate the loop but skips the remaining code for the current iteration.

```Javascript
for (let i = 0; i < 10; i++) {
  if (i === 9) {
    continue; // Skips the iteration when i is 9
  }
  console.log(i); // Outputs values from 0 to 8
}

```

## Best Practices for Using Loops
 - Use Meaningful Variable Names: Choose variable names that clearly describe their purpose.
 - Initialize Variables Outside the Loop: Avoid unnecessary reinitialization inside the loop.
 - Choose the Right Loop: Use the loop that best fits the problem (e.g., for for known iterations, while for unknown).
 - Avoid Infinite Loops: Ensure loops have an appropriate exit condition.
 - Minimize Code Inside Loops: Keep the code inside loops concise and move complex operations outside if possible.
 - Use break and continue Judiciously: Use them sparingly to avoid reducing code readability.


## Common Mistakes to Avoid
 - Forgetting to Update Loop Control Variables: This can cause infinite loops or incorrect results.
 - Using the Wrong Loop Type: This can lead to unnecessary complexity or inefficiency.
 - Modifying Iterable Objects in for...of Loops: This can lead to unexpected behavior.
 - Not Using Curly Braces for Single-Line Blocks: Always use curly braces to avoid ambiguity.
 - Not Initializing Loop Control Variables: Always initialize before using them in a loop.