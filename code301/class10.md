[Home](README.md)

<br>

# In memory storage


<br>

## Readings from [The JavaScript Call Stack - What It Is and Why It's Necessary](https://www.freecodecamp.org/news/understanding-the-javascript-call-stack-861e41ae61d4/)

<br>

### JavaScript Engine

<br>

> The JavaScript engine (which is found in a hosting environment like the browser), is a single-threaded interpreter comprising of a heap and a single call stack. The browser provides web APIs like the DOM, AJAX, and Timers.

<br>

### What is Call Stack?

<br>

- The call stack is primarily used for function invocation (call). Since the call stack is single, function(s) execution, is done, one at a time, from top to bottom. It means the call stack is synchronous.

- In Asynchronous JavaScript, we have a callback function, an event loop, and a task queue. 

- The callback function is acted upon by the call stack during execution after the call back function has been pushed to the stack by the event loop.

<br>

### Call Stack Data Structure

<br>

- At the most basic level, a call stack is a data structure that uses the Last In, First Out (LIFO) principle to temporarily store and manage function invocation (call).

- When we say that the call stack, operates by the data structure principle of Last In, First Out, it means that the last function that gets pushed into the stack is the first to be pop out, when the function returns.

<br>

### Temporarily store

<br>

- When a function is invoked (called), the function, its parameters, and variables are pushed into the call stack to form a stack frame.

- This stack frame is a memory location in the stack. The memory is cleared when the function returns as it is pop out of the stack.

<br>

### Manage function invocation (call)

<br>

- The call stack maintains a record of the position of each stack frame.

- It knows the next function to be executed (and will remove it after execution). This is what makes code execution in JavaScript synchronous.

<br>

### How does the call stack handle function calls?

<br>

- When secondFunction() gets executed, an empty stack frame is created. It is the main (anonymous) entry point of the program.

- secondFunction() then calls firstFunction()which is pushed into the stack.

- firstFunction() returns and prints “Hello from firstFunction” to the console.

- firstFunction() is pop off the stack.

- The execution order then move to secondFunction().

- secondFunction() returns and print “The end from secondFunction” to the console.

- secondFunction() is pop off the stack, clearing the memory.

<br>

### What causes a stack overflow?

<br>

> A stack overflow occurs when there is a recursive function (a function that calls itself) without an exit point. The browser (hosting environment) has a maximum stack call that it can accomodate before throwing a stack error.

<br>

## Readings from [JavaScript error messages && debugging](https://codeburst.io/javascript-error-messages-debugging-d23f84f0ae7c)

<br>

### Types of error messages

<br>

- Types of error messages
    - This is as simple as when you try to use a variable that is not yet declared you get this type os errors.

- Syntax errors
    -  This occurs when you have something that cannot be parsed in terms of syntax, like when you try to parse an invalid object using JSON.parse.

- Range errors
    - Try to manipulate an object with some kind of length and give it an invalid length and this kind of errors will show up.

- Type errors
    - This types of errors show up when the types (number, string and so on) you are trying to use or access are incompatible, like accessing a property in an undefined type of variable.

<br>

### Debugging

<br>

> To debug your JS code, the easiest and maybe the most common way its to simply console.log() the variables you want to check or, by using chrome developer tools.

> If the line you selected was run you will be able to see what has happened before that point and you can try and evaluate the next lines to check if everything is outputting what you are expecting.

> The breakpoint can also be achieved by putting a debugger statement in your code in the line you want to break.

<br>

### Call stack

<br>

- Call back is the path that your program has taken to reach the point were you set a breaking point or were you have an error.

<br>

### Handling errors

<br>

> The light blue part of our earliest example of an error message, that shows up like that when we do not handle errors properly, meaning that anything after that error will not be executed.

> To avoid this we usually `try` to `catch` the errors so we can gracefully fallback to a default state of our application in case of an error (this fallback can be a 404 page which is normally not that graceful but is better than a page to just stop working).

<br>

### Tools to avoid runtime errors

<br>

- `quokka` to evaluate your code as you type.
- `eslint` to make sure your style guide is consistency and it will grab you an error or two along the way and.
- To make JS a more strong typed experience you can use stuff like `TypeScript`.

<br>

## Conclusion

<br>

- What is a ‘call’?
    - Its is basically an invocation. A call stack is a data structure that uses the Last In, First Out (LIFO) principle to temporarily store and manage function invocation (call).
    
- How many ‘calls’ can happen at once?
    - Once at a time.

- What does LIFO mean?
    - Last In, First Out.

- Draw an example of a call stack and the functions that would need to be invoked to generate that call stack.
    - When secondFunction() gets executed, an empty stack frame is created. It is the main (anonymous) entry point of the program.
    - secondFunction() then calls firstFunction()which is pushed into the stack.
    - firstFunction() returns and prints “Hello from firstFunction” to the console.
    - firstFunction() is pop off the stack.
    - The execution order then move to secondFu nction().
    - secondFunction() returns and print “The end from secondFunction” to the console.
    - secondFunction() is pop off the stack, clearing the memory.


- What causes a Stack Overflow?
    - A stack overflow occurs when there is a recursive function (a function that calls itself) without an exit point. The browser (hosting environment) has a maximum stack call that it can accomodate before throwing a stack error.

<br>

- What is a ‘refrence error’?
    - This is as simple as when you try to use a variable that is not yet declared you get this type os errors.

- What is a ‘syntax error’?
    - This occurs when you have something that cannot be parsed in terms of syntax, like when you try to parse an invalid object using JSON.parse.

- What is a ‘range error’?
    - Try to manipulate an object with some kind of length and give it an invalid length and this kind of errors will show up.


- What is a ‘tyep error’?
    - This types of errors show up when the types (number, string and so on) you are trying to use or access are incompatible.

- What is a breakpoint?
    - Code that will make your program stop at that point only if a condition is met.

- What does the word ‘debugger’ do in your code?
    - It creates a breakpoint there.
