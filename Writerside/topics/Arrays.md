# Arrays

Arrays in JavaScript are versatile and widely used to store and manipulate ordered collections of values. Here's a summary of key concepts and methods related to JavaScript arrays:

## Arrays Overview
Passed by Reference: Arrays in JavaScript are passed by reference, not by value. This means that when you assign an array to a new variable, both variables point to the same array in memory. Changes to one variable will affect the other.

```Javascript
let dennisInfo = [23, 'Dennis', [56, 78, 91], {idNumber: 34567890, location: 'Nairobi'}, function name() {return grades}];
```
## Accessing and Modifying Arrays
Accessing Elements: Use indices to access elements in an array. Indices start from 0.

```Javascript
dennisInfo[1]); // Outputs: Dennis
```
## Printing the Whole Array: 

Simply use console.log() to view the entire array.

```Javascript
console.log(dennisInfo);
```

## Modifying Elements: 
You can change an element by assigning a new value to a specific index.

```Javascript
dennisInfo[1] = 'Marvin';
console.log(dennisInfo[1]); // Outputs: Marvin
```

## Adding Elements:
Use push() to add elements to the end of the array.

```Javascript
dennisInfo.push('Dedan Kimathi Uni');
console.log(dennisInfo);
```

## Removing Elements: 
Use pop() to remove the last element or shift() to remove the first element.

```Javascript
dennisInfo.pop();
console.log(dennisInfo);

dennisInfo.shift();
console.log(dennisInfo);
```

## array Methods
### Finding Indexes: Use indexOf() to get the index of a particular value in the array.

```Javascript
const alaminInfo = ['Alamin', 'Juma', 45];
alaminInfo.push(33317490);
console.log(alaminInfo.indexOf(33317490)); // Outputs: 3
```

## Joining Arrays: 
Use concat() to join multiple arrays.

```Javascript
const markMwangi = ['Mark', 23456];
const stanley = ['Stanley', 54657];
console.log(markMwangi.concat(stanley));
```
## Joining Array Elements into a String:
Use join() to create a string from array elements, with optional separators.

```Javascript
const months = ['Jan', 'March', 'April', 'June'];
console.log(months.join()); // Outputs: Jan,March,April,June
console.log(months.join('')); // Outputs: JanMarchAprilJune
console.log(months.join(' ')); // Outputs: Jan March April June
```

## Modifying Arrays with splice(): 
Use splice() to remove, replace, or add elements in an array.

```Javascript
const siz = ['Felistus', 'Nelly', 'Perl'];
siz.splice(1, 0, 'Fatma');
console.log(siz); // Outputs: [ 'Felistus', 'Fatma', 'Nelly', 'Perl' ]

siz.splice(1, 2, 'Najma', 'Jane');
console.log(siz); // Outputs: [ 'Felistus', 'Najma', 'Jane', 'Perl' ]

console.log(siz.splice(1)); // Outputs: [ 'Najma', 'Jane', 'Perl' ]
```

## Creating Subarrays with slice():

Use slice() to create a shallow copy of a portion of an array.

```Javascript
const broz = ['Mark', 'Alan', 'Ian', 'Stano'];
console.log(broz.slice(1, 3)); // Outputs: [ 'Alan', 'Ian' ]
```

## Checking for Presence with includes():
Use includes() to check if an array contains a specific value.

```Javascript
console.log(broz.includes('Dj Shiti')); // Outputs: false
```
