[Home](README.md)

<br>

# React 4

<br>

## Readings from [Dynamic Routes](https://nextjs.org/learn/basics/dynamic-routes/page-path-external-data)

<br>

### Page Path Depends on External Data

<br>

> `Next.js` allows you to statically generate pages with paths that depend on external data.

> This enables dynamic URLs in `Next.js`.

<br>

### How to Statically Generate Pages with Dynamic Routes

<br>

- In our case, we want to create dynamic routes for blog posts:
  - We want each post to have the path `/posts/<id>`, where `<id>` is the name of the markdown file under the top-level posts directory.
  - Since we have ssg-ssr.md and pre-rendering.md, we’d like the paths to be `/posts/ssg-ssr` and `/posts/pre-rendering`.

> Create a page called `[id].js` under `pages/posts`. 

> Pages that begin with `[` and end with `]` are dynamic routes in `Next.js.`

> In `pages/posts/[id].js`, we’ll write code that will render a post page — just like other pages we’ve created.

> Now, here’s what’s new: We’ll export an async function called getStaticPaths from this page.

> In this function, we need to return a list of possible values for id.

> Finally, we need to implement getStaticProps again - this time, to fetch necessary data for the blog post with a given id. getStaticProps is given params, which contains id (because the file name is `[id].js`).

<br>

### Implement getStaticPaths

<br>

- Set up the files:
  - Create a file called `[id].js` inside the pages/posts directory.
  - Also, remove `first-post.js` inside the pages/posts directory — we’ll no longer use this.
  - Then, open `pages/posts/[id].js` in your editor and paste the following code.

```jsx
import Layout from '../../components/layout'

export default function Post() {
  return <Layout>...</Layout>
}
```

> Then, `open lib/posts.js` and add the following getAllPostIds function at the bottom.

```jsx
export function getAllPostIds() {
  const fileNames = fs.readdirSync(postsDirectory)

  return fileNames.map(fileName => {
    return {
      params: {
        id: fileName.replace(/\.md$/, '')
      }
    }
  })
}
```

> Important: The returned list is not just an array of strings — it must be an array of objects that look like the comment above.

> Each object must have the `params` key and contain an object with the id key (because we’re using `[id]` in the file name).

> Otherwise, getStaticPaths will fail.

> Finally, we'll import the `getAllPostIds` function and use it inside getStaticPaths.

> Open `pages/posts/[id].js` and copy the following code above the exported Post component.

<br>

```jsx
import { getAllPostIds } from '../../lib/posts'

export async function getStaticPaths() {
  const paths = getAllPostIds()
  return {
    paths,
    fallback: false
  }
}
```

<br>

> `paths` contains the array of known paths returned by `getAllPostIds()`, which include the params defined by `pages/posts/[id].js`.

<br>

### Implement getStaticProps

<br>

> We need to fetch necessary data to render the post with the given `id`.

> To do so, open `lib/posts.js` again and add the following `getPostData` function at the bottom.

> It will return the post data based on `id`.

> Then, open `pages/posts/[id].js` and replace this line.

> The post page is now using the getPostData function in getStaticProps to get the post data and return it as props.

> Now, let's update the Post component to use postData. In `pages/posts/[id].js` replace the exported Post component with the following code.

<br>

### Render Markdown

<br>

> To render markdown content, we’ll use the remark library.

> First, let’s install it: `npm install remark remark-html`.

> Then, open `lib/posts.js` and add the following imports to the top of the file.

> And update the `getPostData()` function in the same file as follows to use remark.

> Important: We added the `async` keyword to `getPostData` because we need to use `await` for remark.

> `async/await` allow you to fetch data asynchronously.

> That means we need to update getStaticProps in `pages/posts/[id].js` to use await when calling `getPostData`.

> Finally, update the Post component in `pages/posts/[id].js` to render contentHtml using `dangerouslySetInnerHTML`.

<br>

### Adding title to the Post Page

<br>

> In `pages/posts/[id].js`, let’s add the title tag using the post data.

> You'll need to add an import for next/head at the top of the file and add the title tag by updating the Post component.

<br>

### Formatting the Date

<br>

> To format the date, we’ll use the `date-fns` library.

> Next, create a file called `components/date.js` and add the following Date component.

> Now, open `pages/posts/[id].js`, add an import for the Date component at the top of the file, and use it over `{postData.date}`:

<br>

### Adding CSS

<br>

> Finally, let’s add some CSS using the file `styles/utils.module.css` we added before.

> Open `pages/posts/[id].js`, then add an import for the CSS file.

<br>

### Polishing the Index Page

<br>

> Next, let’s update our index page (`pages/index.js`). We need to add links to each post page using the Link component.

> Open `pages/index.js` and add the imports at the top of the file for Link and Date.

<br>

### Fetch External API or Query Database

<br>

> Like `getStaticProps`, `getStaticPaths` can fetch data from any data source.

> In our example, getAllPostIds (which is used by `getStaticPaths`) may fetch from an external API endpoint:

```jsx
export async function getAllPostIds() {
  // Instead of the file system,
  // fetch post data from an external API endpoint
  const res = await fetch('..')
  const posts = await res.json()
  return posts.map(post => {
    return {
      params: {
        id: post.id
      }
    }
  })
}
```

<br>

### Development v.s. Production

<br>

- In development (`npm run dev` or `yarn dev`), `getStaticPaths` runs on every request.
- In production, `getStaticPaths` runs at build time.

<br>

### Fallback

<br>

> Recall that we returned fallback: false from `getStaticPaths`. What does this mean?

> If fallback is false, then any paths not returned by `getStaticPaths` will result in a 404 page.

- If fallback is true, then the behavior of getStaticProps changes:
  - The paths returned from getStaticPaths will be rendered to HTML at build time.
  - The paths that have not been generated at build time will not result in a `404` page.
  - Instead, `Next.js` will serve a “fallback” version of the page on the first request to such a path.
  - In the background, `Next.js` will statically generate the requested path. Subsequent requests to the same path will serve the generated page, just like other pages pre-rendered at build time.

> If fallback is blocking, then new paths will be server-side rendered with getStaticProps, and cached for future requests so it only happens once per path.

> This is beyond the scope of our lessons, but you can learn more about fallback: true and fallback: 'blocking' in the fallback documentation.

<br>

### Catch-all Routes

<br>

> Dynamic routes can be extended to catch all paths by adding three dots (`...`) inside the brackets.

> `pages/posts/[...id].js` matches `/posts/a`, but also `/posts/a/b`, `/posts/a/b/c` and so on.

> If you do this, in `getStaticPaths`, you must return an array as the value of the id key like so.

<br>

### Router

<br>

> If you want to access the `Next.js` router, you can do so by importing the useRouter hook from `next/router`.

<br>

### 404 Pages

<br>

```jsx
// pages/404.js
export default function Custom404() {
  return <h1>404 - Page Not Found</h1>
}
```

<br>

## Readings from [Deploying Your Next.js App](https://nextjs.org/learn/basics/deploying-nextjs-app)

<br>

### Push to GitHub

<br>

- Before we deploy, let’s push our `Next.js` app to GitHub if you haven’t done so already.

> On your personal GitHub account, create a new repository called nextjs-blog.
> The repository can be public or private. You do not need to initialize it with a README or other files.
> If you need help setting up your repo, take a look at this guide on GitHub.

- Then:

> If you haven’t initialized the git repository locally for your `Next.js` app, do so now.
> Push the `Next.js` app to your GitHub repository.

<br>

### Deploy to Vercel

<br>

> The easiest way to deploy `Next.js` to production is to use the `Vercel` platform developed by the creators of `Next.js`.

> `Vercel` is a serverless platform for static and hybrid applications built to integrate with your headless content, commerce, or database.

<br>

### Create a Vercel Account

<br>

### Import your nextjs-blog repository

<br>

- Once you’re signed up, import your nextjs-blog repository on Vercel.

> You’ll need to Install Vercel for GitHub. You can give it access to All Repositories.
> Once you’ve installed Vercel, import nextjs-blog.

- You can use default values for the following settings — no need to change anything. Vercel automatically detects that you have a Next.js app and chooses optimal build settings for you.

> Project Name
> Root Directory
> Build Command
> Output Directory
> Development Command

<br>

### Next.js and Vercel

<br>

- `Vercel` is made by the creators of `Next.js` and has first-class support for `Next.js`.

> Pages that use Static Generation and assets (JS, CSS, images, fonts, etc) will automatically be served from the Vercel Edge Network, which is blazingly fast.
> Pages that use Server-Side Rendering and API routes will automatically become isolated Serverless Functions. This allows page rendering and API requests to scale infinitely.

- `Vercel` has many more features, such as:

> Custom Domains: Once deployed on `Vercel`, you can assign a custom domain to your `Next.js` app. Take a look at our documentation here.
> Environment Variables: You can also set environment variables on `Vercel`. Take a look at our documentation here. You can then use those environment variables in your `Next.js` app.
> Automatic HTTPS: HTTPS is enabled by default (including custom domains) and doesn't require extra configuration. We auto-renew `SSL` certificates.

<br>

### Develop, Preview, Ship

<br>

- We’ve just gone through the workflow we call DPS: Develop, Preview, and Ship.
  - `Develop`
    - We’ve written code in Next.js and used the Next.js development server running to take advantage of its hot reloading feature.
  - `Preview`
    - We’ve pushed changes to a branch on GitHub, and Vercel created a preview deployment that’s available via a URL. We can share this preview URL with others for feedback. In addition to doing code reviews, you can do deployment previews.
  - `Ship`
    - We’ve merged the pull request to main to ship to production.

<br>

### Other Hosting Options

<br>

> `Next.js` can be deployed to any hosting provider that supports `Node.js`.

> If you’ve followed the instructions so far, your `package.json` should have the following build and start scripts:

```jsx
{
  "scripts": {
    "dev": "next",
    "build": "next build",
    "start": "next start"
  }
}
```

<br>

> In your own hosting provider, run the build script once, which builds the production application in the `.next` folder.

> After building, the start script starts a `Node.js` server that supports hybrid pages, serving both statically generated and server-side rendered pages, and `API Routes`.
