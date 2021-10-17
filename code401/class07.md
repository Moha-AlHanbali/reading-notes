[Home](README.md)

<br>

# Game of Greed 2

<br>

## Readings from [Python Scope & the LEGB Rule: Resolving Names in Your Code](https://realpython.com/python-scope-legb-rule/)

<br>

> The concept of scope rules how variables and names are looked up in your code.

<br>

> The Python scope concept is generally presented using a rule known as the LEGB rule(Local, Enclosing, Global, Built-in).

<br>

### Understanding Scope

<br>

> In programming, the scope of a name defines the area of a program in which you can unambiguously access that name, such as variables, functions, objects, and so on.

<br>

> A name will only be visible to and accessible by the code in its scope. Several programming languages take advantage of scope for avoiding name collisions and unpredictable behaviors.

<br>

- Global scope
  - The names that you define in this scope are available to all your code.

- Local scope
  - The names that you define in this scope are only available or visible to the code within the scope.

<br>

> Scope came about because early programming languages (like BASIC) only had global names.

> To work with global names, you’d need to keep all the code in mind at the same time to know what the value of a given name is at any time. 

<br>

> Some languages like Python use scope to avoid this kind of problem.

> When you use a language that implements scope, there’s no way for you to access all the variables in a program at all locations in that program.

> In this case, your ability to access a given name will depend on where you’ve defined that name.

<br>

> The names in your programs will have the scope of the block of code in which you define them.

> When you can access the value of a given name from someplace in your code, you’ll say that the name is in scope.

> If you can’t access the name, then you’ll say that the name is out of scope.

<br>

### Names and Scopes in Python

<br>

> Since Python is a dynamically-typed language, variables in Python come into existence when you first assign them a value.

> On the other hand, functions and classes are available after you define them using def or class, respectively.

> Modules exist after you import them.

<br>

- You can create Python names through one of the following operations:
  - Assignments
  - Import operations
  - Function definitions
  - Argument definitions in the context of functions
  - Class definitions

<br>

> All these operations create or, in the case of assignments, update new Python names because all of them assign a name to a variable, constant, function, class, instance, module, or other Python object.

<br>

> When you reference a name, you’re just retrieving its content or value.

> When you assign a name, you’re either creating that name or modifying it.

<br>

> Python uses the location of the name assignment or definition to associate it with a particular scope (where you assign or define a name in your code determines the scope or visibility of that name).

<br>

### Python Scope vs Namespace

<br>

> In Python, the concept of scope is closely related to the concept of the namespace.

> Python scope determines where in your program a name is visible.

> Python scopes are implemented as dictionaries that map names to objects.

> These dictionaries are commonly called namespaces. These are the concrete mechanisms that Python uses to store names.

> They’re stored in a special attribute called `.__dict__`.

> Names at the top level of a module are stored in the module’s namespace. In other words, they’re stored in the module’s `.__dict__` attribute.

<br>

> After you import sys, you can use `.keys()` to inspect the keys of `sys.__dict__`.

> This returns a list with all the names defined at the top level of the module. In this case, you can say that `.__dict__` holds the namespace of sys and is a concrete representation of the module scope.

<br>

- If you know how `.__dict__` and namespaces work in Python, then you can reference a name in at least two different ways:
  - Using the dot notation on the module’s name in the form module.name
  - Using a subscription operation on `.__dict__` in the form module`.__dict__['name']`

<br>

### Using the LEGB Rule for Python Scope

<br>

- Local (or function) scope
  - The code block or body of any Python function or lambda expression.
  - This Python scope contains the names that you define inside the function.
  - These names will only be visible from the code of the function.
  - It’s created at function call, not at function definition, so you’ll have as many different local scopes as function calls. 
  - This is true even if you call the same function multiple times, or recursively.
  - Each call will result in a new local scope being created.

<br>

- Enclosing (or nonlocal) scope 
  - Is a special scope that only exists for nested functions.
  - If the local scope is an inner or nested function, then the enclosing scope is the scope of the outer or enclosing function.
  - This scope contains the names that you define in the enclosing function.
  - The names in the enclosing scope are visible from the code of the inner and enclosing functions.

<br>

- Global (or module) scope 
  -Is the top-most scope in a Python program, script, or module.
  - This Python scope contains all of the names that you define at the top level of a program or a module.
  - Names in this Python scope are visible from everywhere in your code.

<br>

- Built-in scope 
  - Is a special Python scope that’s created or loaded whenever you run a script or open an interactive session.
  - This scope contains names such as keywords, functions, exceptions, and other attributes that are built into Python.
  - Names in this Python scope are also available from everywhere in your code.
  - It’s automatically loaded by Python when you run a program or script.

<br>

> If you reference a given name, then Python will look that name up sequentially in the local, enclosing, global, and built-in scope.

> If the name exists, then you’ll get the first occurrence of it. Otherwise, you’ll get an error.

<br>

> When you use nested functions, names are resolved by first checking the local scope or the innermost function’s local scope.

> Then, Python looks at all enclosing scopes of outer functions from the innermost scope to the outermost scope.

> If no match is found, then Python looks at the global and built-in scopes.

> If it can’t find the name, then you’ll get an error.

<br>

> At any given time during execution, you’ll have at most four active Python scopes—local, enclosing, global, and built-in—depending on where you are in the code.

> On the other hand, you’ll always have at least two active scopes, which are the global and built-in scopes.

<br>

### Functions: The Local Scope

<br>

> The local scope or function scope is a Python scope created at function calls.

> Every time you call a function, you’re also creating a new local scope.

> On the other hand, you can think of each def statement and lambda expression as a blueprint for new local scopes.

> These local scopes will come into existence whenever you call the function at hand.

<br>

### Nested Functions: The Enclosing Scope

<br>

> Enclosing or nonlocal scope is observed when you nest functions inside other functions.

> The enclosing scope was added in Python 2.2. It takes the form of the local scope of any enclosing function’s local scopes.

> Names that you define in the enclosing Python scope are commonly known as nonlocal names.

<br>

### Modules: The Global Scope

<br>

> From the moment you start a Python program, you’re in the global Python scope.

> Internally, Python turns your program’s main script into a module called `__main__` to hold the main program’s execution.

> The namespace of this module is the main global scope of your program.

<br>

> To inspect the names within your main global scope, you can use dir().

> If you call dir() without arguments, then you’ll get the list of names that live in your current global scope.

> When you call dir() with no arguments, you get the list of names available in your main global Python scope.

> Note that if you assign a new name (like var here) at the top level of the module (which is `__main__` here), then that name will be added to the list returned by dir().

> There’s only one global Python scope per program execution. This scope remains in existence until the program terminates and all its names are forgotten.

<br>

- Whenever you assign a value to a name in Python, one of two things can happen:
  - You create a new name
  - You update an existing name


<br>

> The concrete behavior will depend on the Python scope in which you’re assigning the name.

> If you try to assign a value to a global name inside a function, then you’ll be creating that name in the function’s local scope, shadowing or overriding the global name.

> This means that you won’t be able to change most variables that have been defined outside the function from within the function.

<br>

> Global names can be updated or modified from any place in your global Python scope.

> Beyond that, the global statement can be used to modify global names from almost any place in your code.

<br>

- Modifying global names is generally considered bad programming practice because it can lead to code that is:
  - Difficult to debug
    - Almost any statement in the program can change the value of a global name.
  - Hard to understand
    - You need to be aware of all the statements that access and modify global names.
  - Impossible to reuse
    - The code is dependent on global names that are specific to a concrete program.

<br>

- Good programming practice recommends using local names rather than global names.
  - Write self-contained functions that rely on local names rather than global ones.
  - Try to use unique objects names, no matter what scope you’re in.
  - Avoid global name modifications throughout your programs.
  - Avoid cross-module name modifications.
  - Use global names as constants that don’t change during your program’s execution.

<br>

### builtins: The Built-In Scope

<br>

> The built-in scope is a special Python scope that’s implemented as a standard library module named builtins in Python 3.x. All of Python’s built-in objects live in this module.

> They’re automatically loaded to the built-in scope when you run the Python interpreter.

> Python searches builtins last in its LEGB lookup, so you get all the names it defines for free.

> This means that you can use them without importing any module.

> Notice that the names in builtins are always loaded into your global Python scope with the special name `__builtins__`.

<br>

> Accidentally or inadvertently overriding or redefining built-in names in your global scope can be a source of dangerous and hard-to-find bugs.

> It’s better to try and avoid this kind of practice.

<br>

> Once you explicitly import builtins, you have the module name available in your global Python scope.

> From this point on, you can use fully-qualified names to unambiguously get the names you need from builtins.

<br>

**Action**                                    |   **Global Code**            |   **Local Code**             |   **Nested Function Code**   |
----------------------------------------------|------------------------------|------------------------------|------------------------------|
Access or reference names that live in the global scope	|     Yes            |      Yes                     |     Yes                      |
Modify or update names that live in the global scope	|  Yes               | No (unless declared global)	|  No (unless declared global) |
Access or reference names that live in a local scope	|   No               | Yes (its own local scope), No (other local scope)	| Yes (its own local scope), No (other local scope)|
Override names in the built-in scope	                |   Yes              | Yes (during function execution)	| Yes (during function execution)
Access or reference names that live in their enclosing scope |  N/A	         | N/A	                         | Yes
Modify or update names that live in their enclosing scope	 |  N/A	         | N/A	                         | No (unless declared nonlocal)
  
<br>

### Modifying the Behavior of a Python Scope

<br>

> Even though Python scopes follow these general rules by default, there are ways to modify this standard behavior.

> Python provides two keywords that allow you to modify the content of global and nonlocal names.

<br>

- These two keywords are:

  - global
  - nonlocal

<br>

> You already know that when you try to assign a value to a global name inside a function, you create a new local name in the function scope.

> To modify this behavior, you can use a global statement.

> With this statement, you can define a list of names that are going to be treated as global names.

> The statement consists of the global keyword followed by one or more names separated by commas.

> You can also use multiple global statements with a name (or a list of names).

> All the names that you list in a global statement will be mapped to the global or module scope in which you define them.

> The use of global is considered bad practice in general. 

> You can also use a global statement to create lazy global names by declaring them inside a function.

> This can be a dangerous practice that can lead to buggy code.

> Finally, it’s worth noting that you can use global from inside any function or nested function and the names listed will always be mapped to names in the global Python scope.

<br>

### The nonlocal Statement

<br>

> Similarly to global names, nonlocal names can be accessed from inner functions, but not assigned or updated.

> If you want to modify them, then you need to use a nonlocal statement.

> With a nonlocal statement, you can define a list of names that are going to be treated as nonlocal.

<br>

> The nonlocal statement consists of the nonlocal keyword followed by one or more names separated by commas.

> These names will refer to the same names in the enclosing Python scope.

<br>

### Using Enclosing Scopes as Closures

<br>

> Closures are a special use case of the enclosing Python scope.

> When you handle a nested function as data, the statements that make up that function are packaged together with the environment in which they execute.

> The resulting object is known as a closure. In other words, a closure is an inner or nested function that carries information about its enclosing scope, even though this scope has completed its execution.

<br>

> You can also call this kind of function a factory, a factory function, or—to be more precise—a closure factory to specify that the function builds and returns closures (an inner function), rather than classes or instances.

> Closures provide a way to retain state information between function calls.

> This can be useful when you want to write code based on the concept of lazy or delayed evaluation.

<br>

> Some variables are called free variables.

> They are variables that are used in a code block but not defined there.

> Free variables are the mechanism that closures use to retain state information between calls.

<br>

### Bringing Names to Scope With import

<br>

> When you write a Python program, you typically organize the code into several modules.

> For your program to work, you’ll need to bring the names in those separate modules to your `__main__` module.

> To do that, you need to import the modules or the names explicitly.

> This is the only way you can use those names in your main global Python scope.

<br>

### Conclusion

<br>

> The scope of a variable or name defines its visibility throughout your code.

> In Python, scope is implemented as either a Local, Enclosing, Global, or Built-in scope.

> When you use a variable or name, Python searches these scopes sequentially to resolve it.

> If the name isn’t found, then you’ll get an error.

> This is the general mechanism that Python uses for name resolution and is known as the LEGB rule.


















