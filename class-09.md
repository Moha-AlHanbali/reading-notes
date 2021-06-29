[Home](README.md)

<br>

# HTML Links, JS Functions, and Intro to CSS Layout - from Jon Duckett's books

<br>

## Readings from `HTML & CSS: Design and Build Websites`

<br>

### HTML Chapter 7: Forms

<br>

#### About Forms

- Forms are elements that allow you to collect information from visitors to
your site.

<br>

#### Form Control

- Adding Text
  - Text input (single-line)
  - Password input
  - Text area (multi-line)

- Making Choices
  - Radio buttons
  - Checkboxes
  - Drop-down boxes

- Submitting Forms
  - Submit buttons
  - Image buttons

- Uploading Files
  - File upload

<br>

#### Using Forms

1. A user fills in a form and then presses a button to submit the information to the server.
2. The name of each form control is sent to the server along with the value the user enters or selects.
3. The server processes the information using a programming language such as PHP, C#, VB.net, or Java. It may also store the information in a database.
4. The server creates a new page to send back to the browser based on the information received.

<br>

- A form may have several form controls, each gathering different information. The server needs to know which piece of inputted data corresponds with which form element.
- To differentiate between various pieces of inputted data, information is sent from the browser to the server using name/value pairs.

<br>

- Use `<form>` tag to contain form elements.
  - Every `<form>` element requires an action attribute.
  - Its value is the URL for the page on the server that will receive the information in the form when it is submitted.
  - Forms can be sent using one of two methods: get or post.

`<form action="URL" method="get/post">`

  <br>

- The `<input>` element is used to create several different form controls. The value of the type attribute determines what kind of input they will be creating.
  - Use `type="text"` attribute to set the value for text.
  - Use `name` attribue to allow  he server to know which form control each piece of data was entered into.
  - `maxlength` attribute limits the number of characters a user may enter into the text field.
  - `type="password"` creates a text box that acts just like a single-line text input, except the characters are blocked out.
  - `type="radio"` allow users to pick just one of a number of options.
  - `checked` attribute can be used to indicate which value (if any) should be selected when the page loads.
  - `value` attribute indicates the value that is sent to the server for the selected option. The value of each of the buttons in a group should be different
  - `type="checkbox"` allow users to select (and unselect) one or more options in answer to a question.
  - `type="file"` allow users to upload a file.
  - `type="submit"` is used to send a form to the server.
  - `type="image"` If you want to use an image for the submit button, you can give the type attribute a value of image.
  - `type="hidden"` These form controls are not shown on the page (although you can see them if you use the View Source option in the browser). They
  - `type="date"`.
  - `type="email"`.
  - `type="url"`.
  - `type="search"` On any text input, you can also use an attribute called `placeholder` whose value is text that will be shown in the text box until the user clicks in that area.
  
  <br>

- `<textarea>` is used to create a mutli-line text input. Unlike other input elements this is not an empty element.

  <br>

- `<select>` is used to create a drop down list box. It contains two or more `<option>` elements.
  - You can turn a drop down select box into a box that shows more than one option by adding the `size` attribute.
  - You can allow users to select multiple options from this list by adding the `multiple` attribute with a value of multiple.

  <br>

- `<option>` is used to specify the options that the user can select from.
  - `selected`attribute can be used to indicate the option that should be selected when the page loads.

  <br>

- `<button>` allow users more control over how their buttons appear, and to allow other elements to appear inside the button.

  <br>

- `<label>` can be used in two ways:
  - Wrap around both the text description and the form input.
  - Be kept separate from the form control and use the for attribute to indicate which form control it is a label for.
  - The `for` attribute states which form control the label belongs to.

  <br>

- `<fieldset>` group related form controls together inside it.

  <br>

- `<legend>` can come directly after the opening `<fieldset>` tag and contains a caption which helps identify the purpose of that group of form controls.


<br>


### CSS Chapter 14: Lists, Tables & Forms

<br>

#### Working with specific HTML elements

> Some CSS properties  were created to work with specific types of HTML elements, such as lists, tables, and forms.

- `list-style-type` allows you to control the shape or style of a bullet point.

- `list-style-image` specify an image to act as a bullet point using the list-style-image property.

- `list-style-position` indicates whether the marker should appear on the inside or the outside of the box containing the main points.

- `list-style` `shorthand for list styles.

- Table properties
  - `width`
  - `padding`
  - `text-transform` to convert the content of the table headers to uppercase
  - `letter-spacing, font-size` to add additional styling to the content of the table headers.
  - `border-top, border-bottom`
  - `text-align`
  - `background-color`
  - `:hover`
  - `empty-cells` 
  - `border-spacing, border-collapse` 

- Styling Forms
  - `font-size`
  - `color, background-color`
  - `border, border-radius`
  - `:focus` pseudo-class is used to change the background color of the text input when it is being used.
  - `:hover`
  - `background-image`
  - `text-shadow`
  - `border`

- Cusror Styles allows you to control the type of mouse cursor that should be displayed to users.
  - `auto`
  - `crosshair`
  - `default`
  - `pointer`
  - `move`
  - `text`
  - `wait`
  - `help` 
  - `url("cursor.gif");`

  <br>


## Readings from `Javascript and JQuery: Interactive Front-End Web Development`

<br>

### JS Chapter 6: Events

<br>

#### Events Types

- Events can be used to trigger a function in JavaScript code.

- When an event has occurred, it is often described as having fired or been raised.

- Events are said to t rigger a function or script. When the click event fires on the element in this diagram, it could trigger a script that enlarges the selected item.

- UI Events
  - `load, unload, error, resize, scroll`.

- Keyboard Events
  - `keydown, keyup, keypress`

- Mouse Events
  - `click, dbclick, mousedown, mouseup, mousemove, mouseover, mouseout`

  - Focus Events
    - `focus/focusin, blur/focusout`

- Form Events
  - `input, change, submit, reset, cut, copy, paste, select`


-  Mutation Events
  - `DOMSubtreeModified, DOMNodelnserted, DOMNodeRemoved, OOMNodelnsertedlntoDocument, DOMNodeRemovedFromOocument`

<br>

#### Triggering JS Code (Event Handling)

1. `SELECT ELEMENT` Select the element node(s) you want the script to respond to.
2. `SPEC! FY EVENT` Indicate (bind) which event on the selected node(s) will trigger the response.
3. `CALL CODE` State the code you want to run when the event occurs.

- To bind events use
  - `HTML` event handlers. (Avoid)
  - `DOM` event handlers.
    - `element.oneEvent = code;`.
  - `DOM` level 2 event listerners.
    - `element.addEventListener('event', functionName [, Boolean]);`
  
  <br>

  #### Event Flow

  - Event handlers/listeners be bound to parent elements (elements containing target).

  - In Event bubbling, event starts at the most specific node flowing outwards.

  - In Event Capturing, the event starts at the least specific node and flows inward towards the most specific one.

  - This matters when your elemnt and its' container/contained elements have handlers.

  <br>

  #### Event Object

  > When an event occurs, the event object tells you information about the event, and the element it happened upon.

- Events can happend on screen, page or even client.

  <br>

  #### Event Delegation

  > Creating event listeners for a lot of elements can slow down a page, but event flow allows you to listen for an event on a parent element.

   > By attaching an event listener to a containing element, you are only responding to one element (rather than having an event handler for each child element).

  #### Changing default behavior

> The event object has methods that change: the default behavior of an element and how the element's ancestors respond to the event.

 - Use `preventDefault()`and `stopPropagation()`.

 #### Responding to different events

 1. The DOM events specification is managed by the W3C.
 2. The HTMLS specification details events that browsers are expected to support that are specifically used with HTML.
 3. Browser manufacturers also implement some events as part of their Browser Object Model (BOM).

