So when i was writing this I got to know that this whole conditional statements are called in **contorl flow**

So ```if```, ```if else``` statements are very similar to other propgramming languages.

But trick lies in ```Switch``` Statement

A switch statement allows a program to evaluate an expression and attempt to match the expression's value to a case label. If a match is found, the program executes the associated statement.


```js
switch (expression) {
  case label1:
    statements1;
    break;
  case label2:
    statements2;
    break;
  // …
  default:
    statementsDefault;
}

```

**Break** Statement is essential for Switch
It ensure that the only that case block is executed and then exit the switch.

If there's no break;```, all the code after matched case will also be executed.
*Until we another Break statement, it will go on executing till end of the switch.*