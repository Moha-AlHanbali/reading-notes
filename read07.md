[Home](README.md)

# A Step Into Javascript Expressions and Operators

<br>

## Javascript Operators
`Javascript` has multiple operators to execute logical expressions and perform functions.

<br>

### Assignment operators
- Which is basically Equal Sign `=`. It is used to assign values to variables using `var` keyword.

```
var name="MYNAME";
```

This will allocate place in memory for a variable called `name` and assign the value `MYNAME` o it.

<br>

- Assignment operators can perform additional functions using Arithmetic Operators, to express addition/subtraction and such with assignment in this format:

`x += y, x -= y, x *= y, x /= y, x %= y, x **= y`

That, replaces this format:

`x = x + y, x = x - y, x = x * y, x = x / y, x = x % y, x = x ** y`

- Additional `bitwise` assignment operators are used to manuplate a specific amount/order of bits in a specific direction/overlap and compare values depending on used operator:

`x <<= y, x >>= y, x >>>= y`

Logical `And` and ` Or` can be used in `bitwise` assignment to over lap binary values and operate them.

`x &= y, x |=y` 

This also follows the same rule as before in what does it mean. An example of `bitwise` assignment operator usage:

```
The Decimal Number 1 is equal to this value in binary 0000000000000001
The Decimal Number 5 is equal to this value in binary 0000000000000101
(Both refer to Two's Complement of a Signed Binary Number)

x <<= 5
Moves the Decimal Number 1's bits 5 digits to the left 0000000000100000
x = 0000000000100000 (binary value is equal to the Decimal Number 32)

x &= 5
0000000000000001
0000000000000101
These two values "intersect" in only one bit digit when overlapped using `And` logical `bitwise` operator resulting in:
x = 0000000000000001 (which is equal to the value of the Decimal Number 1)

```

- Logical `And`, and `Or, expressions can be used for assignment in such formats:

`x &&= y, x ||= y, x ??= y`

And they operate in boolean logic:

```
x = 2 (True/Truthy in binary means >> not 0)
y = 0 (False/Falsey in binary means >> equals 0)

x &&= Y
means x = x AND y
means x = true and false 
means x = false
means x = 0

(Assigns only of x is truthy)
(in OR case, the operator assigns only if x is falesy >> changes the value of false entity because the other one is truthy)

While x ??= y only assigns if x is either null or undefined
```

<br>

### Return Value and Chaining
- All Assignments have return values that follows rules in which order to they function when chained.

```
x = a + b 
means (a + b) will be calculated first, then assigned its' value to (x) >> which means the return value of (a + b) is the value of (x), in order.

x += y /= z
means x += (y = (y/z))
then  x += (new y value assigned)
then  x = (x + new y value)
then  x new value is assigned
```

<br>

### Destructuring
- `Javascript` allows data to be stored and extracted from arrays, which functions in this format:

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

###  Arithmetic Operators
- These are the addition, subtraction, multiplication, and division. In addition to more advanced ones (Increment for example `++`).
` +, -, /, *, %, ++, --, **`

<br>

### Comparison Operators
- These logical operators are used to compare values of data, outputting `Boolean` values.
`==, ===, !=, !==, >, <, >=, <=`

<br>

### Logical Operators
- Logical Operators `And, OR, and NOT` are typically used with Boolean values, but they can be also used to execute the same logic on any values:

` &&, ||, !`

```
True  && True = True
True  && False = False
False && True = False 

True  || True = True
True  || False = True
False || True = False

!True = False
!False = True
```
<br>

### String Operators
- Concatenation operator `+` can be used to concatenate (Join) two string values together:

```
'Three ' + 'Strings' + '!' = 'Three Strings!'

a = '123'
b = '456'
a + b = '123456'
```
<br>

### Conditional Operator
- Also know as `ternary operator`, it is often used as a shorter replacement for `If Statement`:

```
x ? a : b

x executes a if x is truthy
x executes b if x is falesy
```

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
<br>

## Functions
- Functions are declared by using the keyword `function` followed by:
  - Name of the function
  - List of parameters, enclosed within `()` and separated with `,`
  - The statement that defines the function, enclosed within `{}`

  ```
function square(number) {
  return number * number
}

  ```
  
  Here, `function` is the keyword, `square` is the name of the function, `number` is a parameter that will be used to reference values. `return` calls for the return value of the specified operations after it.
  Functions are used to define specific operations in a document to be reused or exported into other documents.

  ### Calling Function
  - Calling functions (using them) performs their specified operations on the values where parameters were specified.

  ```
 square(5)
 calls the function square
 square(parameter>>named number in this case)
 return number * number
 return 5 * 5
 25
  ```

  <br>

  ### Function Scope
- Variables defined inside a function can be only accessed by the function, while the   function can access variables anywhere where it is defined (within its' scope).

-A function defined on its' own is called defined on a `global scope` and can access all variables within itself, while a function defined within another can only access its' own variables.

<br>

### Predefined Functions
- There is a set of built-in functions in `Javascript`, that do pre-determained operations:

`eval(), uneval(), isFinite(), isNaN(), parseFloat(), parseInt(), decodeURI(), decodeURIComponent(), encodeURI(), encodeURIComponent(), escape(), unescape()`