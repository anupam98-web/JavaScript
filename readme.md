Hi All

I will adding everything i Know and learn about JavaScript in this Repositery.

Particulary this .md file will contain Generic Info of JavaScript.


Client-side code is code that is run on the user's computer — when a web page is viewed
Server-side code on the other hand is run on the server, then its results are downloaded and displayed in the browser.

| Interpreted | Compiled |
|----------|----------|
| the code is run from top to bottom and the result of running the code is immediately returned.  | the code transformed (compiled) into another form before they are run by the computer.   |
 | The interpreter reads and executes each line of code one at a time. | Before running, the compiler translates all the code into machine language which can be directly executed by the operating system. |
 | Slower | Faster |

JavaScript is a *lightweight interpreted programming language*. The web browser receives the JavaScript code in its original text form and runs the script from that. 
From a technical standpoint, most modern JavaScript interpreters actually use a technique called **just-in-time compiling** to improve performance; the JavaScript source code gets compiled into a faster, binary format while the script is being used, so that it can be run as quickly as possible. 
However, **JavaScript is still considered an interpreted language**, since the compilation is handled at run time, rather than ahead of time.


How do you add JavaScript to your page?
There are two ways to include JavaScript into an HTML document:
1. First method is to include the script tag just before the closing body tag.

```js
<script>
  // JavaScript goes here
</script>
```
2. Second method inculde  the script tag in the head section of the HTML document.

```js
<script src="script.js" defer></script>
```


Guideline Best Practices  for Writing Proper Code:
1. It is bad practice to pollute your HTML with JavaScript, and it is inefficient


One Problem that is seen and not get recognized is *execution of js before the HTML is loaded*.

so to handle above issue we can use the following methods.

1. we can use `window.onload` or `document.addEventListener('DOMContentLoaded')` to fix this.
2.  Another way is to place all scripts at the end of the BODY element so they execute after the HTML has been fully parsed. - But this could cause serious performance issue.
3. We can use `defer` for external js. **It would load the js and execute it only after the HTML is loaded**.
  -  Note : If there are multiple scripts with "defer", they will be **executed sequentially as soon as the HTML is loaded**.
4. Similar to `defer` we another attribute `async`. This will also load the JS asynchronously **but does not guarantee order of execution**.
  - If there is no need for asynchronous loading then we should use `async`. This attribute specifies that the script must be executed asynchronously.
  - Use async attribute if you don't need to block other resources from loading while JS loads.


