[Home](README.md)

<br>

# Classes and Objects

<br>

## Readings from [Classes and Objects](https://www.learnpython.org/en/Classes_and_Objects)

<br>

> Objects are an encapsulation of variables and functions into a single entity. 

> Objects get their variables and functions from classes. 

> Classes are essentially a template to create your objects.

<br>

### Accessing Object Variables

<br>

> Access Object Variables using `object.variable`.

> You can create multiple different objects that are of the same class(have the same variables and functions defined).

> Each object contains independent copies of the variables defined in the class. 

<br>

### Accessing Object Functions

<br>

> Access Object Variables using `object.function()`.

<br>

## Readings from [Thinking Recursively in Python](https://realpython.com/python-thinking-recursively/)

<br>

> If the current problem represents a simple case, solve it. If not, divide it into subproblems and apply the same strategy to them.

<br>

### Recursive Functions in Python

<br>

> A recursive function is a function defined in terms of itself via self-referential expressions.

> The function will continue to call itself and repeat its behavior until some condition is met to return a result. 

> All recursive functions share a common structure made up of two parts: base case and recursive case.

<br>

> Behind the scenes, each recursive call adds a stack frame (containing its execution context) to the call stack until we reach the base case.

> Then, the stack begins to unwind as each call returns its results.

<br>

### Maintaining State

<br>

> When dealing with recursive functions, keep in mind that each recursive call has its own execution context.

- To maintain state during recursion you have to either:
  - Thread the state through each recursive call so that the current state is part of the current call’s execution context.
  - Keep the state in global scope.

<br>

### Recursive Data Structures in Python


<br>

> A data structure is recursive if it can be deﬁned in terms of a smaller version of itself.

- A list is an example of a recursive data structure. Other examples include set, tree, dictionary, etc.
  - Starting with an empty list, you can generate any list by recursively applying the attach_head function, and thus the list data structure can be defined recursively as:
  - Recursion can also be seen as self-referential function composition. We apply a function to an argument, then pass that result on as an argument to a second application of the same function, and so on. Repeatedly composing attach_head with itself is the same as attach_head calling itself repeatedly.

<br>

> Recursive data structures and recursive functions go together like bread and butter. 

> The recursive function’s structure can often be modeled after the definition of the recursive data structure it takes as an input. 

<br>

### Naive Recursion is Naive

<br>

>  Fibonacci surmised that the number of pairs of rabbits born in a given year is equal to the number of pairs of rabbits born in each of the two previous years, starting from one pair of rabbits in the ﬁrst year.

> he deﬁned the recurrence relation: `Fn = Fn-1 + Fn-2`

> The base cases are: `F0 = 0 and F1 = 1`

<br>

### Pesky Details

<br>

> Python doesn’t have support for tail-call elimination. 

> As a result, you can cause a stack overflow if you end up using more stack frames than the default call stack depth.

> Also, Python’s mutable data structures don’t support structural sharing, so treating them like immutable data structures is going to negatively affect your space and GC (garbage collection) efficiency because you are going to end up unnecessarily copying a lot of mutable objects.

<br>

## Readings from [Python Testing with pytest: Fixtures and Coverage](https://www.linuxjournal.com/content/python-testing-pytest-fixtures-and-coverage)

<br>

### Fixtures

<br>

> In many cases you'll have a few tests with similar characteristics, something that pytest handles with "parametrized tests".

> But in other cases, things are a bit more complex. 

> You'll want to have some objects available to all of your tests. Those objects might contain data you want to share across tests, or they might involve the network or filesystem. 

> These are often known as "fixtures" in the testing world, and they take a variety of different forms.

<br>

> At the same time, fixtures are used differently from global variables. 

> For example, let's say you want to include this fixture in one of your tests. 

> You then can mention it in the test's parameter list. Then, inside the test, you can access the fixture by name.

<br>

> Your fixture might act like data, in that you don't invoke it with parentheses. 

> But it's actually a function under the hood, which means it executes every time you invoke a test using that fixture.

> This means that the fixture, in contrast with regular-old data, can make calculations and decisions.

<br>

> If you want to set up an object and then use it multiple times without creating it again? You can do that by setting the fixture's "scope".

> For example, if you set the scope of the fixture to be "module", it'll be available throughout your tests but will execute only a single time. 

> You can do this by passing the scope parameter to the @pytest.fixture decorator.

<br>

> Giving this particular fixture "module" scope is a bad idea, since the second test will end up having a StringIO whose location pointer (checked with file.tell) is already at the end.

<br>

### Coverage

<br>

> Now, 100% code coverage doesn't mean that your code is perfect or that it lacks bugs. But it does give you a greater degree of confidence in the code and the fact that it has been run at least once.

> There's a package called pytest-cov on PyPI that you can download and install.

> Once that's done, you can invoke pytest with the --cov option. If you don't say anything more than that, you'll get a coverage report for every part of the Python library that your program used, so I strongly suggest you provide an argument to --cov, specifying which program(s) you want to test.

> And, you should indicate the directory into which the report should be written.

<br>

> Once you've done this, you'll need to turn the coverage report into something human-readable. I suggest using HTML, although other output formats are available.

<br>

> This creates a directory called htmlcov. Open the index.html file in this directory using your browser, and you'll get a web-based report showing (in red) where your program still lacks coverage. Sure enough, in this case, it showed that the even-number path wasn't covered.



