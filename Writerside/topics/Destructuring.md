# Destructuring

Destructuring is a feature introduced in ES6 (ECMAScript 2015) that allows you to extract values from arrays or properties from objects into distinct variables. This feature simplifies the process of accessing and working with data structures.

#### syntax
```Javascript
const { prop1, prop2 } = object;
```
````Javascript
const info = {
    fname: 'Dennis',
    sname: 'Muhia',
    idNo: 45678490
};

// Traditional way to access values
console.log(`${info.fname} ${info.sname} ${info.idNo}`); // Dennis Muhia 45678490

// Using destructuring
const { fname: firstName, sname: secondName, idNo: idNumber } = info;
console.log(`${firstName} ${secondName} ${idNumber}`); // Dennis Muhia 45678490
````

#### Explanation:

1. Destructuring Syntax: The curly braces {} are used to extract properties from an object. The variable names inside the braces correspond to the property names in the object.
2. Renaming Variables: You can rename variables during destructuring by using a colon. For example, fname: firstName renames fname to firstName.


## Default values
## 1. Array default destructuring
```Javascript
const [element1 = defaultValue1, element2 = defaultValue2] = array;
```
```Javascript
const numbers = [1, 2];

const [first = 10, second = 20, third = 30] = numbers;

console.log(first);  // 1
console.log(second); // 2
console.log(third);  // 30

```
 - first and second take values from the array [1, 2].
 - third is assigned the default value 30 because it does not exist in the array.

## Using Default Values with undefined Elements:
````Javascript
const numbers = [1, undefined];

const [first, second = 20] = numbers;

console.log(first);  // 1
console.log(second); // 20

````
second is explicitly undefined in the array, so it takes the default value 20.


## 2. Objects default destructuring
```Javascript
const { property1 = defaultValue1, property2 = defaultValue2 } = object;
```
```Javascript
const user = {
    name: 'Alice',
    age: 25
};

const { name, age, country = 'Unknown' } = user;

console.log(name);    // Alice
console.log(age);     // 25
console.log(country); // Unknown
```
 - name and age are extracted from the user object.
 - country is assigned the default value 'Unknown' because it does not exist in the user object.


## Using Default Values with Renaming:
```Javascript
const user = {
    name: 'Alice',
    age: 25
};

const { name: userName, age: userAge, country: userCountry = 'Unknown' } = user;

console.log(userName);    // Alice
console.log(userAge);     // 25
console.log(userCountry); // Unknown
```

## Destructuring Arrays
#### syntax
```Javascript
const [item1, item2] = array;
```
```Javascript
```

```Javascript
const numbers = [1, 2, 3, 4];

// Traditional way to access values
const first = numbers[0];
const second = numbers[1];
console.log(first, second); // 1 2

// Using destructuring
const [first, second] = numbers;
console.log(first, second); // 1 2
```

#### Explanation:

1. Destructuring Syntax: Square brackets [] are used to extract values from an array. The variables are assigned values from the array in the same order.
2. Default Values: You can provide default values if an element doesn’t exis
```Javascript
const [a = 1, b = 2] = [undefined, 3];
console.log(a, b); // 1 3
```
## Nested Destructuring

1. Destructuring Nested Objects in JavaScript
   Destructuring is a convenient feature in JavaScript introduced with ES6 (ECMAScript 2015) that allows you to unpack values from objects and arrays into distinct variables. When dealing with nested objects, destructuring becomes even more powerful by enabling you to access deeply nested properties in a straightforward manner.

```Javascript
const user = {
    name: 'Alice',
    address: {
        city: 'Wonderland',
        zip: 12345
    }
};

// Destructuring nested object
const { name, address: { city, zip } } = user;
console.log(name, city, zip); // Alice Wonderland 12345

```
Detailed  walk through
1. Defining the nested object
```Javascript
const user = {
    name: 'Alice',
    address: {
        city: 'Wonderland',
        zip: 12345
    }
};

```
- **User Object**: An object with the following properties:
    - **name**:
        - Type: String
        - Value: `'Alice'`
    - **address**:
        - An object with the following properties:
            - **city**:
                - Type: String
                - Value: `'Wonderland'`
            - **zip**:
                - Type: Number
                - Value: `12345`

2. Destructuring the Nested Object
```Javascript
const { name, address: { city, zip } } = user; 
```
- **How It Works**:
    - **Outer Object Destructuring**:
        - `{ name, address: { city, zip } }` is used to destructure the `user` object.
    - **name**:
        - This extracts the `name` property from the `user` object and assigns it to a variable named `name`.
    - **address: { city, zip }**:
        - This part is where nested destructuring occurs.
        - `address` is the key in the `user` object that holds another object.
        - `{ city, zip }` destructures the `address` object:
            - `city` and `zip` are extracted from the `address` object within `user`.
            - They are assigned to variables `city` and `zip`, respectively.


3. Logging the values
```Javascript
console.log(name, city, zip); // Alice Wonderland 12345 
```
- **Variables**:
    - **name**:
        - Holds the value: `'Alice'`
    - **city**:
        - Holds the value: `'Wonderland'`
    - **zip**:
        - Holds the value: `12345`

- **Console Output**:
    - When logged to the console, the variables display: `Alice Wonderland 12345`


## Destructuring nested arrays
```Javascript
const numbers = [1, [2, 3], 4];

// Nested destructuring
const [first, [second, third], fourth] = numbers;

console.log(first);  // 1
console.log(second); // 2
console.log(third);  // 3
console.log(fourth); // 4
```
[second, third] destructures the second element of the numbers array, which is itself an array.

## Destructuring in Function Parameters
```Javascript
function processNumbers([first, second, third]) {
    console.log(first, second, third);
}

const numbers = [1, 2, 3];
processNumbers(numbers); // 1 2 3

```
The function processNumbers destructures the array directly in its parameter list.
