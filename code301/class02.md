[Home](README.md)

<br>

# State and Props

<br>

## Readings from [React: Component Lifecycle Events](https://medium.com/@joshuablankenshipnola/react-component-lifecycle-events-cb77e670a093)

<br>

### Component Lifecycle Events

<br>

> React lets you define components as classes or functions. The methods that you are able to use on these are called lifecycle events.

> These methods can be called during the lifecycle of a component, and they allow you to update the UI and application states.

<br>

### Phases of Component Lifecycle Events

<br>

![React_Component_Lifecycle_Events](imgs/React_Component_Lifecycle_Events.png)

<br>

#### Mounting

<br>

> When an instance of a component is being created and inserted into the DOM it occurs during the mounting phase.

- During Mounting, these lifecycles events occur in order: `Constructor`, `static getDerivedStateFromProps`, `render`, `componentDidMount`, and `UNSAFE_componentWillMount`.

<br>

#### Updating

<br>

> Anytime a component is updated or state changes then it is rerendered.

- During Update, these lifecycles events occur in order: `static getDerivedStateFromProps`, `shouldComponentUpdate`, `render`,
`getSnapshotBeforeUpdate`, `componentDidUpdate`,`UNSAFE_componentWillUpdate`, `UNSAFE_componentWillReceiveProps`.

<br>

#### Unmounting

<br>

> The final phase of the lifecycle if called when a component is being removed from the DOM.

- `componentWillUnmount` is the only lifecycle event during this phase.

<br>

## Conclusion

<br>

- Based off the diagram, what happens first, the `render` or the `componentDidMount`?
  - The `render`.

- What is the very first thing to happen in the lifecycle of React?
  - Mounting.

- Put the following things in the order that they happen: `componentDidMount`, `render`, `constructor`, `componentWillUnmount`, `React Updates`.
  1. `constructor`.
  2. `render`.
  3. `React Updates`.
  4. `componentDidMount`.
  5. `componentWillUnmount`.

- What does componentDidMount do?
  - This method is invoked immediately after a component is mounted. If you need to load anything using a network request or initialize the DOM, it should go here. This method is a good place to set up any subscriptions.

<br>

- What types of things can you pass in the props?
  - Floats, Integers and Strings datatypes (Titles, Sub-Titles, Counters, ...). Which are things will not change often and will initiate counting or such.

- What is the big difference between props and state?
  - Props passes into the component and it's handled  outside of the component, they contain things that will not change often.
  - States are handled inside of the component and must be updated inside the component, they contain things that will change and get updated often.

- When do we re-render our application?
  - When states change.

- What are some examples of things that we could store in state?
  - Elements updated by the user (forms, counters, ...).
