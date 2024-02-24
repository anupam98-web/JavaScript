## Object

JavaScript is designed on a simple object-based paradigm. An object is a collection of properties, and a property is an association between a name (or key) and a value. A property's value can be a function, in which case the property is known as a method.

```js
o = {
  a: "foo",
  b: 42,
  c: {},
  1: "number literal property",
  "foo:bar": "string literal property",

  shorthandProperty,

  method(parameters) {
    // …
  },

  get property() {},
  set property(value) {},

  [expression]: "computed property",

  __proto__: prototype,

  ...spreadProperty,
};
```

## Using constructor Function

- Define the object type by writing a constructor function. There is a strong convention, with good reason, to use a capital initial letter.
- Create an instance of the object with new.

```js
function Car(make, model, year) {
  this.make = make;
  this.model = model;
  this.year = year;
}
const myCar = new Car("Eagle", "Talon TSi", 1993);

```

**You can also use the class syntax instead of the function syntax to define a constructor function.**




## Using the Object.create() method
The `Object.create()` method creates an Object. This allow you to choose the proptotype object for the object you want to create, **without having to define a constructor function.**

```js
// Animal properties and method encapsulation
const Animal = {
  type: "Invertebrates", // Default value of properties
  displayType() {
    // Method which will display type of Animal
    console.log(this.type);
  },
};

// Create new animal type called animal1
const animal1 = Object.create(Animal);
animal1.displayType(); // Logs: Invertebrates

// Create new animal type called fish
const fish = Object.create(Animal);
fish.type = "Fishes";
fish.displayType(); // Logs: Fishes

```

- Access the proptery in the object.

```js
const myObj = {};
const str = "myString";
const rand = Math.random();
const anotherObj = {};

// Create additional properties on myObj
myObj.type = "Dot syntax for a key named type";
myObj["date created"] = "This key has a space";
myObj[str] = "This key is in variable str";
myObj[rand] = "A random number is the key here";
myObj[anotherObj] = "This key is object anotherObj";
myObj[""] = "This key is an empty string";

console.log(myObj);
// {
//   type: 'Dot syntax for a key named type',
//   'date created': 'This key has a space',
//   myString: 'This key is in variable str',
//   '0.6398914448618778': 'A random number is the key here',
//   '[object Object]': 'This key is object anotherObj',
//   '': 'This key is an empty string'
// }
console.log(myObj.myString); // 'This key is in variable str'

```
When the key is not found it's give `undefined`.

However, beware of using square brackets to access properties whose names are given by external input. This may make your code susceptible to (object injection attacks[https://github.com/nodesecurity/eslint-plugin-security/blob/main/docs/the-dangers-of-square-bracket-notation.md]).

# Iteration in objects

- `for...in` loops. This method traverses all of the enumerable string properties of an object as well as its prototype chain.
- `Object.keys()`. This method returns an array with only the enumerable own string property names ("keys") in the object myObj, but not those in the prototype chain.
- `Object.getOwnPropertyNames()`. This method returns an array containing all the own string property names in the object myObj, regardless of if they are enumerable or not.

**Deleting Properties**

You can remove a non-inherited property using the delete operator. The following code shows how to remove a property.

```js
// Creates a new object, myobj, with two properties, a and b.
const myobj = new Object();
myobj.a = 5;
myobj.b = 12;

// Removes the a property, leaving myobj with only the b property.
delete myobj.a;
console.log("a" in myobj); // false

```

# Inheritance
All objects in JavaScript inherit from at least one other object. The object being inherited from is known as the prototype, and the inherited properties can be found in the prototype object of the constructor

- You can add a property to all objects created through a certain **constructor** using the `prototype` property. This defines a property that is shared by all objects of the specified type, rather than by just one instance of the object.

- # Defining Method

a method is a property of an object that is a function. Methods are defined the way normal functions are defined, except that they have to be assigned as the property of an object

```js
objectName.methodName = functionName;

const myObj = {
  myMethod: function (params) {
    // do something
  },

  // this works too!
  myOtherMethod(params) {
    // do something else
  },
};

objectName.methodName(params);

```
**Methods are typically defined on the prototype object of the constructor, so that all objects of the same type share the same method**

```js
Car.prototype.displayCar = function () {
  const result = `A Beautiful ${this.year} ${this.make} ${this.model}`;
  console.log(result);
};

car1.displayCar();
car2.displayCar();
```

# this. What is "this"???.........LOL

`this`, that you can use within a method to refer to the current object.

```js
const Manager = {
  name: "Karina",
  age: 27,
  job: "Software Engineer",
};
const Intern = {
  name: "Tyrone",
  age: 21,
  job: "Software Engineer Intern",
};


// notice this.name here. We assign the same function to both the obj.
function sayHi() {
  console.log(`Hello, my name is ${this.name}`);
}

// add sayHi function to both objects
Manager.sayHi = sayHi;
Intern.sayHi = sayHi;

Manager.sayHi(); // Hello, my name is Karina
Intern.sayHi(); // Hello, my name is Tyrone

```

Getter and Setter are in differnt getSet.md.
Please check out from there.

**Objects are a reference type. Two distinct objects are never equal, even if they have the same properties. Only comparing the same object reference with itself yields true.**


```js
// Two variables, two distinct objects with the same properties
const fruit = { name: "apple" };
const fruitbear = { name: "apple" };

fruit == fruitbear; // return false
fruit === fruitbear; // return false

```

```js
// Two variables, a single object
const fruit = { name: "apple" };
const fruitbear = fruit; // Assign fruit object reference to fruitbear

// Here fruit and fruitbear are pointing to same object
fruit == fruitbear; // return true
fruit === fruitbear; // return true

fruit.name = "grape";
console.log(fruitbear); // { name: "grape" }; not { name: "apple" }

```