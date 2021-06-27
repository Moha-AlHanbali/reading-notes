[Home](README.md)

<br>

# JS Problem Domain, Objects, and the DOM - from Jon Duckett's books

<br>

## Readings from [Understanding The Problem Domain Is The Hardest Part Of Programming](https://simpleprogrammer.com/understanding-the-problem-domain-is-the-hardest-part-of-programming)

<br>

#### Why problem domains are hard?

- The author explains why he thinks problem domains are the hardest part of programming in his opinion
- He claims that creating a familiar problem domain, something like an analogy, you take away the hard part out of it.
- He uses puzzles with no recognizable images as an example:
  - Figure out what the major components of the picture are.
  - Sort the pieces by color or component.
  - Put together all the border pieces.
  - Put together each component of the picture from the piles you created.

> This all breaks down when you don’t have a picture with clear components that you can identify.

> The same thing happens when writing code.  Writing code is a lot like putting together a jigsaw puzzle.  We put together code with the purpose of building components that we have taken out of the “bigger picture” of the problem domain.

> The big issue is that many problem domains are like a puzzle with a blurry picture or no picture at all.

<br>

#### Programming is easy if you understand the problem domain

- He argues that knowing the extent of the domain makes it easy to solve, as you know what you're working towards.

> It is very difficult to solve a problem before you know the question.  It’s like buzzing in on Jeopardy before you hear the clue and shouting out random questions.

<br>

#### What can you do about it?

- The author advises you to do one of the following:
  - Make the problem domain easier.
  - Get better at understanding the problem domain.

> You can often make the problem domain easier by cutting out cases and narrowing your focus to a particular part of the problem.

> It is easy to fall into the trap of thinking you understand enough of the problem to get started coding it

<br>

## Readings from `Javascript and JQuery: Interactive Front-End Web Development`

### JS Chapter 3: Object Literals

<br>

#### What is an Object?

- `Object`s group together a set of variables and functions to create a model of a something you would recognize from the real world.
  - If a variable is part of an `Object`, it is called a `Property`. `Properties` tell us about the `Object`.
  - If a function is part of an `Object`, it is called a method. `Methods` represent tasks that are associated with the `Object`.
  - Like variables and named functions, `Properties` and `Methods` have a name and a value called a `Key`.
  - An `Object` cannot have two keys with the same name.
  - The value of a `Property` can be a string, number, Boolean, array, or even another `Object`.
  - The value of a method is always a function.

  <br>

  #### Creating an Object?

- One way to create an `Object` is `Litteral Notation`.

```
var object{
    // properties: 
    name: 'key',
    number: key,
    check: key,

    // methods:
    methodname= function(){
        code
   }
};
```

<br>

#### Accessing Objects

- Use `Dot Notation` to acces `Properties` or `Methods` inside `Objects`.

```
var variable1 = object.property;

var variable2 = object.method();
```

<br>

### JS Chapter 5: Document Object Model

<br>

#### DOM Tree

- The DOM Tree is a model of a Webpage created while the browser loads it.

![Body of HTML Page](imgs/BODY_OF_HTML_PAGE.PNG)

![Dom Tree](imgs/DOM_TREE.PNG)

- The Document Node
  - Every element, attribute, and piece of text in the HTML is represented by its own DOM node.
  - At the top of the tree a document node is added; it represents the entire page.
  - When you access any element, attribute, or text node, you navigate to it via the document node. It is the starting point for all visits to the DOM tree.

<br>

- Element Nodes
  - HTML elements describe the structure of an HTML page.
  - To access the DOM tree, you start by looking for elements. Once you find the element you want, then you can access its text and attribute nodes if you want to.
  - Every node is a descendant of the document node.

<br>

- Relationships between the document and all of the element nodes are described using the same terms as a family tree: parents, children, siblings, ancestors, and descendants.
- Each node is an object with methods and properties.
- Scripts access and update this DOM tree (not the source HTML file).
- Any changes made to the DOM tree are reflected in the browser.

<br>

- Attribute Nodes
  - The opening tags of HTML elements can carry attributes and these are represented by attribute nodes in the DOM tree.
- Attribute nodes are not children of the element thar carries them; they are part of that element.
- Once you access an element, there are specific JavaScript methods and properties to read or change that element's attributes.

<br>

- Text Nodes
  - Once you have accessed an element node, you can then reach the text within that element. This is stored in its own text node.
  - Text nodes cannot have children. If an element contains text and another child element, the child element is not a child of the text node but rather a child of the containing element.

<br>

#### Working with DOM Tree

- Accessing and updating the DOM tree involves two steps:
  - Locate the node that represents the element you want to work with.
  - Use its text content, child elements, and attributes.

<br>

- To select an indivisual element node
  - Use `get ElementByld ()`, `querySelector ()`, or select individual elements by traversing from one element to another within the DOM tree.

  ```

  object.ElementByld('elementID');
  
  ```

  <br>

- To select multiple elements (nodelists)
  - Use `getElementsByClassName()`, `getElementsByTagName()` or `querySelectorAll()`.

  ```

  object.getElementByClassName('elementClass');
    if (object.length>=1) {
      var variable = object.item(0); OR var variable = object[0]
    }


  let item= document.querySelectorAll(parameter);
  for (let i=0; i< item.length ; i++){
    item[i].className =  `string`;
  }

  ```

<br>

- To traverse between element nodes
  - When you have an element node, you can select another element in relation to it.
  - Traversing the DOM can be difficult because some browsers add a text node whenever they come across whitespace between elements.
  - Use `parentNode`, `previousSibling / nextSibling`, or `firstChild / lastChild`.



<br>

- Access/Update text content.
  - Using `nodeValue`.

- Work with HTML Content.
  - Use `innerHTML`, `create Element()`, `createTextNode()`, or `appendChild() / removeChild()`.
  - `innerHTML` can be used on any element node by:
    - Storing new content including markup as string in a variable.
    - Selecting the element you want to edit its' content.
    - Setting the element's innerHTML property to be the new string.
  - Adding Elements using DOM manipulation technique goes by:
    - Create the element using `create Element()`.
    - Give it content using `createTextNode()`.
    - Add to the child using `appendChild()`.


    ```
    Get Content:

    var Content = document.getElementByld('elementID').innerHTML;


    Set Content:

    document.getElementByld('elementID').innerHTML = Content;

    ```

<br>

- Access/Update attribute values.
  - Use `className /id`, or `hasAttr i bute(), getAttribute(), setAttri bute(), removeAttribute()`.

<br>

- Updating HTML content techniques:
  - `document.write()`
    - It is a quick and easy way to show beginners how content can be added to a page.
    - It only works when the page initially loads.
    - It can cause problems with XHTML pages that are strictly validated.
    - This method is very rarely used by programmers these days and is genera lly frowned upon.
  - `element.innerHTML`
    - You can use it to add a lot of new markup using less code than DOM manipulation methods.
    - It can be faster than DOM manipulation when adding a lot of new elements to a web page.
    - It is a simple way to remove all of the content from one element (by assigning it a blank string).
    - It should not be used to add content that has come from a user (such as a username or blog comment), as it can pose a significant security risk which is discussed over the next four pages.
    - It can be difficult to isolate single elements that you want to update within a larger DOM fragment.
    - Event handlers may no longer work as intended.
  - `DOM Manipulation`
    - It is suited to changing one element from a DOM fragment where there are many siblings.
    - It does not affect event handlers.
    - It easily allows a script to add elements incrementally (when you do not want to alter a lot of code at once).
    - If you have to make a lot of changes to the content of a page, it is slower than innerHTML.
    - You need to write more code to achieve the same thing compared with i nnerHTML.


<br>

#### Cross-Site Scripting (XSS) Attacks

- If you add HTML to a page using i nnerHTML (or several jQuery methods), you need to be aware of Cross-Site Scripting Attacks or XSS; otherwise, an attacker could gain access to your users' accounts.

<br>

- Defending against Cross-Site Scripting (XSS) Attacks:
  - Validate input going through the server
    - Only let visitors input the kind of characters they need to when supplying information. This is known as validation. Do not allow untrusted users to submit HTML markup or JavaScript.
    - Double-check validation on the server before displaying user content/storing it in a database. This is important because users could bypass validation in the browser by turning JavaScript off.
    - The database may safely contain markup and script from trusted sources (e.g., your content management system). This is because it does not try to process the code; it just stores it.
  - Escape Data coming from the Server & Database
    - Do not create DOM fragments containing HTML from untrusted sources. It should only be added as text once it has been escaped.
    - Make sure that you are only inserting content generated by users into certain parts of the template files.
    - As your data leaves the database, all potentially dangerous characters should be escaped.

<br>

- Make sure that your users can only input characters they need to use and limit where this content will be shown on the page. 
- Any content generated by users that contain characters that are used in code should be escaped on the server. You must control any markup added to the page.

<br>

#### Caching DOM Queries

> Methods that find DOM in the DOM Tree are called DOM Queries.

- Use a variable to store this query if you want to re-use it.
- Storing elements in variables mean to store the element's location inside DOM Tree into the variable.

<br>

