# JavaScript Strings

Strings are a fundamental data type in JavaScript, used to represent and manipulate text. This guide covers string creation, manipulation, and common operations.

## Table of Contents

1. [Creating Strings](#creating-strings)
2. [String Properties](#string-properties)
3. [String Methods](#string-methods)
4. [String Interpolation](#string-interpolation)
5. [String Immutability](#string-immutability)
6. [Practical Examples](#practical-examples)

## Creating Strings

Strings in JavaScript can be created using single quotes, double quotes, or backticks:

```javascript
let myName = 'Wangui';
let greeting = "Hello, World!";
let message = `Welcome to JavaScript`;
```
## String Properties
Length
The length property returns the number of characters in a string:

```Javascript
let sister = 'Naima';
console.log(sister.length); // 5
```

## String Methods
JavaScript provides numerous built-in methods for string manipulation:

1 : charAt()
Returns the character at a specified index:

```Javascript
console.log(sister.charAt(1)); // 'a'
```
2: concat()
Joins two or more strings:

```Javascript
console.log('Stanley'.concat('Njoroge')); // 'StanleyNjoroge'
console.log('Stanley'.concat(' Njoroge')); // 'Stanley Njoroge'
```

3:includes()
Checks if a string contains a specified substring:
```Javascript
let sent2 = 'Hi am available';
console.log(sent2.includes('hi')); // false
console.log(sent2.includes('Hi')); // true
```

4:indexOf()
Returns the index of the first occurrence of a specified value in a string:
```Javascript
console.log(sister.indexOf('m')); // 3
console.log(sister.indexOf('M')); // -1

```

5:toLowerCase() and toUpperCase()
Convert a string to lowercase or uppercase:
```javaJavascript
let name = 'dAD';
console.log(name.toUpperCase()); // 'DAD'
```

6:split()
Splits a string into an array of substrings:
```Javascript
let catFam = 'cat';
console.log(catFam.split()); // ['cat']
console.log(catFam.split('')); // ['c', 'a', 't']
```

7: substr()
Extracts a part of a string, starting at a specified position and running for a given number of characters:
```Javascript
let sentence = 'Hellowz my name is Juma';
console.log(sentence.substr(2, 5)); // 'llow '
```

8:substring()
Extracts characters from a string between two specified indices:
```Javascript
console.log(sentence.substring(2, 5)); // 'llo'
```

9:trim(), trimStart(), trimEnd()
Remove whitespace from strings:
```Javascript
let sent = '    Hi am available    ';
console.log(sent.trim()); // 'Hi am available'
console.log(sent.trimStart()); // 'Hi am available    '
console.log(sent.trimEnd()); // '    Hi am available'
```

10:String Interpolation
Template literals (backticks) allow for easy string interpolation:
```Javascript
let name = 'Alice';
let age = 30;
console.log(`My name is ${name} and I am ${age} years old.`);
```

## String Immutability
Strings in JavaScript are immutable, meaning their values cannot be changed after creation. Operations that appear to modify a string actually create a new string.

Practical Examples
Palindrome Checker
Here's a function that checks if a string is a palindrome:
```Javascript
function palindrome(string) {
    let revString = string.toLowerCase().split('').reverse().join('');
    if (string.toLowerCase() === revString) {
        return `${string} is a palindrome`;
    }
    return `${string} is not a palindrome`;
}

console.log(palindrome('cat')); // 'cat is not a palindrome'
console.log(palindrome('DAD')); // 'DAD is a palindrome'
```
This function works by:

 - Converting the input string to lowercase
 - Splitting it into an array of characters
 - Reversing the array
 - Joining it back into a string
 - Comparing the reversed string with the original (lowercase) string