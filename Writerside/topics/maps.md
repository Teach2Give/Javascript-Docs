# Maps

Maps in JavaScript are a collection of key-value pairs where both the keys and the values can be of any type. They are part of the ECMAScript 2015 (ES6) specification and offer several advantages over traditional objects when it comes to working with key-value pairs. Here’s a comprehensive look at Maps and their functionalities:

## 1. Creating a Map
   To create a new Map, use the new Map() constructor:


```Javascript
let myMap = new Map();
```

## 2. Methods and Properties
   
Maps come with several useful methods and properties:

map.set(key, value): Adds a new key-value pair to the Map. If the key already exists, it updates the value.

```Javascript
myMap.set('fname', 'Alamin');
myMap.set('age', 23);
myMap.set(35, true);
```

map.get(key): Retrieves the value associated with the specified key. Returns undefined if the key does not exist.

```Javascript
console.log(myMap.get('age')); // 23
```
map.has(key): Checks if a key exists in the Map. Returns true if the key exists, otherwise false.

```Javascript
console.log(myMap.has('fname')); // true
```

map.delete(key): Removes the key-value pair associated with the specified key. Returns true if the key was successfully removed, otherwise false.

```Javascript
myMap.delete('age');
```

map.clear(): Removes all key-value pairs from the Map.

```Javascript
myMap.clear();
```

map.size: Returns the number of key-value pairs in the Map.

```Javascript
console.log(myMap.size); // 0 after clearing
```

## 3. Example Usage
   
Here is an example that demonstrates various Map operations:

```Javascript
let myMap = new Map();

// Adding key-value pairs
myMap.set('fname', 'Alamin');
myMap.set('age', 23);
myMap.set(35, true);

console.log(myMap);
// Map(3) { 'fname' => 'Alamin', 'age' => 23, 35 => true }

// Accessing a value
console.log(myMap.get('age')); // 23

// Checking if a key exists
console.log(myMap.has('fname')); // true

// Deleting a key-value pair
myMap.delete('age');
console.log(myMap.has('age')); // false

// Clearing the Map
myMap.clear();
console.log(myMap.size); // 0
```


## 4. Key Types
   
In a Map, the keys can be of any type: strings, numbers, objects, or even other Maps. Unlike objects, which coerce keys to strings, Maps can store keys of any type without coercion.

```Javascript
let map = new Map();
map.set('stringKey', 'value');
map.set(123, 'numberKey');
map.set(true, 'booleanKey');
map.set({}, 'objectKey');
```

## 5. Iteration
   
Maps also support iteration methods, which allow you to traverse the key-value pairs:

 - map.keys(): Returns an iterator for the keys.
 - map.values(): Returns an iterator for the values.
 - map.entries(): Returns an iterator for the key-value pairs.
 - forEach(callback): Executes a provided function once for each key-value pair.

```Javascript
for (let [key, value] of myMap.entries()) {
console.log(`${key}: ${value}`);
```
