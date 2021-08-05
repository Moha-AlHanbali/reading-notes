[Home](README.md)

<br>

# HTML Audio, Video, Images - from Jon Duckett's books

<br>

## Readings from `HTML & CSS: Design and Build Websites`

<br>

### CSS Chapter 16: Images

<br>

#### Controlling Images

- Use `width` and `height` properties to control images in CSS.
- Use class names to specify image sizes and control them together.
- Use `float` to align images in their containers.
- To center images, you can either `display` them as `block` elements and apply `text-align` to their container, or use margin properties on the image element itself.

<br>

#### More Forms of Image usage

- The `background-image` property allows you to place an image behind any HTML element. This could be the entire page or just part of the page. By default, a background image will repeat to fill the entire box.
- Use `linear-gradient` to specify a gradient for the background.
- `background-repeat` property can have four values
  - `repeat` The background image is repeated both horizontally and vertically.
  - `repeat-x` The image is repeated horizontally only.
  - `repeat-y` The image is repeated vertically only.
  - `no-repeat` The image is only shown once.

  <br>

- The `background-attachment` property specifies whether a background image should stay in one position or move as the user scrolls up and down the page.
  - `fixed` The background image stays in the same position on the page.
  - `scroll` The background image moves up and down as the user scrolls up and down the page.

<br>

- Use `background-position` to specify where in the browser window the background image should be placed (usually has a pair of values `left top / left center / ...`).

<br>

- To create a link or button that changes to a second style when a user moves their mouse over it (known as a rollover) and a third style when they click on it, by setting a background image for the link or button that has three different styles of the same button using (`:hover, :active`).

<br>

### Chapter 19: Practical Information

<br>

#### Search Engine Optimization (SEO)

> SEO is the practice of trying to help your site appear nearer the top of search engine results when people look for the topicsthat your website covers.

> The idea of working out which terms people are likely to enter into a search engine to find your site and then using these terms in the right places.

- `on-page techniques` is looking at keywords that people are likely to enter into a search engine if they wanted to find your site, and then including these in the text and HTML code for your site in order to help the search engines know that your site covers these topics.
  - Page Title
  - URL/ Web Adress
  - Headings
  - Text
  - Link Text
  - Images Alt Text
  - Page Descriptions

- `off-page techniques` determine how to rank your site by looking at the number of other sites that link to yours.
  - Search engines also look at the
    words between the opening `<a>` tag and closing `</a>` tag in the link. If the text in the link contains keywords (rather than just click here).

<br>

#### Site Analytics

- View your site's and look for key information. In particular, you how many people are coming to your site.
  - Visits
  - Unique Visits
  - Page Views
  - Pages per Visit
  - Average Time on Site
  - Pages Traffic
  - Landing Pages
  - Top Exit Pages
  - Bounce Rate
  - Referrers
  - Direct
  - Search Terms

<br>

#### Domains and Hosting

> Domain name is your web address (e.g. google.com or bbc. co.uk).

> Web servers are special computers that are constantly connected to the Internet. They are specially set up to serve web pages when they are requested.

<br>

## Readings from [MDN Video and Audio APIs](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Client-side_web_APIs/Video_and_audio_APIs)

<br>

### HTML5 video and audio

<br>

- The `<video>` and `<audio>` elements allow us to embed video and audio into web pages.

<br>

###  HTMLMediaElement API

<br>

- `HTMLMediaElement API` provides features to allow you to control video and audio players programmatically.
  - The whole player is wrapped in a `<div>` element, so it can all be styled as one unit if needed.
  - The `<video>` element contains two `<source>`elements so that different formats can be loaded depending on the browser viewing the site.
  - `<button>` used for play/pause, stop, rewind, and fast forward. Each has a `class name`, a `data-icon` attribute for defining what icon should be shown on each button and an `aria-label` attribute to provide an understandable description of each button.
  - A timer `<div>`, which will report the elapsed time when the video is playing.
  - `CSS` part contains visibility and opacity properties.
  - Using `JS`, wire up all the buttons to get the controls working.
  - Implement probably the the play/pause button using and event listener for `click` event.
  - Use event listerners to work with the rest of buttons functions.
  - This could easily work for an `<audio>` element too.
