[Home](README.md)

<br>

# HTML Lists, Control Flow with JS, and the CSS Box Model - from Jon Duckett's books

<br>

## Readings from `HTML & CSS: Design and Build Websites`

### HTML Chapter 3: Lists

<br>

#### Using Lists in HTML
- Lists are required to order and organize information.
- `HTML` provides different options to list items and content:

1. Ordered Lists `<ol>`
2. Unordered Lists `<ul>`
3. Definition Lists `<dl>`

- Each list item of the first two types needs to be enclosed within List Item tags`<li>`.
- Definition list items need to be enclosed with Definition Term tags `<dt>` and Definition tag `<dd>`.
- You can nest lists within eachother for further information.

<br>

```
HTML:

<ol>
<li> Item 1 </li>
<li> Item 2 </li>
<li> Item 3 </li>
</ol>

Display:

1. Item 1
2. Item 2
3. Item 3


HTML:

<ul>
<li> Item 1 </li>
<li> Item 2 </li>
<li> Item 3 </li>
</ul>

Display:

• Item 1
• Item 2
• Item 3


HTML:

<ul>
<li> Item 1 </li>
    <ul>
        <li> Item A </li>
        <li> Item B </li>
    </ul>
</ul>

Display:

• Item 1
    ◦ Item A
    ◦ Item B


HTML:

<dl>
<dt> Item 1 </dt>
<dd> First Item in this list </dd>
<dt> Item 2 </dt>
<dd> Second Item in this list </dd>
<dt> Item 3 </dt>
<dd> Third Item in this list </dd>
</dl>

Display:

Item 1
     First Item in this list
Item 2
    Second Item in this list
Item 3
    Third Item in this list

```

<br>

### CSS Chapter 13: Boxes

<br>

#### Elements in CSS

> CSS treats each HTML element as if it lives in its own box.

- CSS then allows you to control and manipulate these boxes shapes.

- You may use different units to specify property values as required `px, %, em, ...`.

<br>

CSS Property                                      | Function
--------------------------------------------------|--------------------------------------------------
`width, height`                                   | Sets your own dimensions for a box
`min-width, max-, min-height, max-height`         | Specifies the min/max size a box can be displayed.
`overflow (hidden/scroll)`                        | Informs the browser what to do if the content contained within a box is larger than the box itself.
`border`                                          | Controls Box border (whether is it visible or not)
`border-width (thin/medium/thick/px)`             | Controls the width of a border.
`border-style (solid/dotted/dashed/...)`          | Controls the style of a border.
`border-color`                                    | Controls the color of a border.
`margin`                                          | Controls the gap between the borders of two adjacent boxes.
`padding`                                         | The space between the border of a box and any content contained within it.
`display (inline/inline-block/block/none)`        | Turns an inline element into a block-level element or vice versa.   
`visibility (hidden/visible)`                     | Controls the visibility of a box.



<br>


## Readings from `Javascript and JQuery: Interactive Front-End Web Development`

<br>

### JS Review from Reading 02 - Chapter 2: Basic JavaScript Instructions

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

### JS Chapter 4: Decisions and Loops

<br>

#### If... Else Statement

- The conditional `if... else` statement checks for a condition, if it is met the code following `if` is executed, if it is not the code following `else` is executed.

``` 
If (condition) {
    execute this code;
    } else {
        execute this code
    }
```

<br>

#### Switch Statement

- `Switch` statement checks if specific cases apply to the variable in check, if one or more applies, their code will be executed, otherwise it won't and `default` code will get executed instead.

```
switch (variable){

    case 'specify case 1 here`:
        code to be executed;
        break;

    case 'specify case 2 here`:
      code to be executed;
      break;

    default:
        code to be executed;
        break;

}

```
<br>

#### Type Coercion & Weak Typing

> JavaScript can convert data types behind the scenes to complete an operation.

> JavaScript is said to use weak typing because the data type for a value can change.

<br>

#### Truthy and Falsy Values

> Falsy values are treated as if they are false.

- These can be as one of the following: 
`boolean False value, number 0, NaN, Empty Values, A variable with no value assigned to it`.

> Truthy values are treated as if they are true. Almost everything that is not falsy  can be treated as if it were true.

<br>

#### Checking Equality and Existence

> A unary operator returns a result with just one operand.

> Because of type coercion, the strict equality operators ===and ! == result in fewer unexpected values than ==and ! = do.

<br>

#### Loops

- Loops are used to iterate a procedure repeatedly;

<br>

- `for` is used to created a loop that keeps repeating until specified conditions are met.

 ```
 for ([initialExpression]; [conditionExpression]; [incrementExpression])
  statement`
 ```

  ```
  for (let x = 10; x > 5; x--) {
   console.log(x);
   }
  
  Console output will be:
  > 10
  > 9
  > 8
  > 7
  > 6  
  ```
<br>

- `do...while` repeats until a specified condition evaluates to false.

 ```
 do
  statement
 while (condition);`
 ```
<br>

- `while` is used to executes its statements as long as a specified condition evaluates to true.

 ```
 while (condition)
  statement
 ```

 ```
 let x = 10

 while (x > 5) {
  x--;
  console.log(x);
  }

  Console output will be:
  > 9
  > 8
  > 7
  > 6
  > 5
 ```
 
<br>
