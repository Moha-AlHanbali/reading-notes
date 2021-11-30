[Home](README.md)

<br>

# React 3

<br>

## Readings from [Navigate Between Pages](https://nextjs.org/learn/basics/navigate-between-pages)

<br>

### Pages in Next.js

<br>

> In `Next.js`, a page is a React Component exported from a file in the pages directory.

- Pages are associated with a route based on their file name. For example, in development:
  - `pages/index.js` is associated with the `/` route.
  - `pages/posts/first-post.js` is associated with the /`posts/first-post` route.

<br>

### Create a New Page

<br>

> Simply create a `JS` file under the pages directory, and the path to the file becomes the URL path.

> In a way, this is similar to building websites using HTML or PHP files.

> Instead of writing HTML you write `JSX` and use React Components.

<br>

### Link Component

<br>

> When linking between pages on websites, you use the `<a>` HTML tag.

> In Next.js, you use the Link Component from next/link to wrap the `<a>` tag.

> `<Link>` allows you to do client-side navigation to a different page in the application.

<br>

### Using `<Link>`

<br>

> First, open `pages/index.js`, and import the Link component from `next/link` by adding this line at the top.

> `import Link from 'next/link'`.

```jsx
<h1 className="title">
  Learn <a href="https://nextjs.org">Next.js!</a>
</h1>

// change to:

<h1 className="title">
  Read{' '}
  <Link href="/posts/first-post">
    <a>this page!</a>
  </Link>
</h1>

// and export the target

import Link from 'next/link'

export default function FirstPost() {
  return (
    <>
      <h1>First Post</h1>
      <h2>
        <Link href="/">
          <a>Back to home</a>
        </Link>
      </h2>
    </>
  )
}

```

<br>

> `{' '}` adds an empty space, which is used to divide text over multiple lines.

> As you can see, the Link component is similar to using `<a>` tags, but instead of `<a href="…">,` you use `<Link href="…">` and put an `<a>` tag inside.

<br>

### Client-Side Navigation

<br>

> The Link component enables client-side navigation between two pages in the same `Next.js` app.

> Client-side navigation means that the page transition happens using JavaScript, which is faster than the default navigation done by the browser.

> If you’ve used `<a href="…">` instead of `<Link href="…">` and did this, the background color will be cleared on link clicks because the browser does a full refresh.

<br>

### Code splitting and prefetching

<br>

> `Next.js` does code splitting automatically, so each page only loads what’s necessary for that page.

> That means when the homepage is rendered, the code for other pages is not served initially.

> Only loading the code for the page you request also means that pages become isolated.

> If a certain page throws an error, the rest of the application would still work.

> In a production build of `Next.js`, whenever Link components appear in the browser’s viewport, `Next.js` automatically prefetches the code for the linked page in the background. 

> If you need to link to an external page outside the Next.js app, just use an `<a>` tag without `Link`.

> If you need to add attributes like, for example, className, add it to the `a` tag, not to the `Link` tag.

<br>

## Readings from  [Assets, Metadata, and CSS](https://nextjs.org/learn/basics/assets-metadata-css) 

<br>

### Assets

<br>

> `Next.js` can serve static assets, like images, under the top-level public directory.

> Files inside public can be referenced from the root of the application similar to pages.

> The public directory is also useful for `robots.txt`, `Google Site Verification`, and any other static assets.

<br>

### Download Your Profile Picture

<br>

- Download your profile picture in `.jpg` format.
- Create an images directory inside of the `public` directory.
- Save the picture as `profile.jpg` in the `public/images` directory.
- The image size can be around 400px by 400px.
- You may remove the unused SVG logo file directly under the public directory.

<br>

### Unoptimized Image

<br>

- With regular HTML, you have to manually handle:
  - Ensuring your image is responsive on different screen sizes
  - Optimizing your images with a third-party tool or library
  - Only loading images when they enter the viewport

<br>

### Image Component and Image Optimization

<br>

> `next/image` is an extension of the HTML `<img>` element, evolved for the modern web.

> `Next.js` also has support for Image Optimization by default.

> This allows for resizing, optimizing, and serving images in modern formats like WebP when the browser supports it.

> This avoids shipping large images to devices with a smaller viewport.

> It also allows `Next.js` to automatically adopt future image formats and serve them to browsers that support those formats.

> Automatic Image Optimization works with any image source. Even if the image is hosted by an external data source, like a `CMS`, it can still be optimized.

<br>

### Using the Image Component

<br>

> Instead of optimizing images at build time, `Next.js` optimizes images on-demand, as users request them.

> Unlike static site generators and static-only solutions, your build times aren't increased, whether shipping 10 images or 10 million images.

> Images are lazy loaded by default. That means your page speed isn't penalized for images outside the viewport.

> Images load as they are scrolled into viewport.

```jsx
import Image from 'next/image'

const YourComponent = () => (
  <Image
    src= // Route of the image file
    height= // Desired size with correct aspect ratio
    width= // Desired size with correct aspect ratio
    alt= // Alt name
  />
)
```

<br>

### Metadata

<br>

> What if we wanted to modify the metadata of the page, such as the `<title>` HTML tag?

> `<title>` is part of the `<head>` HTML tag, so let's dive into how we can modify the `<head>` tag in a` Next.js` page.

> You can import the `Head` component from the `next/head` module.

<br>

### Adding `Head` to a page

<br>

> Open the `pages.js` file and add an import for Head from `next/head` at the beginning of the file.

> Then, update the exported `component` to include the `Head` component.

> Add just the `title` tag.

<br>

### CSS Styling

<br>

> Pages are using a library called `styled-jsx`.

> It’s a “C`SS-in-JS`” library — it lets you write CSS within a React component, and the CSS styles will be scoped (other components won’t be affected).

> `Next.js` has built-in support for styled-jsx, but you can also use other popular CSS-in-JS libraries such as styled-components or emotion.

<br>

### Writing and Importing CSS

<br>

> `Next.js` has built-in support for CSS and Sass which allows you to import `.css` and `.scss` files.

> Using popular CSS libraries like `Tailwind CSS` is also supported.

<br>

### Layout Component

<br>

- First, Let’s create a Layout component which will be shared across all pages.
  - Create a top-level directory called components.
  - Inside components, create a file called `layout.js` with content.
  - Then, open `page.js`, add an import for the `Layout` component, and make it the outermost component.

<br>

### Adding CSS

<br>

- Create a file called `components/layout.module.css`.
- To use this container class inside `components/layout.js`, you need to:
  - Import the CSS file and assign a name to it, like styles
  - Use `styles.container` as the className

<br>

### Automatically Generates Unique Class Names

<br>

> This is what CSS Modules does: It automatically generates unique class names.

> As long as you use CSS Modules, you don’t have to worry about class name collisions.

> Furthermore, `Next.js`’s code splitting feature works on CSS Modules as well.

> It ensures the minimal amount of CSS is loaded for each page. This results in smaller bundle sizes.

> CSS Modules are extracted from the `JavaScript` bundles at build time and generate `.css` files that are loaded automatically by `Next.js`.

<br>

### Global Styles

<br>

- To load global CSS files, create a file called pages/_app.js with the following content:

```jsx
export default function App({ Component, pageProps }) {
  return <Component {...pageProps} />
}
```

> This App component is the top-level component which will be common across all the different pages.

> You can use this App component to keep state when navigating between pages, for example.


<br>

### Adding Global CSS

<br>

> In `Next.js`, you can add global CSS files by importing them from `pages/_app.js.` You cannot import global CSS anywhere else.

> The reason that global CSS can't be imported outside of `pages/_app.js` is that global CSS affects all elements on the page.

> If you were to navigate from the homepage to the page, global styles from the homepage would affect the page unintentionally.

- You can place the global CSS file anywhere and use any name. So let’s do the following:
  - Create a top-level styles directory and create `global.css` inside.
  - Add the following content to `styles/global.css`.
  - It resets some styles and changes the color of the a tag.
  - Finally, open `pages/_app.js` add import the CSS file like so.

<br>

### Update `components/layout.module.css`

<br>

> First, open `components/layout.module.css` and replace its content.

<br>

### Create `styles/utils.module.css`

<br>

> Second, let’s create a set of utility CSS classes for typography and others that will be useful across multiple components.

> Let’s add a new CSS file called `styles/utils.module.css` with content.

<br>

### Update `components/layout.js`

<br>

> Third, open `components/layout.js` and replace its content.

- Here’s what’s new:
  - `meta` tags (like og:image), which are used to describe a page's content
  - Boolean `home` prop which will adjust the size of the title and the image
  - “Back to home” link at the bottom if `home` is `false`
  - Added images with `next/image`, which are preloaded with the priority attribute

<br>

### Using `classnames` library to toggle classes

<br>

> `classnames` is a simple library that lets you toggle class names easily.

> You can install it using npm install classnames or yarn add classnames.

```jsx
// Suppose that you want to create an Alert component which accepts type, which can be 'success' or 'error'.
// If it’s 'success', you want the text color to be green. If it’s 'error', you want the text color to be red.

import styles from './alert.module.css'
import cn from 'classnames'

export default function Alert({ children, type }) {
  return (
    <div
      className={cn({
        [styles.success]: type === 'success',
        [styles.error]: type === 'error'
      })}
    >
      {children}
    </div>
  )
}
```

<br>

### Customizing PostCSS Config

<br>

> Out of the box, with no configuration, `Next.js` compiles CSS using PostCSS.

> To customize PostCSS config, you can create a top-level file called `postcss.config.js`.

> This is useful if you’re using libraries like `Tailwind CSS`.

<br>

### Using Sass

<br>

> Out of the box, `Next.js` allows you to import Sass using both the `.scss` and `.sass` extensions.

> You can use component-level Sass via CSS Modules and the `.module.scss` or `.module.sass` extension.

<br>

## Readings from [React Context for Beginners](https://www.freecodecamp.org/news/react-context-for-beginners/)

<br>

### What is React context?

<br>

> React context allows us to pass down and use (`consume`) data in whatever component we need in our React app without using props.

> In other words, React context allows us to share data (`state`) across our components more easily.

<br>

### When should you use React context?

<br>

- React context is great when you are passing data that can be used in any component in your application.
  - Theme data (like dark or light mode)
  - User data (the currently authenticated user)
  - Location-specific data (like user language or locale)

> You can think of React context as the equivalent of global variables for our React components.

<br>

### What problems does React context solve?

<br>

> React context helps us avoid the problem of props drilling.

> Props drilling is a term to describe when you pass props down multiple levels to a nested component, through components that don't need it.

<br>

### How do I use React context?

<br>

> Context is an API that is built into React, starting from React version 16.

> This means that we can create and use context directly by importing React in any React project.

- There are four steps to using React context:
  - Create context using the createContext method.
  - Take your created context and wrap the context provider around your component tree.
  - Put any value you like on your context provider using the value prop.
  - Read that value within any component by using the context consumer.

<br>

> In our App component, we are creating context with `React.createContext()` and putting the result in a variable, `UserContext`.

> In almost every case, you will want to export it as we are doing here because your component will be in another file.

> Note that we can pass an initial value to our value prop when we call `React.createContext()`.

> In our App component, we are using `UserContext`.

> Specifically `UserContext.Provider`. The created context is an object with two properties: Provider and Consumer, both of which are components.

> To pass our value down to every component in our App, we wrap our Provider component around it (in this case, User).

> On `UserContext.Provider`, we put the value that we want to pass down our entire component tree.

> We set that equal to the value prop to do so. In this case, it is our name (here, Reed).

> In User, or wherever we want to consume (or use) what was provided on our context, we use the consumer component: `UserContext.Consumer`.

> To use our passed down value, we use what is called the render props pattern.

> It is just a function that the consumer component gives us as a prop.

> And in the return of that function, we can return and use value.

<br>

### What is the useContext hook?

<br>

> We can now consume context with the `useContext` hook.

> Instead of using render props, we can pass the entire context object to `React.useContext()` to consume context at the top of our component.

> The benefit of the `useContext` hook is that it makes our components more concise and allows us to create our own custom hooks.

<br>

### You may not need context

<br>

> The mistake many developers make is reaching for context when once they have to pass props down several levels to a component.

> Instead of immediately resorting to context because we are prop drilling, we should better compose our components.

<br>

### Does React context replace Redux?

<br>

> For many React beginners, Redux is a way of more easily passing around data. This is because Redux comes with React context itself.

> However, if you are not also updating state, but merely passing it down your component tree, you do not need a global state management library like Redux.

<br>

### React context caveats

<br>

> While it is possible to combine React context with a hook like useReducer and create a makeshift state management library without any third-party library, it is generally not recommended for performance reasons.

> The issue with this approach lies in the way that React context triggers a re-render.

> If you are passing down an object on your React context provider and any property on it updates, what happens? Any component which consumes that context will re-render.

> This may not be a performance issue in smaller apps with few state values that are not updated very often (such as theme data).

> But it is a problem if you will be performing many state updates in an application with a lot of components in your component tree.
