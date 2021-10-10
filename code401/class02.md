[Home](README.md)

<br>

# Testing and Modules

<br>

## Readings from [In Tests We Trust — TDD with Python](https://code.likeagirl.io/in-tests-we-trust-tdd-with-python-af69f47e6932)

<br>

### Unit tests and TDD

<br>

> TTD stands for Test-Driven Development.

<br>

> Unit tests are some pieces of code to exercise the input, the output and the behaviour of your code.

<br>

> The test file name should follow the same name of module name.

<br>


> The first one is the test name. The tests can be considered as your alive documentation. We need to be descriptive about it and to say what is expected and what we are testing.

<br>

> A convention widely used for test structure is the AAA: Arrange, Act and Assert

<br>

- Arrange: you need to organize the data needed to execute that piece of code (input).

- Act: here you will execute the code being tested (exercise the behaviour).

- Assert: after executing the code, you will check if the result (output) is the same as you were expecting.

<br>

### The Cycle

<br>

- The cycle is made by three steps:
  - Write a unit test and make it fail (it needs to fail because the feature isn’t there).
  - Write the feature and make the test pass!
  - Refactor the code.

<br>

> you can go through this cycle every time you add or modify a new feature in your code.

<br>

> TDD is how we can grow our software design consciously and well, just building what is needed to make the test pass. When we are writing tests we are forced to think about the design first and how we can break it into small pieces.

<br>

> The greatest advantage about TDD is to craft the software design first

<br>

> Your code will be more reliable: after a change you can run your tests and be in peace

<br>

## Readings from [What does the if `__name__` == “`__main__`”: do?](https://www.geeksforgeeks.org/what-does-the-if-__name__-__main__-do/)

<br>

### Python behavior

<br>

> Python interpreter reads source file and define few special variables/global variables.

<br>

> If the python interpreter is running that module (the source file) as the main program, it sets the special `__name__` variable to have a value “`__main__`”.

<br>

> If this file is being imported from another module, `__name__` will be set to the module’s name. Module’s name is available as value to `__name__` global variable. 

<br>

> A module is a file containing Python definitions and statements. The file name is the module name with the suffix .py appended. 


<br>

```
print ("Always executed")
 
if __name__ == "__main__":
    print ("Executed when invoked directly")
else:
    print ("Executed when imported")
```

<br>

- All of the code that is at indentation level 0 [Block 1] gets executed. Functions and classes that are defined are, well, defined, but none of their code runs.

- Here, as we executed script.py directly `__name__` variable will be `__main__`. So, code in this if block[Block 2] will only run if that module is the entry point to your program. 

- Thus, you can test whether your script is being run directly or being imported by something else by testing `__name__` variable.

- If script is getting imported by some other module at that time `__name__` will be module name.

<br>

- Every Python module has it’s `__name__` defined and if this is ‘`__main__`’, it implies that the module is being run standalone by the user and we can do corresponding appropriate actions.

- If you import this script as a module in another script, the `__name__` is set to the name of the script/module.

- Python files can act as either reusable modules, or as standalone programs.

- if `__name__` == “main”: is used to execute some code only if the file was run directly, and not imported.

<br>

## Readings from [Recursion](https://www.geeksforgeeks.org/recursion/)

<br>

### What is Recursion

<br>

> The process in which a function calls itself directly or indirectly is called recursion and the corresponding function is called as recursive function.

<br>

```

Normal Addition:

f(n) = 1 + 2 + 3 +……..+ n


Recursive adding:

f(n) = 1             n=1

f(n) = n + f(n-1)    n>1

```

<br>

> In approach(2) the function “ f( ) ” itself is being called inside the function.

<br>

### What is base condition in recursion?

<br>

> The solution to the base case is provided and the solution of the bigger problem is expressed in terms of smaller problems.

<br>

### How a particular problem is solved using recursion? 

<br>

> The idea is to represent a problem in terms of one or more smaller problems, and add one or more base conditions that stop the recursion.

<br>

> We compute factorial n if we know factorial of (n-1). The base case for factorial would be n = 0. We return 1 when n = 0.

<br>

### Why Stack Overflow error occurs in recursion?

<br>

> If the base case is not reached or not defined, then the stack overflow problem may arise.

<br>

> If the memory is exhausted by these functions on the stack, it will cause a stack overflow error. 

<br>

### What is the difference between direct and indirect recursion? 

<br>

> A function fun is called direct recursive if it calls the same function fun. A function fun is called indirect recursive if it calls another function say fun_new and fun_new calls fun directly or indirectly.

<br>

### What is difference between tailed and non-tailed recursion? 

<br>

> A recursive function is tail recursive when recursive call is the last thing executed by the function.

<br>

### How memory is allocated to different function calls in recursion? 

<br>

> When any function is called from main(), the memory is allocated to it on the stack. 

> A recursive function calls itself, the memory for a called function is allocated on top of memory allocated to calling function and different copy of local variables is created for each function call.

> When the base case is reached, the function returns its value to the function by whom it is called and memory is de-allocated and the process continues.

