## Iteration.

There are many kind of iteration methods in JS.
Sometimes it become confusing.

Basic Iteration



```js
for (initialization; condition; afterthought)
  statement


const divs = document.getElementsByTagName("div");
for (let i = 0, div; (div = divs[i]); i++) {
  /* Process div in some way */
}
```


When i was going through loops i came across

`break` and `break label`. The Same goes for `continue`, but with a label.
So there is very thin line between them.

So , `break label` is used to exit out of a specific loop. It will not break the whole code flow. And exit out of the labeled one.
I know this is confusing. And totally irrelavnt.

but let me put it through code.

|
```js
let x = 0;
let z = 0;

labelCancelLoops: while (x < 2) {
  console.log("Outer loops:", x);
  x += 1;
  z = 1;
  while (true) {
    console.log("Inner loops:", z);
    z += 1;
    if (z === 2) {
      break;
    } else if (z === 10) {
      break;
    }
  }
}```
`|`
```js
let x = 0;
let z = 0;

labelCancelLoops: while (x < 2) {
  console.log("Outer loops:", x);
  x += 1;
  z = 1;
  while (true) {
    console.log("Inner loops:", z);
    z += 1;
    if (z === 2) {
      break labelCancelLoops;
    } else if (z === 10) {
      break;
    }
  }
}```
`|`
`|`
`Outer loops: 0
Inner loops: 1
Outer loops: 1
Inner loops: 1
`
`|`
`Outer loops: 0
Inner loops: 1
`
`|`

