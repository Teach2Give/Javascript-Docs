# JavaScript Conditionals

Conditionals in JavaScript are fundamental for controlling the flow of a program based on certain conditions. This document will cover basic conditional statements, including `if`, `else`, `else if`, and the ternary operator.

## Basic `if` Statement

The `if` statement evaluates a condition and executes a block of code if the condition is true. If the condition is false, the block is skipped.

### Example

```javascript
let showering = true;
if (showering) {
    alert('You are a good boy');
}
```
## Explanation of Conditionals

### `if` Statement

**Explanation:** The `if` statement checks if `showering` is true. Since it is, the alert box displays "You are a good boy".

```javascript
let showering = true;
if (showering) {
    alert('You are a good boy');
}
```

### Common Issue: No `else` Block

If the condition evaluates to false, the code block inside the `if` statement is not executed, and nothing happens.

```javascript
let eating = false;
if (eating) {
    alert('You are hungry');
}
```
Explanation: Since eating is false, the alert does not appear, and nothing happens.

Using else for Alternative Actions
The else statement provides an alternative block of code to execute when the if condition is false.

```javascript
let hasID = true;
if (hasID) {
alert('Enter the library');
} else {
alert('Access denied');
}
```
Explanation: Since hasID is true, the first alert box appears with the message "Enter the library". If hasID were false, the alert box with "Access denied" would appear.

Using else if for Multiple Conditions
To handle multiple conditions, you can use else if to check additional conditions if the initial if condition is false.

```javascript
let marks = 0;
let grade = '';

function myGrade(marks) {
if (marks > 89) {
grade = 'A';
} else if (marks > 70) {
grade = 'B';
} else if (marks > 50) {
grade = 'C';
} else if (marks > 30) {
grade = 'D';
} else {
grade = 'E';
}
return grade;
}

console.log(myGrade(56)); // Outputs: C
```

Explanation: The myGrade function determines a grade based on the value of marks. It checks conditions in sequence and returns the corresponding grade.

## Ternary Operator (Conditional Operator)
The ternary operator provides a shorthand way to perform a conditional check. It evaluates a condition and returns one of two values based on whether the condition is true or false.

Syntax:

```Javascript
let result = condition ? value1 : value2;

// Example:
let age = 20;
let allowedAccess = (age > 18) ? 'Allowed' : 'Not allowed';
console.log(allowedAccess); // Outputs: Allowed
```
Explanation: The ternary operator checks if age is greater than 18. If true, it assigns 'Allowed' to allowedAccess. Otherwise, it assigns 'Not allowed'.