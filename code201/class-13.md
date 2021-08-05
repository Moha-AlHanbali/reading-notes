[Home](README.md)

<br>

# Local Storage

<br>

## Readings from [THE PAST, PRESENT & FUTURE OF LOCAL STORAGE FOR WEB APPLICATIONS](http://diveinto.html5doctor.com/storage.html)

<br>

### PRESENT & FUTURE OF LOCAL STORAGE FOR WEB APPLICATIONS

<br>

#### Web Cookies

> Cookies were invented early in the web’s history,they can be used for persistent local storage of small amounts of data.

- Downsides of using cookies:
  - Cookies are included with every `HTTP` request, thereby slowing down your web application by needlessly transmitting the same data over and over.
  - Cookies are included with every `HTTP` request, thereby sending data unencrypted over the internet (unless your entire web application is served over `SSL`).
  - Cookies are limited to about 4 KB of data — enough to slow down your application, but not enough to be terribly useful.
  
  <br>

#### Local Storage Before HTML5

- Microsoft invented a great many things and included them in their browser-to-end-all-browser-wars, Internet Explorer. One of these things was called `DHTML` Behaviors, and one of these behaviors was called `userData`.
- `userData` allows web pages to store up to 64 KB of data per domain, in a hierarchical XML-based structure. (Trusted domains, such as intranet sites, can store 10 times that amount.
- Adobe introduced a feature in `Flash 6` that gained the unfortunate and misleading name of `Flash cookies`.
- Within the `Flash` environment, the feature is properly known as Local Shared Objects. Briefly, it allows Flash objects to store up to 100 KB of data per domain.
- Google launched `Gears`, an open source browser plugin aimed at providing additional capabilities in browsers.
- After obtaining permission from the user once, Gears can store unlimited amounts of data per domain in `SQL database` tables.

<br>

#### HTML5 Storage (Web Storage)

- Web Storage was at one time part of the `HTML5` specification proper, but was split out into its own specification.
- Certain browser vendors also refer to it as `Local Storage` or `DOM Storag`e.

> It is a way for web pages to store named key/value pairs locally, within the client web browser. Like cookies, this data persists even after you navigate away from the web site, close your browser tab, exit your browser, or what have you. Unlike cookies, this data is never transmitted to the remote web server (unless you go out of your way to send it manually).

- From your `JavaScript` code, you’ll access `HTML5` Storage through the `localStorage` object on the global window object. Before you can use it, you should detect whether the browser supports it.

<br>

```

function supports_html5_storage() {
  try {
    return 'localStorage' in window && window['localStorage'] !== null;
  } catch (e) {
    return false;
  }
}

```

<br>

#### Using HTML5 Storage

- HTML5 Storage is based on named key/value pairs.
- You store data based on a named key, then you can retrieve that data with the same key. The named key is a string. The data can be any type supported by JavaScript, including strings, Booleans, integers, or floats. However, the data is actually stored as a string.
- If you are storing and retrieving anything other than strings, you will need to use functions like `parseInt()` or `parseFloat()` to coerce your retrieved data into the expected JavaScript datatype.

<br>

- Calling `setItem()` with a named key that already exists will silently overwrite the previous value. Calling `getItem()` with a non-existent key will return null rather than throw an exception.
- Like other JavaScript objects, you can treat the localStorage object as an associative array. Instead of using the `getItem()` and `setItem()` methods, you can simply use square brackets.

<br>

#### Tracking Changes to HTML5 Storage Area

- To keep track programmatically of when the storage area changes, you can trap the storage event.
- The storage event is fired on the window object whenever `setItem()`, `removeItem()`, or `clear()` is called and actually changes something.

<br>

#### Limitations in Browsers

- Standardized `HTML5` Storage is 5 megabytes per origin.
- You will be storing strings, not data in its original format. Each digit in that float is being stored as a character, not in the usual representation of a floating point number.

<br>

#### Future of HTML5 Storage

- Google's `Gears`, an open source cross-browser plugin includes an embedded database based on `SQLite`. This early prototype later influenced the creation of the `Web SQL` Database specification. `Web SQL Database` (formerly known as `WebDB`) provides a thin wrapper around a `SQL database`.
- `The Indexed Database API`, formerly known as `WebSimpleDB`, now affectionately known as `IndexedDB`.
- `The Indexed Database API` exposes what’s called an object store. An object store shares many concepts with a `SQL database`.
