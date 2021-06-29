[Home](README.md)

<br>

# CSS Layout - from Jon Duckett's books

<br>

## Readings from `HTML & CSS: Design and Build Websites`

<br>

### CSS Chapter 15: Layout

<br>

#### Positioning Elements

> CSS treats each HTML element as if it is in its own box. This box will either be a block-level box or an inline box.

- Element Types 
  - Block Level Elements *(Start on new line)*
  `<h1>, <p>, <ul>, <li>, ...`
  - Inline Element *(Flow inbetween surrounding text)*
  `<img>, <b>, <i>, ...`
 
> If one block-level element sits inside another block-level element then the outer box is known as the containing or parent element.

![Containing Elements](imgs/CONTAINING_ELEMENTS.PNG)

> The orange lines in this diagram represent <div> elements. The header (containing the logo and navigation) are in one <div> element, the main content of the page is in another, and the footer is in a third. The <body> element is the containing element for these three <div> elements. The second <div> element is the containing element for two paragraphs of Latin text and images (represented by crossed squares).

<br>

- CSS has five schemes for positioning elements:

  - (Normal Flow) `static`.
    - Each block-level element sits on top of the next one. This is the default way in which browsers treat HTML elements,

  - (Relative Positioning) `relative`.
    - Moves an element in relation to where it would have been in normal flow.

  - (Absolute Positioning) `absolute`.
    - The box is taken out of normal flow and no longer affects the position of other elements on the page. (They act like it is not there.)
    - The box offset properties (top or bottom and left or right) specify where the element should appear in relation to its containing element.

  - (Fixed Positioning) `fixed`.
    - A type of absolute positioning that requires the position property to have a value of fixed.
    - It positions the element in relation to the browser window. Therefore, when a user scrolls down the page, it stays in the exact same place.

  - (Overlapping Elements) `z-index`.
    - Controls whichelement sits on top.

  - (Floating Elements) `float`.
    - Takes an element in normal flow and place it as far to the left or right of the containing element as possible.
    - Anything else that sits inside the containing element will flow around the element that is floated.

  - (Clearing Floats) `clear: left/right/both/none`.
    - The clear property allows you to say that no element (within the same containing element) should touch the left or righthand sides of a box.

- Use `width, float , and margin` to create multi column layouts.

<br>

#### Screen Resolution

> Resolution refers to the number of dots a screen shows per inch.

> Different visitors to your site will have different sized screens.

> Because screen sizes and display resolutions vary so much, webdesigners often try to create pages of around 960-1000 pixels wide.

<br>

#### Fixed Width Layouts

> Fixed width layout designs do not change size as the user increases or decreases the size of their browser window. Measurements tend to be given in pixels.

<br>

#### Liquid Layouts

> Liquid layout designs stretch and contract as the user increases or decreases the size of their browser window. They tend to use percentages.

<br>

#### Layout Grids

> Grids set consistent proportions and spaces between items which helps to create a professional looking design.

<br>

#### CSS Frameworks

> CSS frameworks provide the code for common tasks, such as creating layout grids, styling forms, creating printer-friendly versions of pages and so on. You can include the CSS framework code in your projects rather than writing the CSS from scratch.

- Use `@import` to link one stylesheet containing it to your `HTML`.
- Or `<link>` spearate stylesheets in the `HTML` document.
