[Home](README.md)

<br>

# Automation

<br>

## Readings from [Python Regular Expression Tutorial](https://www.datacamp.com/community/tutorials/python-regular-expression-tutorial)

<br>

### Overview

<br>

> Regular Expressions, often shortened as regex, are a sequence of characters used to check whether a pattern exists in a given text (string) or not.

> They are used at the server side to validate the format of email addresses or passwords during registration, used for parsing text data files to find, replace, or delete certain string, etc.

> Start with importing `re` Python library that supports regular expressions.

> Some very useful functions provided by the `re` library are: `compile()`, `search()`, `findall()`, `sub()` for search and replace, `split()`,

<br>

### Regular Expressions in Python

<br>

> `import re`.

<br>

### Basic Patterns: Ordinary Characters

<br>

> Ordinary characters can be used to perform simple exact matches:

```
pattern = r"Cookie"
sequence = "Cookie"
if re.match(pattern, sequence):
    print("Match!")
else: print("Not a match!")

# Match!
```

<br>

> The `match()` function returns a match object if the text matches the pattern. Otherwise, it returns `None`.

> The r at the start of the pattern Cookie is called a raw `string literal`. It changes how the `string literal` is interpreted. Such literals are stored as they appear.

> `\` is just a backslash when prefixed with an `r` rather than being interpreted as an `escape sequence`.

<br>

### Wild Card Characters: Special Characters

<br>

> Special characters are characters that do not match themselves as seen but have a special meaning when used in a regular expression.

> `.` A period, matches any single character except the newline character.

> `re.search(r'Co.k.e', 'Cookie').group()`: 'Cookie'

<br>

> `^` A caret Matches the start of the string.

> `re.search(r'^Eat', "Eat cake!").group()`: 'Eat'

<br>

> `$` Matches the end of string.

> `re.search(r'cake$', "Cake! Let's eat cake").group()`: 'cake'

<br>

> `[abc]` Matches a or b or c.

> `[a-zA-Z0-9]` Matches any letter from (a to z) or (A to Z) or (0 to 9).

> `re.search(r'[0-6]', 'Number: 5').group()`: '5'

> `re.search(r'Number: [^5]', 'Number: 0').group()`: 'Number: 0'

<br>

> `\` Backslash.

- If the character following the backslash is a recognized escape character, then the special meaning of the term is taken.
- Else if the character following the \ is not a recognized escape character, then the \ is treated like any other character and passed through (Scenario 2).
- \ can be used in front of all the metacharacters to remove their special meaning (Scenario 3).

> `re.search(r'Not a\sregular character', 'Not a regular character').group()`: 'Not a regular character'

> `re.search(r'Just a \regular character', 'Just a \regular character').group()`: 'Just a \regular character'

> `re.search(r'Just a \\sregular character', 'Just a \sregular character').group()`: 'Just a \\sregular character'

<br>

> There is a predefined set of special sequences that begin with '\' and are also very helpful when performing search and match.

> `\w ` Lowercase 'w'. Matches any single letter, digit, or underscore.

> `\W` Uppercase 'W'. Matches any character not part of \w (lowercase w).

> `print("Lowercase w:", re.search(r'Co\wk\we', 'Cookie').group())`: Lowercase w: Cookie

> `print("Uppercase W:", re.search(r'C\Wke', 'C@ke').group())`: Uppercase W: C@ke

> `print("Uppercase W won't match, and return:", re.search(r'Co\Wk\We', 'Cookie'))`: Uppercase W won't match, and return: None

<br>

> `\s` Lowercase 's'. Matches a single whitespace character like: space, newline, tab, return.

> `\S` Uppercase 'S'. Matches any character not part of \s (lowercase s).

> `print("Lowercase s:", re.search(r'Eat\scake', 'Eat cake').group())`: Lowercase s: Eat cake

> `print("Uppercase S:", re.search(r'cook\Se', "Let's eat cookie").group())`: Uppercase S: cookie

<br>

> `\d` Lowercase d. Matches decimal digit 0-9.

> `\D` Uppercase d. Matches any character that is not a decimal digit.

> `print("How many cookies do you want? ", re.search(r'\d+', '100 cookies').group())`: How many cookies do you want?  100

<br>

> The `+` symbol used after the `\d` in the example above is used for repetition.

> `\t` Lowercase t. Matches tab.

> `\n` Lowercase n. Matches newline.

> `\r` Lowercase r. Matches return.

> `\A` Uppercase a. Matches only at the start of the string. Works across multiple lines as well.

> `\Z` Uppercase z. Matches only at the end of the string.

> TIP: `^` and `\A` are effectively the same, and so are `$` and `\Z`. Except when dealing with `MULTILINE` mode.

<br>

> `\b` Lowercase b. Matches only the beginning or end of the word.

> `print("\\t (TAB) example: ", re.search(r'Eat\tcake', 'Eat    cake').group())`: \t (TAB) example:  Eat    cake

> `print("\\b match gives: ",re.search(r'\b[A-E]ookie', 'Cookie').group())`: \b match gives:  Cookie

<br>

### Repetitions

<br>

> `+` Checks if the preceding character appears one or more times starting from that position.

> `re.search(r'Co+kie', 'Cooookie').group()`: 'Cooookie'

<br>

> `*` Checks if the preceding character appears zero or more times starting from that position.

> `re.search(r'Ca*o*kie', 'Cookie').group()`: 'Cookie'

<br>

> `?` Checks if the preceding character appears exactly zero or one time starting from that position.

> `re.search(r'Colou?r', 'Color').group()`: 'Color'

<br>

> `{x}` Repeat exactly x number of times.

> `{x,}` Repeat at least x times or more.

> `{x, y}` Repeat at least x times but no more than y times.

> `re.search(r'\d{9,10}', '0987654321').group()`: '0987654321'

<br>

### Grouping in Regular Expressions

<br>

> The group feature of regular expression allows you to pick up parts of the matching text. Parts of a regular expression pattern bounded by parenthesis `()` are called groups.

> The parenthesis does not change what the expression matches, but rather forms groups within the matched sequence.

> he plain `match.group()` without any argument is still the whole matched text as usual.

> Another way of doing the same is with the usage of `<>` brackets instead. This will let you create named groups. 

> Named groups will make your code more readable. The syntax for creating named group is: `(?P<name>...)`.

> You can always access the named groups using numbers instead of the name. 

```
statement = 'Please contact us at: support@datacamp.com'
match = re.search(r'([\w\.-]+)@([\w\.-]+)', statement)
if statement:
  print("Email address:", match.group()) # The whole matched text
  print("Username:", match.group(1)) # The username (group 1)
  print("Host:", match.group(2)) # The host (group 2)

-----------------------------------------------------------------------

statement = 'Please contact us at: support@datacamp.com'
match = re.search(r'(?P<email>(?P<username>[\w\.-]+)@(?P<host>[\w\.-]+))', statement)
if statement:
  print("Email address:", match.group('email'))
  print("Username:", match.group('username'))
  print("Host:", match.group('host'))


# Same result in both cases

# Email address: support@datacamp.com
# Username: support
# Host: datacamp.com
```

<br>

### Greedy vs. Non-Greedy Matching

<br>

> When a special character matches as much of the search sequence (string) as possible, it is said to be a `Greedy Match`.

> It is the normal behavior of a regular expression, but sometimes this behavior is not desired.

```
pattern = "cookie"
sequence = "Cake and cookie"

heading  = r'<h1>TITLE</h1>'
re.match(r'<.*>', heading).group()

# '<h1>TITLE</h1>'

```

<br>

> The pattern `<.*>` matched the whole string, right up to the second occurrence of `>`.

> Adding `?` after the qualifier makes it perform the match in a non-greedy or minimal fashion; That is, as few characters as possible will be matched. When you run `<.*>`, you will only get a match with `<h1>`.

<br>

### Function provided by 're'

<br>

> The `re` library in Python provides several functions to make your tasks easier.

> You have already seen some of them, such as the `re.search()`, `re.match()`.

> None is different from finding a zero-length match at some point in the string.

> `compile(pattern, flags=0)`: > Regular expressions are handled as strings by Python. However, with `compile()`, you can computer a regular expression pattern into a regular expression object.


> `search(pattern, string, flags=0)`: With this function, you scan through the given string/sequence, looking for the first location where the regular expression produces a match.

> `match(pattern, string, flags=0)`: Returns a corresponding match object if zero or more characters at the beginning of string match the pattern. Else it returns None, if the string does not match the given pattern.

> `findall(pattern, string, flags=0)`: Finds all the possible matches in the entire sequence and returns them as a list of strings. Each returned string represents one match.

> `finditer(string, [position, end_position])`:  it finds all the possible matches in the entire sequence but returns regex match objects as an iterator.

> `sub(pattern, repl, string, count=0, flags=0)`: It returns the string obtained by replacing or substituting the leftmost non-overlapping occurrences of pattern in string by the replacement repl. 

> `subn(pattern, repl, string, count=0)`:  is similar to `sub()`. However, it returns a tuple containing the new string value and the number of replacements that were performed in the statement.

> `split(string, [maxsplit = 0])`: This splits the strings wherever the pattern matches and returns a list.

> `start()`: Returns the starting index of the match.

> `end()`: Returns the index where the match ends.

> `span()`: Return a tuple containing the (start, end) positions of the match.

<br>

> The `match()` function checks for a match only at the beginning of the string (by default).

> The `search()` function checks for a match anywhere in the string.

<br>

### Compilation Flags

<br>

> `IGNORECASE (I)`: Allows case-insensitive matches.

> `DOTALL (S)`: Allows . to match any character, including newline.

> `MULTILINE (M)`: Allows start of string (^) and end of string ($) anchor to match newlines as well.

> `VERBOSE (X)`: Allows you to write whitespace and comments within a regular expression to make it more readable.

<br>

## Readings from [shutil — High-level File Operations](https://pymotw.com/3/shutil/)

<br>

### Overview

<br>

> The shutil module includes high-level file operations such as copying and archiving.

<br>

### Copying Files

<br>

> `copyfile()` copies the contents of the source to the destination and raises IOError if it does not have permission to write to the destination file.

> `copy2()` works like `copy()`, but includes the access and modification times in the metadata copied to the new file.

<br>

### Copying File Metadata¶

<br>

> By default when a new file is created under Unix, it receives permissions based on the umask of the current user. To copy the permissions from one file to another, use `copymode()`.

> To copy other metadata about the file use `copystat()`.

<br>

### Working With Directory Trees

<br>

> `shutil` includes three functions for working with directory trees.

> To copy a directory from one place to another, use `copytree()`.

> It recurses through the source directory tree, copying files to the destination.

> The destination directory must not exist in advance.

> To remove a directory and its contents, use `rmtree()`.

<br>

### Finding Files   

<br>

> The `which()` function scans a search path looking for a named file.

> The typical use case is to find an executable program on the shell’s search path defined in the environment variable PATH.

<br>

### Archives

<br>

> Python’s standard library includes many modules for managing archive files such as tarfile and zipfile.

> There are also several higher-level functions for creating and extracting archives in shutil.

> `get_archive_formats() `returns a sequence of names and descriptions for formats supported on the current system.

> Use `make_archive()` to create a new archive file.

> Its inputs are designed to best support archiving an entire directory and all of its contents, recursively.

> Extract the archive with `unpack_archive()`, passing the archive file name and optionally the directory where it should be extracted.

> If no directory is given, the current directory is used.

<br>

### File System Space

<br>

> It can be useful to examine the local file system to see how much space is available before performing a long running operation that may exhaust that space.

> `disk_usage()` returns a tuple with the total space, the amount currently being used, and the amount remaining free.

> The values returned by `disk_usage()` are the number of bytes, so the example program converts them to more readable units before printing them.
