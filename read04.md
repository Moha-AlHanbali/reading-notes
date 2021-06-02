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