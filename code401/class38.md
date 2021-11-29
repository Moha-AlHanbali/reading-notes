[Home](README.md)

<br>

# React 2

<br>

## Readings from [Conditional Rendering](https://reactjs.org/docs/conditional-rendering.html)

<br>

### Overview

<br>

> Conditional rendering in React works the same way conditions work in `JavaScript`.

> Use JavaScript operators like `if` or the conditional operator to create elements representing the current state, and let React update the UI to match them.

<br>

### Element Variables

<br>

> While declaring a variable and using an `if` statement is a fine way to conditionally render a component, sometimes you might want to use a shorter syntax.

> There are a few ways to inline conditions in `JSX`.

<br>

### Inline If with Logical && Operator

<br>

> You may embed expressions in `JSX` by wrapping them in curly braces.

> This includes the JavaScript logical `&&` operator.

> It can be handy for conditionally including an element.

> It works because in `JavaScript`, `true &&` expression always evaluates to expression, and `false &&` expression always evaluates to false.

> Therefore, if the condition is true, the element right after `&&` will appear in the output.

> If it is false, React will ignore and skip it.

> Note that returning a falsy expression will still cause the element after && to be skipped but will return the falsy expression. 

<br>

### Inline If-Else with Conditional Operator

<br>

> Another method for conditionally rendering elements inline is to use the `JavaScript` conditional operator condition `? true : false`.

<br>

### Preventing Component from Rendering

<br>

> In rare cases you might want a component to hide itself even though it was rendered by another component.

> To do this return `null` instead of its render output.

<br>

### Lists and Keys

<br>

> Given the code below, we use the `map()` function to take an array of numbers and double their values.

> We assign the new array returned by `map(`) to the variable doubled and log it.

<br>

### Rendering Multiple Components

<br>

> You can build collections of elements and include them in `JSX` using curly braces `{}`.

> Below, we loop through the numbers array using the `JavaScript map()` function.

> We return a `<li>` element for each item.

> Finally, we assign the resulting array of elements to listItems.

<br>

### Basic List Component

<br>

> Usually you would render lists inside a component.

> We can refactor the previous example into a component that accepts an array of numbers and outputs a list of elements.

> When you run this code, you’ll be given a warning that a `key` should be provided for list items.

> A `“key”` is a special string attribute you need to include when creating lists of elements.

<br>

### Keys

<br>

> `Keys` help React identify which items have changed, are added, or are removed.

> `Keys` should be given to the elements inside the array to give the elements a stable identity.

> The best way to pick a `key` is to use a string that uniquely identifies a list item among its siblings.

> When you don’t have stable IDs for rendered items, you may use the item `index` as a key as a last resort.

<br>

### Extracting Components with Keys

<br>

> `Keys` only make sense in the context of the surrounding array.

> If you extract a ListItem component, you should keep the key on the `<ListItem />` elements in the array rather than on the `<li>` element in the ListItem itself.

<br>

### Keys Must Only Be Unique Among Siblings

<br>

> `Keys` used within arrays should be unique among their siblings.

> However, they don’t need to be globally unique.

> We can use the same keys when we produce two different arrays.

> Keys serve as a hint to React but they don’t get passed to your components.

<br>

### Embedding map() in JSX

<br>

> `JSX` allows embedding any expression in curly braces so we could inline the `map()` result.

<br>

## Readings from [Forms](https://reactjs.org/docs/forms.html)

<br>

### Overview

<br>

> This form has the default `HTML` form behavior of browsing to a new page when the user submits the form.

> If you want this behavior in React, it just works.

> But in most cases, it’s convenient to have a JavaScript function that handles the submission of the form and has access to the data that the user entered into the form.

<br>

### Controlled Components

<br>

> In HTML, form elements such as `<input>`, `<textarea>`, and `<select>` typically maintain their own state and update it based on user input.

> In React, mutable state is typically kept in the state property of components, and only updated with `setState()`.

> Since the value attribute is set on our form element, the displayed value will always be `this.state.value`, making the React state the source of truth.

> Since `handleChange` runs on every keystroke to update the React state, the displayed value will update as the user types.

<br>

### The textarea Tag

<br>

> In React, a `<textarea>` uses a value attribute instead.

> This way, a form using a `<textarea>` can be written very similarly to a form that uses a single-line input.

<br>

### The select Tag

<br>

> React, instead of using this selected attribute, uses a value attribute on the root select tag.

> This is more convenient in a controlled component because you only need to update it in one place.

> Overall, this makes it so that `<input type="text">`, `<textarea>`, and `<select>` all work very similarly - they all accept a value attribute that you can use to implement a controlled component.

<br>

### The file input Tag

<br>

> In HTML, an `<input type="file">` lets the user choose one or more files from their device storage to be uploaded to a server or manipulated by `JavaScript` via the `File API`.

<br>

### Handling Multiple Inputs

<br>

> When you need to handle multiple controlled input elements, you can add a name attribute to each element and let the handler function choose what to do based on the value of `event.target.name`.

> Since `setState()` automatically merges a partial state into the current state, we only needed to call it with the changed parts.

<br>

### Controlled Input Null Value

<br>

> Specifying the value prop on a controlled component prevents the user from changing the input unless you desire so.

> If you’ve specified a value but the input is still editable, you may have accidentally set value to undefined or `null`.


<br>

## Readings from [Lifting State Up](https://reactjs.org/docs/lifting-state-up.html)

<br>

### Overview

<br>

> In React, sharing state is accomplished by moving it up to the closest common ancestor of the components that need it.

> This is called “lifting state up”.

> There should be a single “source of truth” for any data that changes in a React application.

> Usually, the state is first added to the component that needs it for rendering.

> Then, if other components also need it, you can lift it up to their closest common ancestor.

> Instead of trying to sync the state between different components, you should rely on the top-down data flow.

> Lifting state involves writing more “boilerplate” code than two-way binding approaches, but as a benefit, it takes less work to find and isolate bugs.

> Since any state “lives” in some component and that component alone can change it, the surface area for bugs is greatly reduced.

> Additionally, you can implement any custom logic to reject or transform user input.

>If something can be derived from either props or state, it probably shouldn’t be in the state.

> When you see something wrong in the UI, you can use React Developer Tools to inspect the props and move up the tree until you find the component responsible for updating the state.

<br>

## Readings from [Composition vs Inheritance](https://reactjs.org/docs/composition-vs-inheritance.html)

<br>

### Containment

<br>

> Some components don’t know their children ahead of time.

> This is especially common for components like Sidebar or Dialog that represent generic “boxes”.

> Anything inside the `<FancyBorder>` `JSX` tag gets passed into the FancyBorder component as a children prop.

> Since FancyBorder renders {props.children} inside a `<div>`, the passed elements appear in the final output.

> React elements like `<Contacts />` and `<Chat />` are just objects, so you can pass them as props like any other data.

> This approach may remind you of “slots” in other libraries but there are no limitations on what you can pass as props in React.

<br>

### Specialization

<br>

> Sometimes we think about components as being “special cases” of other components. For example, we might say that a WelcomeDialog is a special case of Dialog.

<br>

## Readings from [Thinking in React](https://reactjs.org/docs/thinking-in-react.html)

<br>

### Break The UI Into A Component Hierarchy

<br>

> The first thing you’ll want to do is to draw boxes around every component (and subcomponent) in the mock and give them all names.

> If you’re working with a designer, they may have already done this, so go talk to them! Their Photoshop layer names may end up being the names of your React components!

> But how do you know what should be its own component? Use the same techniques for deciding if you should create a new function or object.

> One such technique is the single responsibility principle, that is, a component should ideally only do one thing.

> If it ends up growing, it should be decomposed into smaller subcomponents.

> Since you’re often displaying a JSON data model to a user, you’ll find that if your model was built correctly, your UI (and therefore your component structure) will map nicely.

> That’s because UI and data models tend to adhere to the same information architecture.

> Separate your UI into components, where each component matches one piece of your data model.

<br>

### Build A Static Version in React

<br>

> Now that you have your component hierarchy, it’s time to implement your app.

> The easiest way is to build a version that takes your data model and renders the UI but has no interactivity.

> It’s best to decouple these processes because building a static version requires a lot of typing and no thinking, and adding interactivity requires a lot of thinking and not a lot of typing. We’ll see why.

> To build a static version of your app that renders your data model, you’ll want to build components that reuse other components and pass data using props.

> props are a way of passing data from parent to child.

> If you’re familiar with the concept of state, don’t use state at all to build this static version.

> State is reserved only for interactivity, that is, data that changes over time.

> Since this is a static version of the app, you don’t need it.

<br>

### Identify The Minimal (but complete) Representation Of UI State

<br>

> To make your UI interactive, you need to be able to trigger changes to your underlying data model. React achieves this with state.

> To build your app correctly, you first need to think of the minimal set of mutable state that your app needs.

> The key here is DRY: Don’t Repeat Yourself. Figure out the absolute minimal representation of the state your application needs and compute everything else you need on-demand.

<br>

### Identify Where Your State Should Live

<br>

> OK, so we’ve identified what the minimal set of app state is. Next, we need to identify which component mutates, or owns, this state.

> Remember: React is all about one-way data flow down the component hierarchy.

> It may not be immediately clear which component should own what state. This is often the most challenging part for newcomers to understand, so follow these steps to figure it out.

- For each piece of state in your application:
  - Identify every component that renders something based on that state.
  - Find a common owner component (a single component above all the components that need the state in the hierarchy).
  - Either the common owner or another component higher up in the hierarchy should own the state.
  - If you can’t find a component where it makes sense to own the state, create a new component solely for holding the state and add it somewhere in the hierarchy above the common owner component.

<br>

### Add Inverse Data Flow

<br>

> So far, we’ve built an app that renders correctly as a function of props and state flowing down the hierarchy. Now it’s time to support data flowing the other way: the form components deep in the hierarchy need to update the state.

> If you try to type or check the box in the previous version of the example (step 4), you’ll see that React ignores your input. This is intentional, as we’ve set the value prop of the input to always be equal to the state passed.

> The callbacks passed will call `setState()`, and the app will be updated.
