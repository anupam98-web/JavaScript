## Classes

It's good to have understanding of classes in general. It helps us write clean code, understanding design patterns and low level designs.

How it was before
- JavaScript is a prototype-based language — an object's behaviors are specified by its own properties and its prototype's properties

How it's now.
- the addition of classes, the creation of hierarchies of objects and the inheritance of properties and their values are much more in line with other object-oriented languages such as Java.

# Declaring a class
```js
class MyClass {
  // class body...
}

//example
class MyClass {
  // Constructor
  constructor() {
    // Constructor body
  }
  // Instance field
  myField = "foo";
  // Instance method
  myMethod() {
    // myMethod body
  }
  // Static field
  static myStaticField = "bar";
  // Static method
  static myStaticMethod() {
    // myStaticMethod body
  }
  // Static block
  static {
    // Static initialization code
  }
  // Fields, methods, static fields, and static methods all have
  // "private" forms
  #myPrivateField = "bar";
}
```
Constructing a class
- attempting to "call" a class without new will result in an error.

```js
const myInstance = new MyClass();
console.log(myInstance.myField); // 'foo'
myInstance.myMethod();


const myInstance = MyClass(); // TypeError: Class constructor MyClass cannot be invoked without 'new'

```

- Class declaration hoisting
Unlike function declarations, **class declarations are not hoisted** (or, in some interpretations, hoisted but with the temporal dead zone restriction), which means you cannot use a class before it is declared.

# Class expressions

```js
const MyClass = class {
  // Class body...
};

// Class expression with Name.
const MyClass = class MyClassLongerName {
  // Class body. Here MyClass and MyClassLongerName point to the same class.
};
new MyClassLongerName(); // ReferenceError: MyClassLongerName is not defined

```


# Constructor
- In classes, the instance creation is done by the constructor.
- Within a class constructor, the value of this points to the newly created instance. You can assign properties to it, or read existing properties
- **The this value will be automatically returned as the result of new. You are advised to not return any value from the constructor — because if you return a non-primitive value, it will become the value of the new expression, and the value of this is dropped.**

```js
class MyClass {
  constructor() {
    this.myField = "foo";
    return {};
  }
}
console.log(new MyClass().myField); // undefined
```
# Instance Method
```js
class Color {
  constructor(r, g, b) {
    this.values = [r, g, b];
  }
  getRed() {
    return this.values[0];
  }
}

const red = new Color(255, 0, 0);
console.log(red.getRed()); // 255

```
- Without methods, you may be tempted to define the function within the constructor

```js 
class Color {
  constructor(r, g, b) {
    this.values = [r, g, b];
    this.getRed = function () {
      return this.values[0];
    };
  }
}

console.log(new Color().getRed === new Color().getRed); // false

```
- **This also works. However, a problem is that this creates a new function every time a Color instance is created, even when they all do the same thing!**
- In contrast, if you use a method, it will be shared between all instances. A function can be shared between all instances, but still have its behavior differ when different instances call it, because the value of this is different

```js 
class Color {
  constructor(r, g, b) {
    this.values = [r, g, b];
  }
  getRed() {
    return this.values[0];
  }
  setRed(value) {
    this.values[0] = value;
  }
}

const red = new Color(255, 0, 0);
red.setRed(0);
console.log(red.getRed()); // 0; of course, it should be called "black" at this stage!

```
# Private Fields
- A private field is an identifier prefixed with # (the hash symbol)
- There is a philosophy in object-oriented programming called "encapsulation". This means you should not access the underlying implementation of an object, but instead use well-abstracted methods to interact with it.
- So, if you are an implementor of a class, you would want to hide the internal data structure of your instance from your user, both to keep the API clean and to prevent the user's code from breaking when you do some "harmless refactors". In classes, this is done through private fields.

# Few points to remember...
- In JavaScript, classes are mainly an abstraction over the existing prototypical inheritance mechanism — all patterns are convertible to prototype-based inheritance. 
- Classes themselves are normal JavaScript values as well, and have their own prototype chains. 
- In fact, most plain JavaScript functions can be used as constructors — you use the new operator with a constructor function to create a new object.