[Home](README.md)

<br>

# Topic

<br>

## Readings from [Pain vs. Suffering](https://codefellows.github.io/code-401-python-guide/curriculum/class-01/notes/pain_suffering)

<br>

> That price is pain, the pain of growth.

<br>

- In this course, one is expected to push themselve to their limits, if not beyond. They have to build upon what's taught in class, find their way through, and withstand all the stress and pressure they'll be put under.

<br>

> Suffering is pain without purpose. Pain with no higher goal. Pain with no dreams, no ambition, no aspiration.

<br>

- One has to remind themselves why they're doing this to themselves, remembering these aspects:
    - What’s your perspective?
    - Why are you doing this?
    - Do you want what comes at the end of this journey?
    - Are you doing this for you?

<br>

## Readings from [A beginner's guide to Big O Notation](https://rob-bell.net/2009/06/a-beginners-guide-to-big-o-notation)

<br>

> Big O notation is used in Computer Science to describe the performance or complexity of an algorithm. Big O specifically describes the worst-case scenario.

<br>

- O(1)
    - O(1) describes an algorithm that will always execute in the same time (or space) regardless of the size of the input data set.

- O(N)
    - O(N) describes an algorithm whose performance will grow linearly and in direct proportion to the size of the input data set.

- O(N²)
    - O(N²) represents an algorithm whose performance is directly proportional to the square of the size of the input data set.

- O(2^N)
    - O(2^N) denotes an algorithm whose growth doubles with each addition to the input data set.

- O(log N)
    - The iterative halving of data sets (over or below the mdeian) produce a growth curve that peaks at the beginning and slowly flattens out as the size of the data sets increase.

<br>

## Conclusion

<br>

- Names refer to data values.

- Names are reassigned independently.

- Names live until they have nothing referencing them anymore.

- Assignment never copies data (it'll still read the data stored in the memory).

- Data changes are visible through all names (mutable aliasing) >> They take the updated values of the names they were assigned values based on.

- Immutable values can't alias (ints, floats, strings and tuples) >> They do not take the updated values of the names they were assigned values based on.

- Changing an `int` >> rebinding.

- Changing a `list` >> mutating.

- Assignment is the same for all values (mutable and immutable).

- Changing (aliasing) makes it seem different.

- `x = x + y` is actually `x = x.__iadd__(y)`. This, uses the `iadd` method on the list class as:
    ```
    class List:
      def __iadd__(self, other):
      self.extend(other)
      return self
    ```
    This is rebinding values in place more or less >> value mutated.

- References can be more than just names `list[index]`, `Object Attributes`, `Keys and Values of Dictionaries`, ...

- Running a loop over a list, is reassigning over and over. Defining functions is assigning as well.

- Function Arguments are assignments (assigning values to parameters).

- Do not create functions that mutates arguments, make them return a new list instead.

- Names have scope but no type, while values have type but no scope.
