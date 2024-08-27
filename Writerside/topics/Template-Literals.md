# Template Literals

### Overview

Template literals, enclosed by backticks (`` ` ``), provide a more flexible and readable way to work with strings. They support multi-line strings and string interpolation, making it easier to include variables and expressions within strings.

### Basic Syntax

**Traditional String Concatenation (Before ES6):**

```Javascript
const fname = "Dan";
const sname = "Kitheka";
console.log("Hello " + fname + " " + sname); // Output: Hello Dan Kitheka

```
## Template Literals (ES6)

```Javascript
const fname = "Dan";
const sname = "Kitheka";
console.log(`Hello ${fname} ${sname}`); // Output: Hello Dan Kitheka

```

### Explanation

- Template literals use backticks (`` ` ``) instead of quotes.
- Expressions and variables inside `${}` are evaluated and interpolated directly into the string.

### Multi-Line Strings

- Template literals make it straightforward to create multi-line strings without needing to use escape characters or concatenation.

#### Example:

```Javascript
const message = `Hello,
This is a multi-line string
using template literals.`;
console.log(message);

```

```Javascript
const message = `Hello,
This is a multi-line string
using template literals.`;
console.log(message);

[//]: # (Hello,)

[//]: # (This is a multi-line string)

[//]: # (using template literals.)

```

### String Interpolation

- You can embed expressions and variables inside template literals, allowing for dynamic string creation.

#### Example:

```Javascript
const price = 19.99;
const discount = 0.2;
const finalPrice = `The final price after discount is $${price - (price * discount)}`;
console.log(finalPrice); // Output: The final price after discount is $15.99

```

### Tagged Templates

- Tagged templates allow you to parse template literals with a function. This feature is useful for custom string processing or building complex string structures.

#### Example:

```Javascript
function highlight(strings, ...values) {
    return strings.reduce((result, string, i) => 
        `${result}<strong>${values[i - 1]}</strong>${string}`
    );
}

const name = "Dan";
const age = 30;
const message = highlight`Name: ${name}, Age: ${age}`;
console.log(message); // Output: Name: <strong>Dan</strong>, Age: <strong>30</strong>

```

### Explanation

- `highlight` is a tag function that processes the template literal and returns a new string.

### Using Template Literals in HTML

- Template literals are particularly useful for dynamically generating HTML content.

#### Example:

```Javascript
const people = [
  { name: "Alberto", age: 27 },
  { name: "Maria", age: 30 },
  { name: "John", age: 25 }
];

const markup = `
<ul>
    ${people.map(person => `<li>${person.name}, Age: ${person.age}</li>`).join('')}
</ul>
`;

console.log(markup);
// Output:
// <ul>
//     <li>Alberto, Age: 27</li>
//     <li>Maria, Age: 30</li>
//     <li>John, Age: 25</li>
// </ul>

```

### Explanation

- `people.map(person => <li>${person.name}, Age: ${person.age}</li>)` generates a list item for each person.
- `.join('')` is used to concatenate the list items into a single string.

### Conditional Expressions

- Template literals can also be used for conditional expressions within the string.

#### Example:

```Javascript
const isDiscounted = false;
const getPrice = () => isDiscounted ? `Discounted price: $10` : `Regular price: $20`;
console.log(getPrice()); // Output: Regular price: $20

```

### Explanation

- The ternary operator is used inside the template literal to choose between two different strings based on the `isDiscounted` condition.

### Template Literals with React (JSX)

- In frameworks like React, template literals are useful for embedding dynamic content in JSX.

#### Example:

```Javascript
const isAdmin = true;

function renderPage() {
    return isAdmin ? `<div>Page for Admin</div>` : `<div>Page Not Allowed</div>`;
}

console.log(renderPage()); // Output: <div>Page for Admin</div>

```

### Explanation:

 - The isAdmin variable determines which content is returned as a string.
