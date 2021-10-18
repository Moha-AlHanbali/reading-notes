[Home](README.md)

<br>

# Game of Greed 3

<br>

## Readings from [List Comprehensions in Python](https://www.pythonforbeginners.com/basics/list-comprehensions-in-python)

<br>

> In order to keep your code elegant and readable, it's recommended that you use Python's comprehension features.

> List comprehension is a powerful and concise method for creating lists in Python that becomes essential the more you work with lists, and lists of lists.

<br>

### Syntax

<br>

> `my_new_list = [ expression for item in list ]`

<br>

- Three ingredients are necessary for a python list comprehension to work.
  - First is the expression we'd like to carry out (expression inside the square brackets).
  - Second is the object that the expression will work on (item inside the square brackets).
  - Finally, we need an iterable list of objects to build our new list from (list inside the square brackets).

<br>

> Imagine you're going to perform an expression on each item in the list. The expression will determine what item is eventually stored in the output list. 

> Not only can you perform expressions on an entire list in a single line of code, but it's possible to add conditional statements in the form of filters, which allows for more precision in the way lists are handled.

<br>

- Notes about Lists Comprehensions
  - List comprehension methods are an elegant way to create and manage lists. 
  - In Python, list comprehensions are a more compact way of creating lists. 
  - More flexible than for loops, list comprehension is usually faster than other methods.

<br>

### Create a List with range()

<br>

- Creating a list with list comprehensions

```
# construct a basic list using range() and list comprehensions
# syntax
# [ expression for item in list ]
digits = [x for x in range(10)]

print(digits)


# [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
```

<br>

### Create a List Using Loops and List Comprehension in Python

<br>

- Comparing list creation methods in Python

```
# create a list using a for loop
squares = []

for x in range(10):
    # raise x to the power of 2
    squares.append(x**2)

print(squares)

---------------------------------------------

# create a list using list comprehension
squares = [x**2 for x in range(10)]

print(squares)


# [0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
```

<br>

### Multiplying Parts of a List

<br>

- Multiplication with list comprehensions

```
# create a list with list comprehensions
multiples_of_three = [ x*3 for x in range(10) ]

print(multiples_of_three)


# [0, 3, 6, 9, 12, 15, 18, 21, 24, 27]

---------------------------------------------

even_numbers = [ x for x in range(1,20) if x % 2 == 0]


# [2, 4, 6, 8, 10, 12, 14, 16, 18]

```

<br>

### Show the first letter of each word using Python

<br>

- Using list comprehensions with strings

```
# a list of the names of popular authors
authors = ["Ernest Hemingway","Langston Hughes","Frank Herbert","Toni Morrison",
    "Emily Dickson","Stephen King"]

# create an acronym from the first letter of the author's names
letters = [ name[0] for name in authors ]
print(letters)


# ['E', 'L', 'F', 'T', 'E', 'S']
```

<br>

- Separating the characters in a string

```
# use list comprehension to print the letters in a string
letters = [ letter for letter in "20,000 Leagues Under The Sea"]

print(letters)


# ['2', '0', ',', '0', '0', '0', ' ', 'L', 'e', 'a', 'g', 'u', 'e', 's', ' ', 'U', 'n', 'd', 'e', 'r', ' ', 'T', 'h', 'e', ' ', 'S', 'e', 'a']
```

<br>

### Lower/Upper case converter using Python

<br>

- Changing a letter's case

```
lower_case = [ letter.lower() for letter in ['A','B','C'] ]
upper_case = [ letter.upper() for letter in ['a','b','c'] ]

print(lower_case, upper_case)


# ['a', 'b', 'c'] ['A', 'B', 'C']
```

<br>

### Print numbers only from a given string

<br>

- Identify numbers in a string using the isdigit() method

```
# user data entered as name and phone number
user_data = "Elvis Presley 987-654-3210"
phone_number = [ x for x in user_data if x.isdigit()]

print(phone_number)


# ['9', '8', '7', '6', '5', '4', '3', '2', '1', '0']
```

<br>

### Parsing a file using list comprehension

<br>

- Reading a poem with list comprehensions

```
# open the file in read-only mode
file = open("dreams.txt", 'r')
poem = [ line for line in file ]

for line in poem:
    print(line)


# Hold fast to dreams

# For if dreams die

# Life is a broken-winged bird

# That cannot fly.

# -Langston Hughs
```

<br>

### Using functions in list comprehensions

<br>

- Adding arguments to list comprehension

```
# list comprehension with functions
# create a function that returns a number doubled
def double(x):
    return x*2

nums = [double(x) for x in range(1,10)]
print(nums)


# [2, 4, 6, 8, 10, 12, 14, 16, 18]

----------------------------------------------------

# add a filter so we only double even numbers
even_nums = [double(x) for x in range(1,10) if x%2 == 0]
print(even_nums)


# [4, 8, 12, 16]


-----------------------------------------------------

nums = [x+y for x in [1,2,3] for y in [10,20,30]]
print(nums)

# [11, 21, 31, 12, 22, 32, 13, 23, 33]

```

<br>

### Conclusion

<br>

> Writing compact code is essential for maintaining programs and working with teams. 

> Learning to make use of advanced features like list comprehension will save time and improve productivity. 

> Not only will your colleagues thank you when your Python code is more concise and easier to read, but you'll thank yourself when you come back to a program you haven't worked on in months and the code is manageable.
