## Functions

Functions can be decalared in various Ways.
- function declaration

```js
function  function_name(parameter1, parameter2) {

}
```

- function expression
Below function can we anonymous it does not have to have a name.

```js
const square = function (number) {
  return number * number;
};

console.log(square(4)); // 16

```
A name can be provided with a function expression. 
It allows the function to refer to itself, also make it easier to identify the function in a debugger stack traces.
```js
const factorial = function fac(n) {
  return n < 2 ? 1 : n * fac(n - 1);
};

console.log(factorial(3)); // 6

```

- a function can be defined based on a condition. For example, the following function definition defines myFunc only if num equals 0.
 
```js
let myFunc;
if (num === 0) {
  myFunc = function (theObject) {
    theObject.make = "Toyota";
  };
}
```


**Now as we know how to declare the function now it's time to call it.**


The rest parameter syntax allows us to represent an indefinite number of arguments as an array.

the function multiply uses rest parameters to collect arguments from the second one to the end. The function then multiplies these by the first argument.

```js
function multiply(multiplier, ...theArgs) {
  return theArgs.map((x) => multiplier * x);
}

const arr = multiply(2, 1, 2, 3);
console.log(arr); // [2, 4, 6]
```

## Arrow Functions
- An arrow function expression (also called a fat arrow to distinguish from a hypothetical -> syntax in future JavaScript).
- It has a shorter syntax compared to function expressions **and does not have its own this, arguments, super, or new.target. Arrow functions are always anonymous**.
- Two factors influenced the introduction of arrow functions: shorter functions and non-binding of `this`.

```js
// Traditional function expression
function add(a, b) {
    return a + b;
}

// Arrow function
const add = (a, b) => {
    return a + b;
};

```
- Concise Syntax: Arrow functions have a shorter syntax compared to traditional function expressions, making code more concise and readable.

- Implicit Return: If the function body consists of only one expression, the return keyword and curly braces can be omitted. The expression's value will automatically be returned.

- Lexical this Binding: Arrow functions do not have their own this context. Instead, they inherit the this value from the surrounding code (lexical scoping). This behavior can be beneficial in certain situations, especially when dealing with nested functions or callbacks.

- No arguments Object: Arrow functions do not have their own arguments object. If you need access to the arguments passed to the function, you'll need to use rest parameters (...args) instead.

- Cannot Be Used as Constructors: Arrow functions cannot be used as constructors with the new keyword. They lack the prototype property and do not have their own this context.

- Best Practices: Arrow functions are particularly useful for short, one-liner functions, or when you want to maintain the lexical scope of this. However, they may not be suitable for all scenarios, especially when dealing with object methods, prototypes, or constructors.


## Few key points about the functions

- Function are object themselves.
- They can have properties. `.apply`, `.call`, ``.bind``.
- Functions must be in scope when they are called.
- Hoisting is allowed. Ex. we can all function before it's even declare. We can declare the function later.
**Note**: **Hoisting only work with function declarations not with function expressions**

Now Function are object so they have there own scope.
A function has access to it's parent function properties.
But it does not have access to child functions property.


