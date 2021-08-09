[Home](README.md)

<br>

# State and Props

<br>

## Readings from [Lists and Keys](https://reactjs.org/docs/lists-and-keys.html)

<br>

### Transforming Arrays Into Lists of Elements

<br>

> You can build collections of elements and include them in JSX using curly braces {}.

- Loop through the array using the `map()` function.
- Return a `<li>` element for each item.
- Include the entire listItems array inside a `<ul>`.
- Render it to the `DOM`.
- Assign a key to our list items inside `numbers.map()`.

<br>

### Keys

<br>

> Keys help React identify which items have changed, are added, or are removed. Keys should be given to the elements inside the array to give the elements a stable identity.

> The best way to pick a key is to use a string that uniquely identifies a list item among its siblings. Most often you would use IDs from your data as keys.

> You may use the item index as a key as a last resort.

<br>

#### Extracting Components with Keys

 <br>

> If you extract a ListItem component, you should keep the key on the <ListItem /> elements in the array rather than on the <li> element in the ListItem itself.

> A good rule of thumb is that elements inside the map() call need keys.

> Keys used within arrays should be unique among their siblings. However, they don’t need to be globally unique.

<br>

## Readings from [How to Use the Spread Operator (…) in JavaScript](https://medium.com/coding-at-dawn/how-to-use-the-spread-operator-in-javascript-b9e4a8b06fab)

<br>

### What is the spread operator?

<br>

> Spread syntax refers to the use of an ellipsis of three dots `…` to expand an iterable object into the list of arguments.

<br>

### What is ... used for?

<br>

- Use it to “spread” an array into separate arguments
- Copying an array
- Concatenating or combining arrays
- Using Math functions
- Using an array as arguments
- Adding an item to a list
- Adding to state in React
- Combining objects
- Converting NodeList to an array

<br>

## Conclusion

<br>

- What does .map() return?
  - A new array populated with the results of calling a provided function on every element in the calling array.

- If I want to loop through an array and display each value in JSX, how do I do that in React?
  - You can build collections of elements and include them in JSX using curly braces {`elements`}.

- Each list item needs a unique ____.
  - Key.

- What is the purpose of a key?
  - Keys help React identify which items have changed, are added, or are removed.

<br>

- What is the spread operator?
  - The use of an ellipsis of three dots `…` to expand an iterable object into the list of arguments.

- List 4 things that the spread operator can do.
  1. Copying an array.
  2. Concatenating or combining arrays.
  3. Using Math functions.
  4. Adding an item to a list.

- Give an example of using the spread operator to combine two arrays.

  ```

    let A = [1, 2, 3];
    let B = [4, 5, 6];
    console.log(...A,...B) // 1 2 3 4 5 6

  ```

- Give an example of using the spread operator to add a new item to an array.

  ```

    let A = [1, 2, 3];
    let B = [0, ...A];
    console.log(B) // [0, 1, 2, 3]

  ```

- Give an example of using the spread operator to combine two objects into one.

  ```
    
    let A = {a: 1}
    let B = {b: 2}
    let C = {...A, ...B}
    console.log(C) // {a: 1, b: 2}

  ```

<br>

- In the video, what is the first step that the developer does to pass functions between components?
  - He analyzed the situation and created the function where the target state is.

- In your own words, what does the increment function do?
  - Updates the counter of the name matching the cliked button's name.

- How can you pass a method from a parent component into a child component?
  - He passed it down just the way props get passed down from parent to child.

- How does the child component invoke a method that was passed to it from a parent component?
  - He used the method updating the component state to pass the name from it to the method from the parent component.
