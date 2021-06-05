[Home](README.md)

<br>

# Javascript Loops

<br>

## Javascript Operators
- In addition to Operators discussed in [A Step Into Javascript Expressions and Operators](read07.md), few more exist and used alongside them.

<br>

### Comma Operator
- This Operator `,` separates the past and following entity that it is located in between. It is used inside `FOR` loops to "list" multiple variables.

 ```
 var x = ['a', 'b', 'c', 'd', 'e']
 variable x value is assigned to be the array

 each index of the array is defined and separated from the next/following index by a comma (,)
 ```

<br>

### Unary Operator
These Operators require one entity to perform operation on.

 - `delete` Operator is used to delete an objects property in the following formats: 
 `delete object.property, delete object[propertyKey], delete objectname[index], delete property; (within with statement)`

 `delete` doesn't work (returns false) in some cases:

 ```

 When the object is created implicitly  
 x = 5
 delete x;

 The object is declared variable
 var x = 5
 delete x;

 When the object is non-configurable property
 delete x.PI

 When objects are user defined properties
 var myobj = {x: 0}
 delete myobj.x

 ```

 <br>

 - `typeof` Operator is used to indicate the type of unevaluated entity (operand).

 ```
 var x = 10
 var y = '10'
 var z = ['a', 'b', 'c']

 typeof x; >> Number
 typeof y; >> String
 typeof z; >> Object
 typeof a; >> Undefined
 typeof true; >> Boolean
 ```

<br>

- `void` Operator specifies an expression to be evaluated without returning a value (cancels the effect of the following
keyword).

 `void function >> forces function keyword to behave as an expression instead of a declaration`

 <br>

### Relational Operators
These Operators compare their operands and return Boolean values as results.

 - `In` Operator returns `True` if the operand is within the specified object in this format: `propNameOrNumber in objectName`.

 ```
 var x = ['a', 'b', 'c', 'd', 'e', 'f']

 0 in  x;  >> True
 1 in  x;  >> True
 10 in x;  >> False

 ```

 <br>

 - `instanceof` Operator if the specified object is of the specified object type in this format: `objectName instanceof objectType
`.

<br>

### Operator Precedence
Which is basically the priority of executing Operators, which can be overridden by using parentheses `()`, which are refered to as `Grouping operator`.


Operator type	                     |    	Individual operators
-----------------------------------|-----------------------------------
member                             | `. []`
call / create instance	           | `() new`
negation/increment	               | `! ~ - + ++ -- typeof void delete`
multiply/divide	                   | `* / %`
addition/subtraction	             | `+ -`
bitwise shift	                     | `<< >> >>>`
relational                         | `< <= > >= in instanceof`
equality                           | `== != === !==`
bitwise-and	                       | `&`
bitwise-xor	                       | `^`
bitwise-or	                       | `|`
logical-and	                       | `&&`
logical-or	                       | `||`
conditional	                       | `?:`
assignment                         | `= += -= *= /= %= <<= >>= >>>= &= ^= |= &&= ||= ??=`
comma                              | `,`

<br>

## Expressions
Expressions are any valid unit of code that resolves to a value. Aside from expressions discussed in [A Step Into Javascript Expressions and Operators](read07.md), others are used in `Javascript`.

<br>

### Primary Expressions
Which are Basic keywords that have specific value they resolve to.

- `this` expression refer to the current object in these formats: `this['propertyName'], this.propertyName`.

<br>

### Left-Hand-Side Expressions
Where Left values are the destination of an assignment.

- `new` operator creates an instance of a user-defined object type or of one of the built-in object types i this format:

`var objectName = new objectType([param1, param2, ..., paramN]);`

- `super` operator used to call functions on an object's parent. it is used in these formats:

`super([arguments]); >> calls the parent constructor.
super.functionOnParent([arguments]);`

<br>

## Loops
- Loops are used to iterate a procedure repeatedly,

<br>

### `for` statement

- `for` is used to created a loop that keeps repeating until specified conditions are met.

 ```
 for ([initialExpression]; [conditionExpression]; [incrementExpression])
  statement`
 ```

<br>

### `do...while` statement
- `do...while` repeats until a specified condition evaluates to false.

 ```
 do
  statement
 while (condition);`
 ```
<br>

### `while` statement
- `while` is used to executes its statements as long as a specified condition evaluates to true.

 ```
 while (condition)
  statement
 ```
<br>

### `labeled` statement
-  `label` provides a statement with an identifier that lets you refer to it elsewhere in your program.

 ```
 label :
   statement
 ```
<br>

### `break` statement
- `break` terminate a loop, switch, or in conjunction with a labeled statement.


  ```
  break;


  break [label];
  ```

<br>

### `continue` statement
- `continue` The continue statement can be used to restart a while, do-while, for, or label statement.
- When you use `continue` without a `label`, it terminates the current iteration of the innermost enclosing `while`, `do-while`, or `for` statement and continues execution of the loop with the next iteration.
 ```
 continue [label];
 ```

<br>

### `for...in` statement
- `for...in` iterates a specified variable over all the enumerable properties of an object.

 ```
for (variable in object)
  statement
  ```

  <br>

  ### `for...of` statement
  - `fore...of` creates a loop Iterating over iterable objects (including Array, Map, Set, arguments object and so on), invoking a custom iteration hook with statements to be executed for the value of each distinct property.

  ```
  for (variable of object)
  statement
  ```
