[Home](README.md)

<br>

# FUNCTIONAL PROGRAMMING

<br>

## Readings from [Concepts of Functional Programming in Javascript](https://medium.com/the-renaissance-developer/concepts-of-functional-programming-in-javascript-6bc84220d2aa)

<br>

### What is functional programming?

<br>

> Functional programming is a programming paradigm — a style of building the structure and elements of computer programs — that treats computation as the evaluation of mathematical functions and avoids changing-state and mutable data.

<br>


#### Pure functions

<br>

- A pure function returns the same result if given the same arguments (it is also referred as deterministic).

- It does not cause any observable side effects.

<br>

##### Pure functions benefits

<br>

- The code’s definitely easier to test. We don’t need to mock anything.

<br>

#### Immutability

<br>

> When data is immutable, its state cannot change after it’s created. If you want to change an immutable object, you can’t. Instead, you create a new object with the new value.

<br>

#### Referential transparency

<br>

> Basically, if a function consistently yields the same result for the same input, it is referentially transparent.

> pure functions + immutable data = referential transparency

<br>

#### Functions as first-class entities

<br>

> The idea of functions as first-class entities is that functions are also treated as values and used as data.

- Functions as first-class entities can:
    - Refer to it from constants and variables
    - Pass it as a parameter to other functions
    - Return it as result from other functions

<br>

#### Higher-order functions

<br>

> Function that either takes one or more functions as arguments, or returns a function as its result.

<br>

## Conclusion

<br>

- What is functional programming?
    - Is a programming paradigm — a style of building the structure and elements of computer programs — that treats computation as the evaluation of mathematical functions and avoids changing-state and mutable data.

- What is a pure function and how do we know if something is a pure function?
    - A pure function returns the same result if given the same arguments (it is also referred as deterministic), it does not cause any observable side effects.

- What are the benefits of a pure function?
    - The code’s easier to test.

- What is immutability?
    - When data is immutable, its state cannot change after it’s created.

- What is Referential transparency?
    -  If a function consistently yields the same result for the same input, it is referentially transparent

<br>

- What is a module?
    - A Javascript file that we use to split up our code logically for functionality and reusability.

- What does the word ‘require’ do?
    - It allows us to use another module inside our JS file (more or less imports it).

- How do we bring another module into the file the we are working in?
    - We 'require' it.

- What do we have to do to make a module available?
    - We have to export the module.
