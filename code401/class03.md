[Home](README.md)

<br>

# FileIO & Exceptions

<br>

## Readings from [Reading and Writing Files in Python](https://realpython.com/read-write-files-python/)

<br>

### What Is a File

<br>

> A file is a contiguous set of bytes used to store data.

<br>

> This data is organized in a specific format and can be anything as simple as a text file or as complicated as a program executable.

<br>

> These byte files are then translated into binary 1 and 0 for easier processing by the computer.

<br>

- File systems are composed of three main parts:
  - Header: metadata about the contents of the file (file name, size, type, and so on).
  - Data: contents of the file as written by the creator or editor.
  - End of file (EOF): special character that indicates the end of the file.

<br>

> What this data represents depends on the format specification used, which is typically represented by an extension.

<br>

### File Paths

<br>

- The file path is a string that represents the location of a file. It’s broken up into three major parts:
  - Folder Path: the file folder location on the file system where subsequent folders are separated by a forward slash / (Unix) or backslash \ (Windows).
  - File Name: the actual name of the file.
  - Extension: the end of the file path pre-pended with a period (.) used to indicate the file type.

<br>

> You can use the special characters double-dot (..) to move one directory up.

> The double-dot (..) can be chained together to traverse multiple directories above the current directory.

<br>

### Line Endings

<br>

> ASA standard states that line endings should use the sequence of the Carriage Return (CR or \r) and the Line Feed (LF or \n) characters (CR+LF or \r\n).

<br>

> The ISO standard however allowed for either the CR+LF characters or just the LF character.

<br>

> Windows uses the CR+LF characters to indicate a new line, while Unix and the newer Mac versions use just the LF character.

<br>

### Character Encodings

<br>

> An encoding is a translation from byte data to human readable characters.

> This is typically done by assigning a numerical value to represent a character. 

> The two most common encodings are the ASCII and UNICODE Formats. 

> ASCII can only store 128 characters, while Unicode can contain up to 1,114,112 characters.

> ASCII is actually a subset of Unicode (UTF-8), meaning that ASCII and Unicode share the same numerical to character values.

<br>

### Opening and Closing a File in Python

<br>

>  This is done by invoking the open() built-in function.

> open() has a single required argument that is the path to the file. 

> open() has a single return, the file object.

<br>

- There are two ways that you can use to ensure that a file is closed properly:
  - The first way to close a file is to use the try-finally block.
  - The second way to close a file is to use the with statement.

<br>

- There are three different categories of file objects:
  - Text files.
    - With these types of files, open() will return a TextIOWrapper file object.
  - Buffered binary files.
    - With these types of files, open() will return either a BufferedReader or BufferedWriter file object.
  - Raw binary files.
    - With these types of files, open() will return a FileIO file object.

<br>

### Reading and Writing Opened Files

<br>

- There are multiple methods that can be called on a file object to help you out:
  - `.read(size=-1)`
    - This reads from the file based on the number of size bytes. If no argument is passed or None or -1 is passed, then the entire file is read.
  - `.readline(size=-1)`
    - This reads at most size number of characters from the line. This continues to the end of the line and then wraps back around. If no argument is passed or None or -1 is passed, then the entire line (or rest of the line) is read.
  - `.readlines()`
    - This reads the remaining lines from the file object and returns them as a list.

<br>

### Iterating Over Each Line in the File

<br>

> A common thing to do while reading a file is to iterate over each line. Here’s an example of how to use the Python .readline() method to perform that iteration.

> you could iterate over each line in the file is to use the Python .readlines() method of the file object. Remember, .readlines() returns a list where each element in the list represents a line in the file.

<br>

- File objects have multiple methods that are useful for writing to a file:
  - `.write(string)`
    - This writes the string to the file.
  - `.writelines(seq)`
    - This writes the sequence to the file. No line endings are appended to each sequence item. It’s up to you to add the appropriate line ending(s).

<br>

### Working With Bytes

<br>

> This is done by adding the 'b' character to the mode argument.

> All of the same methods for the file object apply. However, each of the methods expect and return a bytes object instead.

<br>

### Tips and Tricks

<br>

> The `__file__` attribute is a special attribute of modules, similar to `__name__`.

<br>

### Appending to a File

<br>

> This is easily done by using the 'a' character for the mode argument.

<br>

### Creating Your Own Context Manager

<br>

> There may come a time when you’ll need finer control of the file object by placing it inside a custom class. 

> When you do this, using the with statement can no longer be used unless you add a few magic methods: `__enter__` and `__exit__`.

> `__enter__()` is invoked when calling the with statement. `__exit__()` is called upon exiting from the with statement block.

<br>

### Don’t Re-Invent the Snake

<br>

- wave: read and write WAV files (audio)

- aifc: read and write AIFF and AIFC files (audio)

- sunau: read and write Sun AU files

- tarfile: read and write tar archive files

- zipfile: work with ZIP archives

- configparser: easily create and parse configuration files

- xml.etree.ElementTree: create or read XML based files

- msilib: read and write Microsoft Installer files

- plistlib: generate and parse Mac OS X .plist files

- PyPDF2: PDF toolkit

- xlwings: read and write Excel files

- Pillow: image reading and manipulation

<br>

## Readings from [Python Exceptions: An Introduction](https://realpython.com/python-exceptions/)

<br>

### Exceptions versus Syntax Errors

<br>

> Syntax errors occur when the parser detects an incorrect statement.

> The arrow indicates where the parser ran into the syntax error.

<br>

> An exception error is a type of error that occurs whenever syntactically correct Python code results in an error.

> Instead of showing the message exception error, Python details what type of exception error was encountered.

<br>

### Raising an Exception

<br>

> We can use raise to throw an exception if a condition occurs. The statement can be complemented with a custom exception.

<br>

### The AssertionError Exception

<br>

> Instead of waiting for a program to crash midway, you can also start by making an assertion in Python. 

> We assert that a certain condition is met. If this condition turns out to be True, then that is excellent! The program can continue. 

> If the condition turns out to be False, you can have the program throw an AssertionError exception.

<br>

### The try and except Block: Handling Exceptions

<br>

> The try and except block in Python is used to catch and handle exceptions.

>  Python executes code following the try statement as a “normal” part of the program.

> The code that follows the except statement is the program’s response to any exceptions in the preceding try clause.

<br>

> When syntactically correct code runs into an error, Python will throw an exception error. 

> This exception error will crash the program if it is unhandled. The except clause determines how your program responds to exceptions.

> Catching Exception hides all errors…even those which are completely unexpected. 

<br>

### The else Clause

<br>

> In Python, using the else statement, you can instruct a program to execute a certain block of code only in the absence of exceptions.

<br>

### Cleaning Up After Using finally

<br>

> The finally clause cleans up after executing your code after executing it.

<br>

### Summing Up

<br>

- Raise allows you to throw an exception at any time.

- Assert enables you to verify if a certain condition is met and throw an exception if it isn’t.

- In the try clause, all statements are executed until an exception is encountered.

- Except is used to catch and handle the exception(s) that are encountered in the try clause.

- Else lets you code sections that should run only when no exceptions are encountered in the try clause.

- Finally enables you to execute sections of code that should always run, with or without any previously encountered exceptions.
