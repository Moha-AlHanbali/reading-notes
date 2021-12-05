[Home](README.md)

<br>

# Pythonisms

<br>

## Readings from [Enriching Your Python Classes With Dunder (Magic, Special) Methods](https://dbader.org/blog/python-dunder-methods)

<br>

### What Are Dunder Methods?

<br>

> In Python, special methods are a set of predefined methods you can use to enrich your classes.

> They are easy to recognize because they start and end with double underscores.

> Dunder methods let you emulate the behavior of built-in types.

<br>

### Object Initialization: `__init__`

<br>

>The constructor takes care of setting up the object.

> To construct account objects from the Account class I need a constructor which in Python is the `__init__` dunder.

<br>

### Object Representation: `__str__`, `__repr__`

<br>

> It’s common practice in Python to provide a string representation of your object for the consumer of your class.

- There are two ways to do this using dunder methods:

- `__repr__`: The “official” string representation of an object. This is how you would make an object of the class. The goal of `__repr__` is to be unambiguous.

- `__str__`: The “informal” or nicely printable string representation of an object. This is for the enduser.

> If you don’t want to hardcode "class name" as the name for the class you can also use `self.__class__.__name__` to access it programmatically.

<br>

### Iteration: `__len__`, `__getitem__`, `__reversed__`

<br>

> To iterate over things in reversed order you can implement the `__reversed__` special method.

> To iterate over class in reversed order you can implement the `__len__` special method and `__getitem__` to use iterable instances.

<br>

### Operator Overloading for Comparing Accounts: `__eq__`, `__lt__`

<br>

> Use the functools.total_ordering decorator which allows me to take a shortcut, only implementing `__eq__` and `__lt__`.

<br>

### Operator Overloading for Merging Accounts: `__add__`

<br>

> In Python, everything is an object. 

> Implement `__add__` to be able to merge two class instances. 

<br>

### Callable Python Objects: `__call__`

<br>

> You can make an object callable like a regular function by adding the `__call__` dunder method.

<br>

### Context Manager Support and the With Statement: `__enter__`, `__exit__`

<br>

> A context manager is a simple “protocol” (or interface) that your object needs to follow so it can be used with the with statement.

> Basically all you need to do is add `__enter__` and `__exit__` methods to an object if you want it to function as a context manager.

<br>

## Readings from [Python Iterators: A Step-By-Step Introduction](https://dbader.org/blog/python-iterators)

<br>

### Python Iterators That Iterate Forever

<br>

> Repeater looks like a bog-standard Python class.

> But notice how it also includes the `__iter__` dunder method.

- RepeaterIterator looks like a straightforward Python class, but you might want to take note of the following two things:
  - In the `__init__` method we link each RepeaterIterator instance to the Repeater object that created it. That way we can hold on to the “source” object that’s being iterated over.
  - In RepeaterIterator.`__next__`, we reach back into the “source” Repeater instance and return the value associated with it.

<br>

### How do for-in loops work in Python?

<br>

- The for-in was just syntactic sugar for a simple while loop:
  - It first prepared the repeater object for iteration by calling its `__iter__` method. This returned the actual iterator object.
  - After that, the loop repeatedly calls the iterator object’s `__next__` method to retrieve values from it.

> Ierators provide a common interface that allows you to process every element of a container while being completely isolated from the container’s internal structure.

<br>

> Python offers these facades for other functionality as well.

> For example, `len(x)` is a shortcut for calling `x.__len__`. Similarly, calling `iter(x)` invokes `x.__iter__` and calling `next(x)` invokes `x.__next__`.

<br>

### A Simpler Iterator Class

<br>

> We need it to host the `__next__` method for fetching new values from the iterator.

> But it doesn’t really matter where `__next__` is defined. In the iterator protocol, all that matters is that `__iter__` returns any object with a `__next__` method on it.

<br>

### Who Wants to Iterate Forever

<br>

> Python iterators normally can’t be “reset”—once they’re exhausted they’re supposed to raise StopIteration every time `next()` is called on them.

> To iterate anew you’ll need to request a fresh iterator object with the `iter(`) function.

### Conclusion

<br>

- Iterators provide a sequence interface to Python objects that’s memory efficient and considered Pythonic. Behold the beauty of the for-in loop!
- To support iteration an object needs to implement the iterator protocol by providing the `__iter__` and `__next__` dunder methods.
- Class-based iterators are only one way to write iterable objects in Python. Also consider generators and generator expressions.

<br>

## Readings from [What Are Python Generators?](https://dbader.org/blog/python-generators)

<br>

### Python Generators 101 – The Basics

<br>

> Calling a generator function doesn’t even run the function.

> It merely creates and returns a generator object.

> The code in the generator function only executes when `next()` is called on the generator object.

> When a return statement is invoked inside a function, it permanently passes control back to the caller of the function.

> When a `yield` is invoked, it also passes control back to the caller of the function—but it only does so temporarily.

> Whereas a `return` statement disposes of a function’s local state, a `yield` statement suspends the function and retains its local state.

<br>

### Python Generators That Stop Generating

<br>

> We were able to signal the end of iteration by manually raising a StopIteration exception.

> Because generators are fully compatible with class-based iterators, that’s still what happens behind the scenes.

> Generators stop generating values as soon as control flow returns from the generator function by any means other than a `yield` statement.

> This means you no longer have to worry about `raising` StopIteration at all!

<br>

### Conlusion

<br>

- `Generator` functions are syntactic sugar for writing objects that support the iterator protocol. `Generators` abstract away much of the boilerplate code needed when writing class-based iterators.
- The `yield` statement allows you to temporarily suspend execution of a generator function and to pass back values from it.
- `Generators` start `raising` StopIteration exceptions after control flow leaves the generator function by any means other than a `yield` statement.