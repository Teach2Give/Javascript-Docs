# Sets

Javascript sets are a useful way of creating a unique list, which can be mutated, but contains no duplicates. A Set in Javascript is a great way to check if a value exists in a specified list of other values. Javascript sets are useful because they are typically faster than something like Array.includes - so they provide an efficient and optimised way of checking if a value exists in a set of other values.

To create a new set, we use the new Set() constructor:

```Javascript
let mySet = new Set();
```

## Basic Set Operations
It is one thing to initialize a new set, but how do we actually use it? Set has a number of operations, many of which will be familiar if you read my guide on maps. Let’s take a look

## Adding elements to a Set
The Set.add() method is used to add elements to a set:

```Javascript
let mySet = new Set();
mySet.add(5);
console.log(mySet); // Set(1)&nbsp;{5}
```

Sets can contain any data type - so you can add objects, numbers, strings, or anything else which you desire. If you try to add the same value twice, it will only appear in the set once:

```Javascript
let mySet = new Set();
mySet.add(5);
mySet.add(5);
console.log(mySet); // Set(1)&nbsp;{5}
```

## Deleting elements from a Set
To delete a single element from a set in Javascript, you can use the Set.delete() method:

```Javascript
let mySet = new Set();
mySet.add(5);
mySet.delete(5);
console.log(mySet); // Set(0)&nbsp;{}
```

You can also use the Set.clear() method to clear all items from a set:

```Javascript
let mySet = new Set();
mySet.add(5);
mySet.add(10);
mySet.clear();
console.log(mySet); // Set(0)&nbsp;{}
```
## Deleting objects from a Set
Interestingly, objects are still created with separate references, so you can’t delete an object from a set using the Set.delete() method. Trying to do so still results in the object item appearing in the set:

```Javascript
let mySet = new Set();
mySet.add({o: 4});
mySet.delete({o: 4});
console.log(mySet); // Set(1)&nbsp;
```

Instead, if you want to delete an object from a set, you have to loop through the set using forEach or something similar. After finding the element you want to delete, simply delete it as normal:

```Javascript
let mySet = new Set();
mySet.add({o: 4});
mySet.forEach((x) => {
if(x.o == 4) {
mySet.delete(x)
}
});
console.log(mySet); // Set(0)&nbsp;{}
```

## Set keys and entries
Sets in Javascript also have Set.keys() and Set.entries() methods. All sets are essentially a kind of array, so using Set.keys() simply returns an iterable set of keys from that set, as shown below:

```Javascript
let mySet = new Set();
mySet.add(5);
mySet.add(10);
console.log(mySet.keys()); // SetIterator&nbsp;{5, 10}
Set.entries() is quite strange, since as I sort of mentioned, sets don’t really have keys. In Javascript, typically an entries() method returns the key value pairs from a data structure in an array format, like [key, value]. Since sets don’t have keys, Set.entries() just returns the same value for both key and value. The main reason this method exists is to provide consistency with the Map data type:

let mySet = new Set();
mySet.add(5);
mySet.add(10);
let setEntries = mySet.entries();

for(let x of setEntries) {
console.log(x);
// Returns [ 5, 5 ], [ 10, 10 ]
}

```


## Checking Set Membership

The main use case for sets in Javascript is checking membership. This is slightly faster than using something like Array.includes(). To check set membership, you can use the Set.has() method. It returns true, if the set contains the item, and false if it does not:

```Javascript
let mySet = new Set();
mySet.add(5);
mySet.add(10);
mySet.add(20);
console.log(mySet.has(10)); // true
Again, this will not work with objects exactly, since an object has a different reference when checked using has. As such, to check if an object is within a set, you must loop through it and check some value within the object:

let mySet = new Set();
mySet.add({o: 4});
mySet.forEach((x) => {
if(x.o == 4) {
// the object is in the set
}
});
```

## Checking the size of a set
While arrays have .length, sets have .size. To check the size or length of a set, we can’t use .length, like we normally would. Instead, the size of a set is found using .size:

```Javascript
let mySet = new Set();
mySet.add(5);
mySet.add(10);
mySet.add(20);
console.log(mySet.size); // Returns 3
```

## Iterating over a Set

Sets themselves are able to be looped through with a simple for loop:

```Javascript
let mySet = new Set();
mySet.add(5);
mySet.add(10);
mySet.add(20);
for(let x of mySet) {
console.log(x); // Returns 5, 10, 20
}
```

However, sets also come with the forEach() method attached, so you can use that too. Typically for loops are faster, though:

```Javascript
let mySet = new Set();
mySet.add(5);
mySet.add(10);
mySet.add(20);
mySet.forEach(() => {
console.log(x); // Returns 5, 10, 20
}
```
As well as this, sets come with an iterator method attached too. You can access it like shown in the code below, 
and then use next() to iterate through each item in a set.
You may not have seen this notation before, but many data
structures and prototypes contain an iterator method. Here, we access it via mySet[Symbol.iterator]().

```Javascript
let mySet = new Set();
mySet.add(5);
mySet.add(10);
let setIterator = mySet[Symbol.iterator]();

console.log(setIterator.next()); // Returns { value: 5, done: false }
console.log(setIterator.next()); // Returns { value: 10, done: true }

```