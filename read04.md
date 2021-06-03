[Home](README.md)

<br>

# Introducing CSS

<br>

## What is CSS
- `CSS` stands for `Cascading Style Sheets`, a language used to stylize and add aesthetics to your rendered `HTML` webpages.
- It also functions as the organizer of `HTML` structure content, as it permits you to display your `HTML` material with more freedom and allowing some level of customization.

<br>

## How to use CSS
There are three ways to implement `CSS` into `HTML` document:

<br>

- Inline `CSS`, where you type `CSS Syntax` within `HTML` tag, in a similar format:

```
<p style="color:red;"> Your Stylized Text Here </p>
```

<br>

- Internal `CSS`, where you type `CSS Syntax` inside `HTML` documents, as follows:

```
<style>
p{
  color:red
}
</style>
```

<br>

- External `CSS`, where you link `CSS` files to your `HTML` document, and basically works like `Internal CSS`, but in its' own environment.

```
p{
  color:red
}
```

<br>
The results of all the previous three methods should render the same output:
<p style="color:red;"> Your Stylized Text Here </p>

## Color Support in CSS
`CSS` supports a handful of popular color codes;
- `RGB`Color code, which stands for `RED, GREEN, and BLUE` color ratios in order, and used in this format.

```
<h2 style="color:rgb(100,100,100)";> YOUR COLORED TEXT HERE </h>
```

<br>

- `RGBA` Color code, which stands for `RED, GREEN, BLUE, and Alpha Channel`, it's different from `RGB` where using this code, you can control transparency using `Alpha Channel`.

```
<h2 style="color:rgba(100,100,100,0.50)";> YOUR COLORED TEXT HERE </h>
```

<br>

- `HEX` Color code, where every pair of digits represents the values of colors `RED, GREEN, and BLUE` in order in the following format:

```
<h2 style="color:#000000";> YOUR COLORED TEXT HERE </h>
```

<br>

- `HSL` Color code, where `HUE, SATURATION, AND LIGHTNESS` are represented in order, in such a format `0-360,0-100%, 0-100%`

```
<h2 style="color:hsl(50,10%,10%)";> YOUR COLORED TEXT HERE </h>
