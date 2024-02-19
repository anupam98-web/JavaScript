## Closure

A closure is an expression (most commonly, a function) that can have free variables together with an environment that binds those variables (that "closes" the expression)

- The inner function can be accessed only from statements in the outer function.
- The inner function forms a closure: the inner function can use the arguments and variables of the outer function, while the outer function cannot use the arguments and variables of the inner function.

The outer function does not have access to the variables and functions defined inside the inner function. This provides a sort of encapsulation for the variables of the inner function.

Now we konw that inner function form a *closure*.
So you can call the outer function and specify arguments for both the outer and inner function.

```
function outside(x) {
  function inside(y) {
    return x + y;
  }
  return inside;
}

const fnInside = outside(3); // Think of it like: give me a function that adds 3 to whatever you give it
console.log(fnInside(5)); // 8
console.log(outside(3)(5)); // 8
```

# Important  points about closures
We look at above example.
- Notice how x is preserved when inside is returned. 
- A closure must preserve the arguments and variables in all scopes it references. - Since each call provides potentially different arguments, a new closure is created for each call to outside. 
- The memory can be freed only when the returned inside is no longer accessible.

*This is not different from storing references in other objects, but is often less obvious because one does not set the references directly and cannot inspect them.*

Also, since the inner function has access to the scope of the outer function, the variables and functions defined in the outer function will live longer than the duration of the outer function execution, if the inner function manages to survive beyond the life of the outer function. A closure is created when the inner function is somehow made available to any scope outside the outer function.

```// The outer function defines a variable called "name"
const pet = function (name) {
  const getName = function () {
    // The inner function has access to the "name" variable of the outer function
    return name;
  };
  return getName; // Return the inner function, thereby exposing it to outer scopes
};
const myPet = pet("Vivie");

console.log(myPet()); // "Vivie"
```


Name Conflicts
*Priority is given to nested Scope.*
For Example

```function outside() {
  const x = 5;
  function inside(x) {
    return x * 2;
  }
  return inside;
}

console.log(outside()(10)); // 20 (instead of 10)
```
The name conflict happens at the statement return `x * 2` and is between inside's parameter x and outside's variable x. The scope chain here is {inside, outside, global object}. Therefore, inside's x takes precedences over outside's x, and 20 (inside's x) is returned instead of 10 (outside's x).

When there is a name conflict then there is no way to refer to the variable in the outer scope again. (The inner scope variable "overrides" the outer one, until the program exits the inner scope).
