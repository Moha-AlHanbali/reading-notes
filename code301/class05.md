[Home](README.md)

<br>

# Putting it all together

<br>

## Readings from [Thinking in React](https://reactjs.org/docs/thinking-in-react.html)

<br>

### Break The UI Into A Component Hierarchy

<br>

- A component should ideally only do one thing. If it ends up growing, it should be decomposed into smaller subcomponents.

- UI and data models tend to adhere to the same information architecture. Separate your UI into components, where each component matches one piece of your data model.

- Components that appear within another component should be a child in the hierarchy.

<br>

### Build A Static Version in React

<br>

- The easiest way is to build a version that takes your data model and renders the UI but has no interactivity.

- Build components that reuse other components and pass data using props. Props are a way of passing data from parent to child.   Don’t use state at all to build this static version. 

- It’s usually easier to go top-down, and on larger projects, it’s easier to go bottom-up and write tests as you build.

<br>

### Identify The Minimal (but complete) Representation Of UI State

<br>

- Figure out the absolute minimal representation of the state your application needs and compute everything else you need on-demand. 

- The key here is DRY: Don’t Repeat Yourself.

<br>

### Identify Where Your State Should Live

<br>

- Identify every component that renders something based on that state.

- Find a common owner component (a single component above all the components that need the state in the hierarchy).

- Either the common owner or another component higher up in the hierarchy should own the state.

- If you can’t find a component where it makes sense to own the state, create a new component solely for holding the state and add it somewhere in the hierarchy above the common owner component.

<br>

### Add Inverse Data Flow

<br>

- Whenever the user changes the form, we update the state to reflect the user input. 

- Since components should only update their own state, parent will pass callbacks to child that will fire whenever the state should be updated. 

<br>

## Conclusion

<br>

-  How would you break a mock into a component heirarchy?
    - Draw boxes around every component (and subcomponent) in the mock and give them all names.

-  What is the single responsibility principle and how does it apply to components?
    - A component should ideally only do one thing. If it ends up growing, it should be decomposed into smaller subcomponents.

-  What does it mean to build a ‘static’ version of your application?
    - A version that takes your data model and renders the UI but has no interactivity.

-  Once you have a static application, what do you need to add?
    - An absolute minimal representation of the state your application needs and compute everything else you need on-demand.

-  What are the three questions you can ask to determine if something is state?
    1. Is it passed in from a parent via props? If so, it probably isn’t state.
    2. Does it remain unchanged over time? If so, it probably isn’t state.
    3. Can you compute it based on any other state or props in your component? If so, it isn’t state.

-  How can you identify where state needs to live?
    1. Identify every component that renders something based on that state.
    2. Find a common owner component (a single component above all the components that need the state in the hierarchy).
    3. Either the common owner or another component higher up in the hierarchy should own the state.
    4. If you can’t find a component where it makes sense to own the state, create a new component solely for holding the state and add it somewhere in the hierarchy above the common owner component.
