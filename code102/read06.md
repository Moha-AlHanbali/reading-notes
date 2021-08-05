[Home](README.md)

<br>

# Implementing Javascript

<br>

## Definition of JavaScript
- `JavaScript` is a programming language used for scripting *(functions when it is commanded to run)* Web pages mainly, but it's still functional in other coding environments. It is `JIT compiled`, meaning it gets executed as soon as the code is run.

<br>

## Usage of JavaScript
- `JavaScript` allows web and software environments to provide an interactive `UI`. It provides depth to users' interactions with the environment and provides functions that `HTML` and `CSS` cannot support alone.
- `JavaScript` allows developers to utilized the usage of parameters in their work, in an otherwise static environments. Meaning their content can be *changing, updated, responsive, and overall dynamic.*
- It works in many Application Programming Interfaces `(API)`, where you can basically create a program within the main program to *automate* tedious functions or perform ones that are not implemented within the parent program.

<br>

## JavaScript Role in Web Pages
- `JavaScript` is mainly responsible for making your Web pages responsive, meaning optimizing `HTML` and `CSS` to adjust best to the users` requirements.

## JavaScript language nature
- As mentioned, `JavaScript` is an interpreted language, meaning the code will run from top to bottom, line by line in order as soon as it is encountered by the browser.

## Integrating JavaScript into HTML Web pages
There are three ways to use `JavaScript code` in `HTML` document, just like `CSS`.
<br>
- Inline `JavaScript`, coded inside `HTML` block in this format:

```
<button onclick="createParagraph()"> YOUR FUNCTION NAME HERE</button>

```

<br>

- Internal `JavaScript`, used inside `HTML` document, within its` own block as in this format:

```
<script>
YOUR CODE GOES HERE
</script>

```

<br>

- External `JavaScript`, linked in a `.js` file to the `HTML` document, as in this format:

```
function myFunction() {
  document.getElementById("demo").innerHTML = "Paragraph changed.";
}
```

<b>

## Types of Data in Javascript
There are many Data Types in `Javascript`, each with their own identifiers and usage, among them are:

- Numbers:
Basically any number
 `1, 5, -5, 48`

- Strings:
Anything enclosed within `"..." or '...'` such as:
`"a", "text", "58", 'number'`

- Boolean Values: Expressions that have one of true values, either `True` or `False`, such as:
`8>5 >>> True, 3=8 >>> False`

<br>

## Javascript Operations
`Javascript` has multiple operators to execute logical expressions and perform functions.

<br>

### Assignment operators
- Which is basically Equal Sign `=`. It is used to assign values to variables using `var` keyword.

```
var name="MYNAME";
```

This will allocate place in memory for a variable called `name` and assign the value `MYNAME` o it.

<br>

###  Arithmetic Operators
- These are the addition, subtraction, multiplication, and division. In addition to more advanced ones (Increment for example `++`).
` +, -, /, *, %, ++, --, **`

<br>

### Comparison Operators
- These logical operators are used to compare values of data, outputting `Boolean` values.
`==, ===, !=, !==, >, <, >=, <=`

<br>

## Conditional Statements
- `If statement` used to proceed with an operation if the conditions are met.

```
If(condition){
  OPERATION CODE GOES HERE
} else {
  IF THE CONDITION IS VOIDED YOU CAN ADD CODE HERE TO PROCEED WITH IT
} 

```