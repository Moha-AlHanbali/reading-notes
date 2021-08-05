[Home](README.md)

<br>

# Object-Oriented Programming, HTML Tables - from Jon Duckett's books

<br>

## Readings from [Domain Modeling](https://github.com/codefellows/domain_modeling#domain-modeling)

<br>

#### What is Domain Modeling

> Domain modeling is the process of creating a conceptual model in code for a specific problem.

> A model describes the various entities, their attributes and behaviors, as well as the constraints that govern the problem domain. 

>  An entity that stores data in properties and encapsulates behaviors in methods is commonly referred to as an object-oriented model.

<br>

#### Define a constructor and initialize properties

> To define the same properties between many objects, you'll want to use a constructor function.

```
//parameter1 and parameter2 are object properties

let constructor = function(parameter1, parameter2){
this.parameter1 = parameter1;
this.parameter2 = parameter2;
};

let variable1 = new constructor(newParameter1, newParameter12);
let variable2 = new constructor(newParameter1, newParameter12);
```

<br>

- The `constructor` function is defined using a function expression.
- The `variable` is declared and then assigned a `function` and `parameters`.
- When the function is called, the data inside these `parameters` are stored inside `properties`.
- `Objects` are instantiated with the `new` keyword and their `properties` are initialized by calling `constructor` function.
- After being instantiated and initialized, these `objects` are stored inside the `variables`.

<br>

1. The `new` keyword instantiates (i.e. creates) an object.
2. The `constructor` function initializes `properties` inside that `object` using the this `variable`.
3. The `object` is stored in a `variable` for later use.

<br>

```
let constructor = function(parameter1, parameter2){
this.parameter1 = parameter1;
this.parameter2 = parameter2;
};

constructor.prototype.method(){

};

let variable1 = new constructor(newParameter1, newParameter12);
let variable2 = new constructor(newParameter1, newParameter12);
```

- `Methods` can be added to a `constructor` function's `prototype`.
- You can substitute in the `prototype` to do the work.
- When an `object` is asked to run a `method`, it searches through all of its own `methods`. When it doesn't find the `method` there, it then searches through all of the `methods` on its `prototype object`. When it finds it on its `prototype object`, it will calls the `method`, passing in `parameters` as the `arguments`.

<br>

#### Summary

> Domain modeling is the process of creating a conceptual model for a specific problem.

1. When modeling a single entity that'll have many instances, build self-contained objects with the same attributes and behaviors.
2. Model its attributes with a constructor function that defines and initializes properties.
3. Model its behaviors with small methods that focus on doing one job well.
4. Create instances using the new keyword followed by a call to a constructor function.
5. Store the newly created object in a variable so you can access its properties and methods from outside.
6. Use the this variable within methods so you can access the object's properties and methods from inside.
 
<br>

## Readings from `HTML & CSS: Design and Build Websites`

<br>

### HTML Chapter 6: Tables

<br>

#### Using Tables in HTML

> A table represents information in a grid format.

- Use `<table>` tag to create a table.
- Start each row with Table row `<tr>` tag.
- Follow `<tr>` with Table data `<td>`, one for each cell.
- Use Table heading `<th>` to represent the heading for the table or for either a column or a row using `<th scope="col"/"row">`.
- In long tables cases
  - Table head`<th>` should be inside `<thead>`.
  - Table body should be inside `<tbody>`.
  - Table footer should be inside `<tfoot>`.
- Use `<td rowspan/colspan="2">` to span a cell in more than one space.
- Add attributes to table tags in this format `<th width="000" bgcolor="#FFFFFF">`.


```
<table>
<tr>
<th> Heading </th>
<td> Item1 </td>
<td> Item2 </td>
<td> Item3 </td>
</tr>
</table>
```

<br>


## Readings from `Javascript and JQuery: Interactive Front-End Web Development`

<br>

### JS Chapter 3: Functions, Methods, and Objects

<br>

#### Object Constructor


```
var Object(parameter1, parameter2, parameter3){

    this.name: parameter1;
    this.number: parameter2;
    this.check: parameter3;


    this.methodname= function(){
       this.something and this.somethingelse
   };
};

let variable newObject1 = new Object (newKey1, newKey2, newKey3);
let variable newObject2 = new Object (newKey4, newKey5, newKey6);

let elNumber = document.getElementById('ID');
elNumber.textContent= ('newValue');
```

- Use `new` keyword with a `Constructor` to create a "blank" object.
- Use `delete` keyword to delete object property.
- To clear a property value, set it to an empty string `''`.
- Use `this` keyword instead of the object's name inside it.
- Constructors' names usually begin with a capital letter to use `new` with it.

<br>

#### Arrays 

- `Arrays` are special type of `Objects`.
- They hold a related set of `key/value` pairs where the index number is the `key`.
- `Arrays` can be nested and combined and can even contain objects.

<br>

#### Built-in Objects

> An object model is a group of objects, each of which represent related things from the real world. Together they form a model of something larger.

- There are three sets of Built-in Objects
  - Browser Object Model
    - Contains objects that represent the current browser window or tab. It contains objects that model things like browser history and the device's screen.
    - `window.innerHeight, window.screenX, window.alert(), window.open(), ...`.
  - Document Object Model
    - The Document Object Model uses objects to create a representation of the current page. It creates a new object for each element (and each individual section of text) within the page.
    - `document.title, document.getElementByld(), document.createElement(), ...`
  - Global Javascript Objects
    - The global JavaScript objects represent things that the JavaScript language needs to create a model of. For example, there is an object that deals only with dates and times.

- To work with built-in `Objects` such as `String, Number, Math, and Date` create an instance of them.
- Use built in object `methods` to retrieve and represent their data like `getDate(), getDay(), getFul1Year(), ...`.

```
let today = new Date()
```
