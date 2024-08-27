# Object Prototypes

## 1. What is a Prototype?

In JavaScript, every object has a hidden internal property called __proto__, which refers to another object known as its prototype. The prototype itself can have a prototype, forming a chain of objects. This chain is called the prototype chain and is used to look up properties and methods.

## 2. Prototypes and Constructor Functions

Constructor functions are used to create multiple instances of objects with similar properties and methods. Each constructor function has a prototype property. When you create an object using this constructor function, the object inherits properties and methods from the constructor’s prototype.

Example with Constructor Function:

```Javascript
function Car(make, model) {
this.make = make;
this.model = model;
}

// Adding a method to the prototype of Car
Car.prototype.startEngine = function() {
console.log('Engine started');
};

// Creating an instance of Car
var myCar = new Car('Toyota', 'Camry');

console.log(myCar.make); // Toyota
console.log(myCar.model); // Camry
myCar.startEngine(); // Engine started
```

In this example:
 - Car.prototype is an object that has a method startEngine.
 - myCar inherits startEngine from Car.prototype.

## 3. Prototypes in ES6 Classes

With ES6 classes, you can define prototypes using a class-based syntax, which is syntactic sugar over JavaScript's prototype-based inheritance.

Example with ES6 Class:

```Javascript
class Car {
constructor(make, model) {
this.make = make;
this.model = model;
}

startEngine() {
console.log('Engine started');
}
}

let myCar = new Car('Toyota', 'Camry');

console.log(myCar.make); // Toyota
console.log(myCar.model); // Camry
myCar.startEngine(); // Engine started
```

In this example:

 - Car class has a startEngine method defined directly in its prototype.
 - Instances created from Car inherit startEngine from the Car class’s prototype.


## 4. Object.create()

Object.create() is a method that creates a new object with a specified prototype object. This method allows you to create an object with a custom prototype.

Example with Object.create():

```Javascript
let animal = {
eat() {
console.log('Eating');
}
};

let dog = Object.create(animal);
dog.bark = function() {
console.log('Barking');
};

dog.eat(); // Eating (inherited from animal)
dog.bark(); // Barking (own method)
```

In this example:

 - dog inherits the eat method from animal.
 - dog has its own method bark.

## 5. Property Lookup and Prototypes

When you try to access a property on an object, JavaScript first looks for that property on the object itself. If it’s not found, JavaScript looks up the prototype chain until it finds the property or reaches the end of the chain (where __proto__ is null).

Example of Property Lookup:
```Javascript
function Animal() {
this.type = 'Unknown';
}

Animal.prototype.sound = 'Generic sound';

let dog = new Animal();
dog.type = 'Dog';

console.log(dog.type); // Dog (found on the object itself)
console.log(dog.sound); // Generic sound (inherited from Animal.prototype)
```

## 6. Modifying Prototypes

You can add or modify properties and methods on an object's prototype at any time, and those changes will be reflected in all objects inheriting from that prototype.

Example of Modifying Prototypes:
```Javascript
function Animal(name) {
this.name = name;
}

Animal.prototype.sayHello = function() {
console.log(`Hello, I'm ${this.name}`);
};

let cat = new Animal('Whiskers');
cat.sayHello(); // Hello, I'm Whiskers

// Modifying prototype
Animal.prototype.sayHello = function() {
console.log(`Hi, I'm ${this.name}`);
};

let dog = new Animal('Rover');
cat.sayHello(); // Hi, I'm Whiskers
dog.sayHello(); // Hi, I'm Rover
```

## 7. Prototypes and Inheritance

Prototypes are fundamental to JavaScript’s inheritance model. You can create inheritance hierarchies using prototypes. For example, if you have a base class Animal and a derived class Dog, you can set up inheritance so that Dog inherits from Animal.

Example of Prototypal Inheritance:

````javascript
function Animal(name) {
this.name = name;
}

Animal.prototype.makeSound = function() {
console.log('Some generic sound');
};

function Dog(name, breed) {
Animal.call(this, name); // Call Animal constructor
this.breed = breed;
}

// Set up inheritance
Dog.prototype = Object.create(Animal.prototype);
Dog.prototype.constructor = Dog;

Dog.prototype.bark = function() {
console.log('Woof');
};

let myDog = new Dog('Buddy', 'Golden Retriever');
myDog.makeSound(); // Some generic sound (inherited from Animal)
myDog.bark(); // Woof (own method)
````

In this example:

 - Dog inherits from Animal through the prototype chain.
 - Dog has its own method bark and inherits makeSound from Animal.

## 8. Prototype Chain and Object Methods

The prototype chain is used when JavaScript looks for methods and properties. Some built-in methods like toString and hasOwnProperty are inherited from Object.prototype, which is the root prototype.

Example:
```Javascript
let obj = {};
console.log(obj.toString()); // [object Object] (inherited from Object.prototype)
console.log(obj.hasOwnProperty('toString')); // false (toString is inherited, not an own property)
```

Summary
 - Prototype: An object that is used as a fallback source for properties and methods.
 - Prototype Chain: The chain of prototypes used to look up properties.
 - Constructor Function and ES6 Classes: Mechanisms to create objects with shared methods through prototypes.
 - Object.create(): Creates a new object with a specified prototype.
 - Property Lookup: JavaScript first checks the object itself and then the prototype chain.
 - Inheritance: Objects can inherit properties and methods through prototypes.