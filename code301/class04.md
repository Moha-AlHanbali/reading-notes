[Home](README.md)

<br>

# React and Forms

<br>

## Readings from [Forms](https://reactjs.org/docs/forms.html)

<br>

### Working with Forms in React

<br>

> HTML form elements work a bit differently from other DOM elements in React, because form elements naturally keep some internal state.

<br>

#### Controlled Components

<br>

> In HTML, form elements such as <input>, <textarea>, and <select> typically maintain their own state and update it based on user input.

> In React, mutable state is typically kept in the state property of components, and only updated with setState().

>We can combine the two by making the React state be the “single source of truth”.

> Then the React component that renders a form also controls what happens in that form on subsequent user input.

<br>

#### The textarea Tag

<br>

> In HTML, a <textarea> element defines its text by its children.

>In React, a <textarea> uses a value attribute instead. This way, a form using a <textarea> can be written very similarly to a form that uses a single-line input.

<br>

#### The Select Tag

<br>

> In HTML, <select> creates a drop-down list. For example, this HTML creates a drop-down list.

> React, instead of using this selected attribute, uses a value attribute on the root select tag. 

> Overall, this makes it so that <input type="text">, <textarea>, and <select> all work very similarly - they all accept a value attribute that you can use to implement a controlled component.

<br>

#### The file input Tag

<br>>

> In HTML, an <input type="file"> lets the user choose one or more files from their device storage to be uploaded to a server or manipulated by JavaScript via the File API.

<br>

#### The file input Tag

<br>

> When you need to handle multiple controlled input elements, you can add a name attribute to each element and let the handler function choose what to do based on the value of event.target.name.

<br>

#### The file input Tag

<br>

> Specifying the value prop on a controlled component prevents the user from changing the input unless you desire so. If you’ve specified a value but the input is still editable, you may have accidentally set value to undefined or null.

<br>

## Readings from [The Conditional (Ternary) Operator](https://codeburst.io/javascript-the-conditional-ternary-operator-explained-cac7218beeff)

<br>

### The if statement

<br>

> Using a conditional, like an if statement, allows us to specify that a certain block of code should be executed if a certain condition is met.

<br>

### The Conditional (Ternary) Operator

<br>

1. The condition is what you’re actually testing. The result of your condition should be `true` or `false` or at least coerce to either boolean value.

2. A `?` separates our conditional from our true value. Anything between the `?` and the `:` is what is executed if the condition evaluates to true.

3. Finally a `:` colon. If your condition evaluates to `false`, any code after the `colon` is executed.

  ```


    let person = {
    name: 'tony',
    age: 20,
    driver: null
    };
    person.driver = person.age >=16 ? 'Yes' : 'No'; // Yes

  ```

  <br>

## Conclusion

<br>

-  What is a ‘Controlled Component’?
  -  An input form element whose value is controlled by React in this way is called a `controlled component`.

- Should we wait to store the users responses from the form into state when they submit the form OR should we update the state with their responses as soon as they enter them? Why.
  - We update the state with their responses as soon as they enter them, we can now pass the value to other UI elements too, or reset it from other event handlers.

-  How do we target what the user is entering if we have an event handler on an input field?
  - When the value attribute is set on our form element, the displayed value will always be `this.state.value`, making React  handleChange run on every keystroke to update the React state, the displayed value will update as the user types.

<br>

-  Why would we use a ternary operator?
  - To yield the same results as if statement with shorter code.

-  Rewrite the following statement using a ternary statement:

  ```

      if(x===y){
        console.log(true);
      } else {
        console.log(false);
      }

      x === y ? console.log(true): console.log(false);

  ```
