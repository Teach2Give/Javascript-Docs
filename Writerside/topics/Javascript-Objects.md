# Javascript Objects

JavaScript objects are a fundamental data structure used to store keyed collections of data. They allow you to group related data and functionalities together. In JavaScript, everything that holds data can be considered a data structure, and objects are one of the most versatile and widely used data structures in the language.

## Basics of Objects
Objects in JavaScript are used to store collections of data in the form of key-value pairs. Here’s a breakdown of how objects work:

## Creating and Using Objects
Defining an Object:

```Javascript
var person = {};
person.firstName = 'Emmanuel';
person.secondName = 'Mwendwa';
person.age = 24;
console.log(person); // Outputs: { firstName: 'Emmanuel', secondName: 'Mwendwa', age: 24 }
```
Explanation: An object is created with {}. Properties can be added using dot notation (person.firstName = 'Emmanuel'). The object person now holds three properties: firstName, secondName, and age.

## Properties and Methods
Objects can hold various types of values including strings, numbers, arrays, and even other objects. They can also include functions, which are known as methods when they are part of an object.

Example with Different Data Types:

```Javascript
const DennisInfo = {
fName: 'Dennis', // string
age: 23, // number
marks: [56, 78, 90], // array
govInfo: {
idNumber: 34567890,
location: 'Nairobi'
},
meanGrade: function(meangrade) { // function as a method
return meangrade;
}
};
```
Explanation: The DennisInfo object has various properties including fName (string), age (number), marks (array), govInfo (another object), and meanGrade (function).

## Accessing Object Properties
There are several ways to access data stored in objects:

Dot Notation:
```Javascript
const name = {
firstName: 'Felistus',
secondName: 'Chemutai',
age: 15
};
console.log(name.firstName); // Outputs: Felistus
```

## Bracket Notation:
```Javascript
console.log(name['secondName']); // Outputs: Chemutai
```
Explanation: Bracket notation is useful when property names are dynamic or not valid identifiers.

## Using Object.keys():
```Javascript
console.log(Object.keys(name)); // Outputs: [ 'firstName', 'secondName', 'age' ]
```
Explanation: Object.keys() returns an array of an object’s own enumerable property names. This can be useful for iterating over object properties.

## Arrays of Objects
Arrays can hold multiple objects. Each object can be accessed using array indices.

Example:
```Javascript
const car = [
{ brand: 'Toyota', model: 'Toyota TX' },
{ brand: 'Landrover', model: 'Defender' },
{ brand: 'Lexus', model: 'Lexus X5' }
];

console.log(car); // Outputs the array of car objects
console.log(car[1]); // Outputs: { brand: 'Landrover', model: 'Defender' }
console.log(car[1].model); // Outputs: Defender
```
Explanation: The car array contains three objects, each representing a car with brand and model properties. You can access individual cars using array indices and properties using dot notation.

## Functions as Object Methods
Functions can be defined within objects to perform operations related to that object. These functions are referred to as methods.

Example:
```Javascript
const hero = {
name: 'The Maldarion',
phrase: 'This is the way',
speak: function() {
return this.phrase;
}
};
console.log(hero.speak()); // Outputs: This is the way
```
Explanation: The hero object has a method speak that returns the phrase property of the object. The this keyword refers to the object itself, allowing access to its properties.

## Accessing Object Properties Dynamically
Sometimes, you need to access object properties dynamically. This can be done using bracket notation.

Example:

```Javascript
var obj = {
fname: 'Colin',
sName: 'Osidiana',
age: 21,
key: function(n) {
return this[Object.keys(this)[n]];
}
};
console.log(obj.key(1)); // Outputs: Osidiana
```

Explanation: The key method uses Object.keys() to get an array of property names and access a specific property based on its index.