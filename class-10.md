
[Home](README.md)

<br>

# JS Debugging - from Jon Duckett's books

## Readings from `Javascript and JQuery: Interactive Front-End Web Development`

<br>

### JS Chapter 10: Error Handling & Debugging

<br>

#### ORDER OF EXECUTION

> To find the source of an error, it helps to know how scripts are processed. The order in which statements are executed can be complex; some tasks cannot complete until another statement or function has been run.

> The JavaScript interpreter uses the concept of execution contexts. There is one global execution context; plus, each function creates a new new execution context. They correspond to variable scope.

- Global Context
  - Code that is in the script, but not in a function. There is only one global context in any page.
  - If a variable is declared outside a function, it can be used anywhere because it has global scope. If you do not use the var keyword when creating a variable, it is placed in global scope.

- Function Context
  - Code that is being run within a function. Each function has its own function context.
  - When a variable is declared within a function, it can only be used within that function. This is because it has function-level scope.

- Eval Context
  - Text is executed like code in an internal function called eval().

<br>

- Each execution context also creates its own vari ab 1 es object. This object contains details of all of the variables, functions, and parameters for that execution context.

<br>

#### Hoisting

- `Javascript` interpeter processes one line of code at a time.
- When a statement has to call for another code, the task goes on top of the pile until it's processed, and the interpeter goes back to the task at hand.

- Each time a script enters a new execution context, there are two phases of activity.
  - Prepare : all of the variables and functions and hoisting them to the top of the execution context.
    - The new scope is created
    - Variables, functions, and arguments are created
    - The value of the this keyword is determined
  - Execute
    - Now it can assign values to variables
    - Reference functions and run their code
    - Execute statements

<br>

#### Errors

> If a JavaScript statement generates an error, then it throws an exception. At that point, the interpreter stops and looks for exception-handling code.

> Error objects can help you find where your mistakes are and browsers have tools to help you read them.

- Error types
  - Syntax Error `Syntax is not Correct`
  - ReferenceError `Variable does not exist`
  - EvalError `Incorrect use of eval() function`
  - URIError `Incorrect use of URI functionn`
  - Type Error `Value is unexpected data type`
  - RangeError `Number is outside of range`
  - Error `General error object`
  - NaN `Not an error`

  <br>

#### Dealing with errors

- Debug the script to fix errors (track down the source of the error, and fix it)

- Handle errors gracefully (using try, catch, throw, and finally statements)

<br>

- Debugging workflow
  - Where is the Problem?
    1. Look at the error message `It tells you the relevant script that caused the problem, The line number where it became a problem for the interpreter, and The type of error.`
    2. Check how far the script is running.
    3. Use breakpoints where things are going wrong.
  - What exactly is the problem?
    1. When you have set breakpoints, you can see if the variables around them have the values you would expect them to. If not, look earlier in the script.
    2. Break down / break out parts of the code to test smaller pieces of the functionality. `Write values of variables into the console, Calrfunctions from the console to check if they are returning what you would expect them to, and Check if objects exist and have the methods / properties that you think they do.`
    3. Check the number of parameters for a function, or the number of items in an array.

    <br>

- Use `console.log(), console.warn(), console.info(), console.group(), console.table(), console.assert()`

- Use breakpoints (from sources option in inspect element) and pick the line you want to stop executing code at.

> If you set multiple breakpoints, you can step through them one-by-one to see where values change and a problem might occur.

- You can create a breakpoint in your code using just the `debugger` keyword. When the developer tools are open, this will automatically create a breakpoint.

<br>

#### Exceptions

- If you know your code might fail, use try, catch, and finally. Each one is given its own code block.

- Try
  - First, you specify the code that you t hink might throw an exception within the try block.
  - If an exception occurs in this section of code, control isautomatically passed to thecorresponding catch block.
- Catch
  - If the try code block throws an exception, catch steps in with an alternative set of code.
  - It has one parameter: the error object. Although it is optional, you are not handling the error if you do not catch an error.
- Finally 
  - The contents of the fially code block will run eitherway - whether the try block succeeded or failed.
  - It even runs if a return keyword is used in the try or catch block. It is sometimes used to clean up after the previous two clauses.

> If you know something might cause a problem for your script, you can generate your own errors before the interpreter creates them.
