[Home](README.md)

<br>

# React 1

<br>

## Readings from [ES6 Syntax and Feature Overview](https://www.taniarascia.com/es6-syntax-and-feature-overview/)

<br>

### Variables and constant feature comparison

<br>

Keyword           | Scope            | Hoisting         | Can Be Reassigned  | Can Be Redeclared
------------------|------------------|------------------|--------------------|------------------
var               | Function scope   | Yes              | Yes                | Yes
let               | Block scope      | No               | Yes                | No
const             | Block scope      | No               | No                 | No

<br>

### Arrow functions

<br>

> `let func = (a, b, c) => {} // parentheses required with multiple parameters`.

<br>

### Template literals

<br>

> ``let str = `Release Date: ${date}``.

<br>

### Method definition shorthand

<br>

```js
let obj = {
  a(c, d) {},
  b(e, f) {},
}
```

<br>

### Array iteration

<br>

```js
for (let i of arr) {
  console.log(i)
}
```

<br>

### Classes/constructor functions

<br>

```js
class Func {
  constructor(a, b) {
    this.a = a
    this.b = b
  }

  getSum() {
    return this.a + this.b
  }
}

let x = new Func(3, 4)
```

<br>

### Inheritance

<br>

```js
class Inheritance extends Func {
  constructor(a, b, c) {
    super(a, b)

    this.c = c
  }

  getProduct() {
    return this.a * this.b * this.c
  }
}

let y = new Inheritance(3, 4, 5)
```

<br>

### Modules - export/import

<br>

```js
export {func, obj, x}

import {func, obj, x} from './export.js'
```

<br>

### Promises/Callbacks

<br>

```js
let doSecond = () => {
  console.log('Do second.')
}

let doFirst = new Promise((resolve, reject) => {
  setTimeout(() => {
    console.log('Do first.')

    resolve()
  }, 500)
})

doFirst.then(doSecond)


function makeRequest(method, url) {
  return new Promise((resolve, reject) => {
    let request = new XMLHttpRequest()

    request.open(method, url)
    request.onload = resolve
    request.onerror = reject
    request.send()
  })
}

makeRequest('GET', 'https://url.json')
  .then((event) => {
    console.log(event.target.response)
  })
  .catch((err) => {
    throw new Error(err)
  })
```

<br>

## Readings from [Introducing JSX](https://reactjs.org/docs/introducing-jsx.html)

<br>

### Why JSX?

<br>

> React doesn’t require using `JSX`, but most people find it helpful as a visual aid when working with UI inside the JavaScript code.

> It also allows React to show more useful error and warning messages.

<br>

### Embedding Expressions in JSX

<br>

> You can put any valid `JavaScript` expression inside the curly braces in `JSX`.

> We split `JSX` over multiple lines for readability.

> While it isn’t required, when doing this, we also recommend wrapping it in parentheses to avoid the pitfalls of automatic semicolon insertion.

<br>

### JSX is an Expression Too

<br>

> After compilation, `JSX` expressions become regular JavaScript function calls and evaluate to JavaScript objects.

> This means that you can use `JSX` inside of if statements and for loops, assign it to variables, accept it as arguments, and return it from functions.

```jsx
function getGreeting(user) {
  if (user) {
    return <h1>Hello, {formatName(user)}!</h1>;
  }
  return <h1>Hello, Stranger.</h1>;
}
```

<br>

### Specifying Attributes with JSX

<br>

> You may use quotes to specify string literals as attributes.

> You may also use curly braces to embed a JavaScript expression in an attribute:

> Don’t put quotes around curly braces when embedding a JavaScript expression in an attribute.

> You should either use quotes (for string values) or curly braces (for expressions), but not both in the same attribute.

<br>

### Specifying Children with JSX

<br>

> If a tag is empty, you may close it immediately with `/>`.

> `JSX` tags may contain children.

```jsx
const element = (
  <div>
    <h1>Hello!</h1>
    <h2>Good to see you here.</h2>
  </div>
);
```

<br>

### JSX Prevents Injection Attacks

<br>

> By default, `React DOM` escapes any values embedded in `JSX` before rendering them.

> Thus it ensures that you can never inject anything that’s not explicitly written in your application.

> Everything is converted to a string before being rendered.

> This helps prevent `XSS (cross-site-scripting)` attacks.

<br>

### JSX Represents Objects

<br>

> Babel compiles `JSX` down to `React.createElement()` calls.

> `React.createElement()` performs a few checks to help you write bug-free code but essentially it creates an object.

> These objects are called “React elements”. You can think of them as descriptions of what you want to see on the screen.

> React reads these objects and uses them to construct the DOM and keep it up to date.

<br>

## Readings from [Rendering Elements](https://reactjs.org/docs/rendering-elements.html)

<br>

### Rendering an Element into the DOM

<br>

> We call this a “root” DOM node because everything inside it will be managed by `React DOM`.

> Applications built with just React usually have a single root DOM node.

> If you are integrating React into an existing app, you may have as many isolated root DOM nodes as you like.

> To render a React element into a root DOM node, pass both to `ReactDOM.render()`.

<br>

### Updating the Rendered Element

<br>

> React elements are immutable. Once you create an element, you can’t change its children or attributes.

> With our knowledge so far, the only way to update the UI is to create a new element, and pass it to `ReactDOM.render()`.

<br>

### React Only Updates What’s Necessary

<br>

> React DOM compares the element and its children to the previous one, and only applies the DOM updates necessary to bring the DOM to the desired state.

<br>

## Readings from [Components and Props](https://reactjs.org/docs/components-and-props.html)

<br>

### Function and Class Components

<br>

> This function is a valid React component because it accepts a single “props” (which stands for properties) object argument with data and returns a React element.

> We call such components “function components” because they are literally JavaScript functions.

<br>

### Rendering a Component

<br>

> When React sees an element representing a user-defined component, it passes `JSX` attributes and children to this component as a single object.

> We call this object `props`.

<br>

### Composing Components

<br>

> Components can refer to other components in their output.

> This lets us use the same component abstraction for any level of detail.

> A button, a form, a dialog, a screen: in React apps, all those are commonly expressed as components.

> Typically, new React apps have a single App component at the very top.

> However, if you integrate React into an existing app, you might start bottom-up with a small component like Button and gradually work your way to the top of the view hierarchy.

<br>

### Extracting Components

<br>

> Extracting components might seem like grunt work at first, but having a palette of reusable components pays off in larger apps

> A good rule of thumb is that if a part of your UI is used several times, or is complex enough on its own, it is a good candidate to be extracted to a separate component.

<br>

### Props are Read-Only

<br>

> All React components must act like pure functions with respect to their props.

<br>

## Readings from [State and Lifecycle](https://reactjs.org/docs/state-and-lifecycle.html)

<br>

### Converting a Function to a Class

<br>

- Create an ES6 class, with the same name, that extends React.Component.
- Add a single empty method to it called `render()`.
- Move the body of the function into the `render()` method.
- Replace props with `this.props` in the `render()` body.
- Delete the remaining empty function declaration.

<br>

### Adding Local State to a Class

<br>

- Replace `this.props.something` with this.state.date in the `render()` method.
- Add a class constructor that assigns the initial `this.state`.
- Remove the date prop from the `<TAG />` element:

<br>

### Adding Lifecycle Methods to a Class

<br>

> The `componentDidMount()` method runs after the component output has been rendered to the DOM.

> While `this.props` is set up by React itself and this.state has a special meaning, you are free to add additional fields to the class manually if you need to store something that doesn’t participate in the data flow.

> We will tear down the timer in the `componentWillUnmount()` lifecycle method.

> Use `this.setState()` to schedule updates to the component local state.

<br>

### Using State Correctly

<br>

#### Do Not Modify State Directly

<br>

> Use `setState()`.

> The only place where you can assign `this.state` is the constructor.

<br>

#### State Updates May Be Asynchronous

> React may batch multiple `setState()` calls into a single update for performance.

> Because `this.props` and this.state may be updated asynchronously, you should not rely on their values for calculating the next state.

> To fix it, use a second form of `setState()` that accepts a function rather than an object.

> That function will receive the previous state as the first argument, and the props at the time the update is applied as the second argument.

<br>

#### State Updates are Merged

<br>

> When you call `setState()`, React merges the object you provide into the current state.

> Then you can update them independently with separate `setState()` calls.

<br>

### The Data Flows Down

<br>

> Neither parent nor child components can know if a certain component is stateful or stateless, and they shouldn’t care whether it is defined as a function or a class.

> This is why state is often called local or encapsulated. It is not accessible to any component other than the one that owns and sets it.

> This is commonly called a “top-down” or “unidirectional” data flow.

> Any state is always owned by some specific component, and any data or UI derived from that state can only affect components “below” them in the tree.

<br>

## Readings from [Handling Events](https://reactjs.org/docs/handling-events.html)

<br>

### Overview

<br>

> React events are named using camelCase, rather than lowercase.

> With `JSX` you pass a function as the event handler, rather than a string.

> Another difference is that you cannot return false to prevent default behavior in React.

> You must call preventDefault explicitly.

> When using React, you generally don’t need to call `addEventListener` to add listeners to a DOM element after it is created.

> Instead, just provide a listener when the element is initially rendered.

> When you define a component using an ES6 class, a common pattern is for an event handler to be a method on the class.

<br>

> You have to be careful about the meaning of this in `JSX` callbacks.

> In `JavaScript`, class methods are not bound by default.

<br>

### Passing Arguments to Event Handlers

<br>

> Inside a loop, it is common to want to pass an extra parameter to an event handler.

> The above two lines are equivalent, and use arrow functions and `Function.prototype.bind respectively`.

<br>

## Readings from [Utility-First](https://tailwindcss.com/docs/utility-first)

<br>

### Overview

<br>

> Traditionally, whenever you need to style something on the web, you write CSS.

> With Tailwind, you style elements by applying pre-existing classes directly in your HTML.

> This approach allows us to implement a completely custom component design without writing a single line of custom CSS.

- But once you’ve actually built something this way, you’ll quickly notice some really important benefits:
  - `You aren’t wasting energy inventing class names`:
    - No more adding silly class names like sidebar-inner-wrapper just to be able to style something, and no more agonizing over the perfect abstract name for something that’s really just a flex container.
  - `Your CSS stops growing`:
    - Using a traditional approach, your CSS files get bigger every time you add a new feature. With utilities, everything is reusable so you rarely need to write new CSS.
  - `Making changes feels safer`:
    - CSS is global and you never know what you’re breaking when you make a change. Classes in your HTML are local, so you can change them without worrying about something else breaking.

<br>

### Why not just use inline styles?

<br>

- Using utility classes has a few important advantages over inline styles:
  - `Designing with constraints`:
    - Using inline styles, every value is a magic number. With utilities, you’re choosing styles from a predefined design system, which makes it much easier to build visually consistent UIs.
  - `Responsive design`:
    - You can’t use media queries in inline styles, but you can use Tailwind’s responsive utilities to build fully responsive interfaces easily.
  - `Hover, focus, and other states`:
    - Inline styles can’t target states like hover or focus, but Tailwind’s state variants make it easy to style those states with utility classes.

<br>

### Maintainability concerns

<br>

> The biggest maintainability concern when using a utility-first approach is managing commonly repeated utility combinations.

> This is easily solved by extracting components, usually as template partials or components.

> You can also use Tailwind’s `@apply` feature to create CSS abstractions around common utility patterns.

<br>

## Readings from [Create a Next.js App](https://nextjs.org/learn/basics/create-nextjs-app)

<br>

### Overview

<br>

- To build a complete web application with React from scratch, there are many important details you need to consider:
  - Code has to be bundled using a bundler like webpack and transformed using a compiler like Babel.
  - You need to do production optimizations such as code splitting.
  - You might want to statically pre-render some pages for performance and SEO. You might also want to use server-side rendering or client-side rendering.
  - You might have to write some server-side code to connect your React app to your data store.

<br>

### Next.js: The React Framework

<br>

> Enter Next.js, the React Framework. Next.js provides a solution to all of the above problems.

> But more importantly, it puts you and your team in the pit of success when building React applications.

- Next.js aims to have best-in-class developer experience and many built-in features, such as:
  - An intuitive page-based routing system (with support for dynamic routes)
  - Pre-rendering, both static generation (SSG) and server-side rendering (SSR) are supported on a per-page basis
  - Automatic code splitting for faster page loads
  - Client-side routing with optimized prefetching
  - Built-in CSS and Sass support, and support for any CSS-in-JS library
  - Development environment with Fast Refresh support
  - API routes to build API endpoints with Serverless Functions
  - Fully extendable

<br>

### Setup

<br>

> If you don’t have `Node.js` installed, install it from here. You’ll need `Node.js` version 10.13 or later.

> You’ll be using your own text editor and terminal app for this tutorial.

<br>

### Create a Next.js app

<br>

> To create a `Next.js` app, open your terminal, cd into the directory you’d like to create the app in, and run the following command:

> `npx create-next-app nextjs-blog --use-npm --example "https://github.com/vercel/next-learn/tree/master/basics/learn-starter"`.

<br>

### Run the development server

<br>

> You now have a new directory called nextjs-blog. Let’s cd into it:

> `cd nextjs-blog`

> `npm run dev`

<br>

### Welcome to Next.js

<br>

> You should see a page like this when you access `http://localhost:3000`.

> This is the starter template page which shows some helpful information about `Next.js`.

<br>

### Editing the Page

<br>

> Make sure the `Next.js` development server is still running.

> Open `pages/index.js` with your text editor.

> Find the text that says “Welcome to” under the `<h1>` tag and change it to “Learn”.

> Save the file.

> The Next.js development server has Fast Refresh enabled.
