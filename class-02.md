[Home](README.md)

<br>

# Basics of HTML, CSS & JS - from Jon Duckett's books

<br>

## Readings from `HTML & CSS: Design and Build Websites`

### HTML Chapter 2: Text

<br>

#### HTML Text Tags

- `HTML` uses Structural and Semantics Markup to describe the hierarchy of information and clarity in what is displayed.
- Generally, you have to enclose your text with the opening and closing tags of choice for them to function.

`<p> Example </p>`

<br>

Tag                                                        | Purpose
-----------------------------------------------------------|-------------------------------------------------------------
`<h1>, <h2>, <h3>, <h4>, <h5>, <h6>`                       | Order page headings from more to less important respectively
`<p>`                                                      | Marks paragraphs text
`<b>, <i>, <sup>, <sub>`                                   | Typographical Emphasis - Make text render bold/italic/...
`(White Space), <br>, <hr>`                                | Create Line-Breaks
`<strong>, <em>, <blockquote>, <q>`                        | Semantic Markup - Do not affect page structure but add emphasis
`<cite>, <dfn>`                                            | Citations and Definitions in order

<br>



### HTML Chapter 10: Introducing CSS

<br>

#### What is CSS

> CSS works by associating rules with HTML elements. These rules govern
how the content of specified elements should be displayed.

<br>

#### Parts of a CSS Rule
- A `CSS` rule consists of a `selector` and a `declaration`.
  - Selectors indicate which
element the rule applies to.
  - Declarations indicate how
the elements referred to in
the selector should be styled.

<br>

```
h1 {
   color: white;
   background-color: black;
}

Where:
      h1 is the selector
      what's within {} is the declaration
      color and background-color are called: properties
      white and black are called: values 

```

<br>

- You can use `,` to assign the same declaration to multiple selectors in this format `p, h1 { declaration here }`

#### Usage of CSS

- Inline `CSS`, where you type `CSS Syntax` within `HTML` tag, in a similar format:

```
<p style="color:red;"> Your Stylized Text Here </p>
```

<br>

- Internal `CSS`, where you type `CSS Syntax` inside `HTML` documents, as follows:

```
<style>
p{
  color:red
}
</style>
```

<br>

- External `CSS`, where you link `CSS` files to your `HTML` document, and basically works like `Internal CSS`, but in its' own environment.

```
p{
  color:red
}
```

<br>
The results of all the previous three methods should render the same output:
<p style="color:red;"> Your Stylized Text Here </p>

<br>

#### CSS Selectors
<br>

CSS Selector                                            | Usage
--------------------------------------------------------|---------------------------------
Universal Selector *(Apply to all elements in document)*| `* {}`
Type Selector *(Matches the name)*                      | `h1, h2, h3 {}`
Class Selector                                          | `.className`
ID Selector                                             | `#IDname`
Child Selector *(Matches adirect child of an element)*  | `li>a {}`
Descendant Selector *(Matches an element descending of another)*| `p a {}`
Adjacent Sibling Selector *(Matches the next sibling another element)*| `h1+p {}`
General Sibling Selector *(Matches an element that is a sibling of another)*| `h1~p {}`

<br>


## Readings from `Javascript and JQuery: Interactive Front-End Web Development`

<br>

### JS Chapter 2: Basic JavaScript Instructions

<br>

#### Javascript Code

- `Javascript` code is written as a step of instructions, each one of them is known as a `statement`.
- `Statements` should end with a `;`.
- `Javascript` is a case-sensitive language.
- Some text can be commented out to leave descriptions/information about your code to other users as follows `// Comment goes here`.
- `Javascript` has to store any value into memory by assigning them to variables using keywords  `let/var variable = value`.

<br>

#### Javascript Datatypes

- `Javascript` has multiple data type that it can use and store.
  - `Numbers` as in `1, 2, 22, 65, 845`
  - `Floats` as in `1.5, 22.35, 0.2, 99.99`
  - `Strings` as in `"text", "125", "one"`
  - `Boolean` as in `True, False`

- Once you assign a value to a variable (declare it) you can later change it in most cases using a different method for each keyword.
- Variable names need to be unique and not built-in/duplicate names.

<br>

#### Arrays

- Arrays store a list of variables in `Javascript`.

 ```
 var x = ['a', 'b', 'c'];
 where ('a') is index (0) of the variable (x) 
      ('b') is index (1) of the variable (x)and so on

 var a = x[0] 

 >> means to assign the value of the first index of variable x to the variable a
 a = 'a'

 var b = x[1] 

 >>  means to assign the value of the second index of variable x to the variable b 
 b = 'b'
 ```

<br>

#### Expressions and Operators

- Which are basically Equal Sign `=`. It is used to assign values to variables using `var` keyword.

 ```
 var name="MYNAME";
 ```

This will allocate place in memory for a variable called `name` and assign the value `MYNAME` o it.

<br>

- Assignment operators can perform additional functions using Arithmetic Operators, to express addition/subtraction and such with assignment in this format:

`x += y, x -= y, x *= y, x /= y, x %= y, x **= y`

That, replaces this format:

`x = x + y, x = x - y, x = x * y, x = x / y, x = x % y, x = x ** y`

<br>
 
-  Arithmetic Operators are addition, subtraction, multiplication, and division. In addition to more advanced ones (Increment for example `++`).
` +, -, /, *, %, ++, --, **`

<br>


### JS Chapter 4: Decisions and Loops

<br>

#### Decision Making

- The need for decision making arises in script wherever there is a situation with multiple outputs or inputs.
- Decision components:
1. A value, when the expression is evaluated.
2. Conditional statement that decides what to do in each situatuin.

- These logical operators are used to compare values of data, outputting `Boolean` values.
 
 `==, ===, !=, !==, >, <, >=, <=`
 
<br>

- Logical Operators `And, OR, and NOT` are typically used with Boolean values, but they can be also used to execute the same logic on any values:

 `&&`, `||`, `!`

<br>

#### If Statement

- `If statement` (`Conditional Statements`) used to proceed with an operation if the conditions are met.

 ```
 If(condition){
   OPERATION CODE GOES HERE
 } else {
   IF THE CONDITION IS VOIDED YOU CAN ADD CODE HERE TO PROCEED WITH IT
 } 
