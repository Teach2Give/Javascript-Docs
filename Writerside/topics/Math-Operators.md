# Math Operators

# 1. Basic Math Operations
   
## Addition (+): Adds two numbers.

```Javascript
console.log(10 + 10); // 20
```

## Subtraction (-): Subtracts the second number from the first.

```Javascript
console.log(23 - 6); // 17
```
## Multiplication (*): Multiplies two numbers.

```Javascript
console.log(30 * 3); // 90
```
## Division (/): Divides the first number by the second.

```Javascript
console.log(20 / 5); // 4
```
## Modulus (%): Returns the remainder of a division operation.

```Javascript
console.log(9 % 4); // 1
```
## Exponentiation (**): Raises the first number to the power of the second.

```Javascript
console.log(4 ** 2); // 16 (4^2 = 16)
```

## 2. Increment and Decrement Operators
   
## Increment (++): Increases the value of a variable by 1. Can be used in both pre-increment and post-increment forms.

## Post-increment (variable++): Increments after returning the value.

```Javascript
let number = 10;
console.log(number++); // 10 (value before incrementing)
console.log(number);   // 11 (value after incrementing)
```

## Pre-increment (++variable): Increments before returning the value.

```Javascript
let number1 = 8;
console.log(++number1); // 9 (value after incrementing)
Decrement (--): Decreases the value of a variable by 1. Can be used in both pre-decrement and post-decrement forms.
```

## Post-decrement (variable--): Decrements after returning the value.

```Javascript
let num1 = 9;
console.log(num1--); // 9 (value before decrementing)
console.log(num1);   // 8 (value after decrementing)
```

## Pre-decrement (--variable): Decrements before returning the value.
```Javascript
let num2 = 9;
console.log(--num2); // 8 (value after decrementing)
```

## 3. Comparison Operators
   
## Strict Equality (===): Checks if two values are equal and of the same type.

```Javascript
let number3 = '12'; // string
let number4 = 12;   // number
console.log(number3 === number4); // false (different types)
Strict Non-Equality (!==): Checks if two values are not equal or not of the same type.
```

```Javascript
console.log(number3 !== number4); // true (different types)
```

## Loose Equality (==): Checks if two values are equal, performing type conversion if necessary.

```Javascript
console.log(number3 == number4); // true (values are equal after type conversion)
```

## Loose Non-Equality (!=): Checks if two values are not equal, performing type conversion if necessary.

```Javascript
console.log(number3 != number4); // false (values are equal after type conversion)
```

Less Than (<): Checks if the first value is less than the second.
```Javascript
let number5 = 20;
let number6 = 34;
console.log(number5 < number6); // true
```

## Greater Than (>): Checks if the first value is greater than the second.

```Javascript
console.log(number5 > number6); // false
```

## Less Than or Equal To (<=): Checks if the first value is less than or equal to the second.

```Javascript
console.log(number5 <= number6); // true

```

## Greater Than or Equal To (>=): Checks if the first value is greater than or equal to the second.

```Javascript
console.log(number5 >= number6); // false

```
## 4. Logical Operators
   
## AND (&&): Returns true if both conditions are true.

```Javascript
let myAge = 27;

if (myAge > 30 && myAge < 37) {
console.log('I am a millennial');
} else if (myAge > 28 && myAge < 30) {
console.log('I am a Gen Z');
} else {
console.log('I am a minor');
}
```

## OR (||): Returns true if at least one of the conditions is true.

```Javascript
if (myAge < 30 || myAge > 50) {
console.log('Age is either below 30 or above 50');
}
```

## NOT (!): Negates a condition, returning true if the condition is false, and false if the condition is true.

```Javascript
if (!(myAge > 30)) {
console.log('Age is not greater than 30');
}
```

## 5. Additional Math Operations
   
Unary Plus (+): Converts a variable to a number.

```Javascript
let strNumber = '5';
console.log(+strNumber); // 5 (converted to number)
```

## Unary Minus (-): Converts a variable to a negative number or negates a number.

```Javascript
let num = 10;
console.log(-num); // -10

```

Math Object Methods: JavaScript provides the Math object with methods for more complex mathematical operations.

```Javascript
console.log(Math.sqrt(16)); // 4 (square root)
console.log(Math.round(4.7)); // 5 (rounds to nearest integer)
console.log(Math.random()); // Random number between 0 and 1
```
