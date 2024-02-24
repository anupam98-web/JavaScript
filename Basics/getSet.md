## Getter Setter.

I know just as the name suggest the main use is to **get** the property from an object and **set** the property for an object.

These are function we define in an object. 
Use specific key word for declaratiobn.

Proper defination.
-A getter is a function associated with a property that gets the value of a specific property. A setter is a function associated with a property that sets the value of a specific property. Together, they can indirectly represent the value of a property.

Getters and setters can be either
- defined within object initializers
- added later to any existing object

# defined within object initializers

Within object initializers, getters and setters are defined like regular methods, but prefixed with the keywords get or set. The getter method must not expect a parameter, while the setter method expects exactly one parameter (the new value to set)

```js
const myObj = {
  a: 7,
  get b() {
    return this.a + 1;
  },
  set c(x) {
    this.a = x / 2;
  },
};

console.log(myObj.a); // 7
console.log(myObj.b); // 8, returned from the get b() method
myObj.c = 50; // Calls the set c(x) method
console.log(myObj.a); // 25

```
The myObj object's properties are:

- myObj.a — a number
- myObj.b — a getter that returns myObj.a plus 1
- myObj.c — a setter that sets the value of - myObj.a to half of the value myObj.c is being set to

# added later to any existing object

Getters and setters can also be added to an object at any time after creation using the `Object.defineProperties()` method. This method's first parameter is the object on which you want to define the getter or setter. 
The second parameter is an object whose property names are the getter or setter names, and whose property values are objects for defining the getter or setter functions. 

```js
const myObj = { a: 0 };

Object.defineProperties(myObj, {
  b: {
    get() {
      return this.a + 1;
    },
  },
  c: {
    set(x) {
      this.a = x / 2;
    },
  },
});

myObj.c = 10; // Runs the setter, which assigns 10 / 2 (5) to the 'a' property
console.log(myObj.b); // Runs the getter, which yields a + 1 or 6

```

Note: **If we add new property in myObj which is independent of a,b,c then it will not be affected by the get and set.**


