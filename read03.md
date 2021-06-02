[Home](README.md)

<br>

# Structuring HTML WebPages

<br>

## Wireframing

<br>

- The process of wireframing is creating a guideline for how you want your webpage to look like.
- You can sketch out your ideas or use digital tools to help you organize your thoughts and expirement with your ideas.
- The goal of wireframing is to provide yourself with a rough idea aabout how will your webpage look like, and allow you to imagine different outputs and share with with your team.

<br>

## HTML Structure

<br>

- `HTML` stands for `HyperText Markup Language`, a code that is used to create the skeletal structure of webpages.
- `HTML` uses `tags` to depict how will text/media appear when they're rendered, in something similar to this format:

 ``` 
 <b> Your Text Here </b>
 ```

 Where `<b>` and `</b>` are *opening and closing tags* in order, enclosing your text, which is named "*content*". The whole block is called an "*element*". In this specific case, the outcome result will render the text in bold. 

 Where `<b>` and `</b>` are *opening and closing tags* in order, enclosing your text, which is named "*content*". The whole block is called an "*element*". In this specific case, the outcome result will render the text in bold. `


 **Your Text Here**

<br>

- HTML Document Main Tags that allows it to function properly are:
``` 
    <!DOCTYPE html>

    <html>

    <head> --- </head>

    <body> --- </body>

    </html>
```

<br>

- You can add some aesthetic value to your strucutral elements using *attributes*. These are extra information you add that lets your work render in a specific style.

 ```
 <h1 style="color:red;"> Your Stylized Text Here </h1> 
 ```
 Here, `style` is an *attribute*, `color` is a *property*, and `red` is the *value*. Your text should render like this: 
<h1 style="color:red;"> Your Stylized Text Here </h1>

<br>

- You can nest elements within others in a similar format:
 ```
 <p> Your <b> Bold </b> Statement </p>
 ```
 And it should look something like this:

 Your **Bold** Statement Here

<br>


