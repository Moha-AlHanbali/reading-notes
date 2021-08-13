[Home](README.md)

<br>

# NODE.JS

<br>

## Readings from [What Is Node and When Should I Use It](https://www.sitepoint.com/an-introduction-to-node-js/)

<br>

### What Is Node.js?

<br>

> Node.js® is a JavaScript runtime built on Chrome’s V8 JavaScript engine.

> Node.js is an event-based, non-blocking, asynchronous I/O runtime that uses Google’s V8 JavaScript engine and libuv library.

<br>

### Node Is Built on Google Chrome’s V8 JavaScript Engine

<br>

> The V8 engine is the open-source JavaScript engine that runs in Google Chrome and other Chromium-based web browsers, including Brave, Opera, and Vivaldi.

> It was designed with performance in mind and is responsible for compiling JavaScript directly to native machine code that your computer can execute.

> Node.js is a program we can use to execute JavaScript on our computers. In other words, it’s a JavaScript runtime.

<br>

### How Do I Install Node.js?

<br>

#### Node Binaries vs Version Manager

<br>

> Using a version managerm, this allows you to install multiple versions of Node and switch between them at will. There are various advantages to using a version manager.

> It negates potential permission issues when using Node with npm and lets you set a Node version on a per-project basis.

<br>

#### Node.js Has Excellent Support for Modern JavaScript

<br>

> As you’re only targeting one runtime (a specific version of the V8 engine), this means that you can write your JavaScript using the latest and most modern syntax.

> It also means that you don’t generally have to worry about compatibility issues — as you would if you were writing JavaScript that would run in different browsers.

<br>

### npm, the JavaScript Package Manager

<br>

> In addition to being the package manager for JavaScript, npm is also the world’s largest software registry. 

<br>

#### Working with the package.json File

<br>

> node_modules is where npm has saved lodash and any libraries that lodash depends on.

> The node_modules folder shouldn’t be checked in to version control, and can, in fact, be re-created at any time by running `npm install` from within the project’s root.

> If you open the package.json file, you’ll see lodash listed under the dependencies field. By specifying your project’s dependencies in this way, you allow any developer anywhere to clone your project and use npm to install whatever packages it needs to run.

<br>

### What Is Node.js Used For?

<br>

> It can be used for anything from bundling your JavaScript files and dependencies into static assets, to running tests, or automatic code linting and style checking.

<br>

#### Node.js Lets Us Run JavaScript on the Server

<br>

> One of the biggest use cases for Node.js — running JavaScript on the server. This isn’t a new concept, and was first attempted by Netscape way back in 1994.

<br>

#### The Node.js Execution Model

<br>

- when you connect to a traditional server, such as Apache, it will spawn a new thread to handle the request.

- In a language such as PHP or Ruby, any subsequent I/O operations (for example, interacting with a database) block the execution of your code until the operation has completed.

- That is, the server has to wait for the database lookup to complete before it can move on to processing the result.

- If new requests come in while this is happening, the server will spawn new threads to deal with them.

- This is potentially inefficient, as a large number of threads can cause a system to become sluggish — and, in the worst case, for the site to go down. 

- The most common way to support more connections is to add more servers.

- Node.js, however, is single-threaded. It’s also event-driven, which means that everything that happens in Node is in reaction to an event. 

- When a new request comes in (one kind of event) the server will start processing it. If it then encounters a blocking I/O operation, instead of waiting for this to complete, it will register a callback before continuing to process the next event. 

- When the I/O operation has finished (another kind of event), the server will execute the callback and continue working on the original request. 

- Under the hood, Node uses the libuv library to implement this asynchronous (that is, non-blocking) behavior.

- Node’s execution model causes the server very little overhead, and consequently it’s capable of handling a large number of simultaneous connections. 

- The traditional approach to scaling a Node app is to clone it and have the cloned instances share the workload.

<br>

#### Are There Any Downsides?

<br>

> Blocking I/O calls should be avoided, CPU-intensive operations should be handed off to a worker thread, and errors should always be handled correctly for fear of crashing the entire process.

<br>

### What Kind of Apps Is Node.js Suited To?

<br>

> Node is particularly suited to building applications that require some form of real-time interaction or collaboration — for example, chat sites.

> It’s also a good fit for building APIs where you’re handling lots of requests that are I/O driven (such as those needing to perform operations on a database), or for sites involving data streaming, as Node makes it possible to process files while they’re still being uploaded.

<br>

### What Are the Advantages of Node.js?

<br>

> Aside from speed and scalability, an often-touted advantage of using JavaScript on a web server — as well as in the browser — is that your brain no longer needs to switch modes. You can do everything in the same language, which, as a developer, makes you more productive.

> Node’s big pluses is that it speaks JSON. JSON is probably the most important data exchange format on the Web, and the lingua franca for interacting with object databases (such as MongoDB).

> JavaScript is ubiquitous: most of us are familiar with JavaScript, or have used it at some point. This means that transitioning to Node development is potentially easier than to other server-side languages.

> it can be used as a scripting language to automate repetitive or error prone tasks on your PC. 

> Node.js can also can be used to build cross-platform desktop apps and even to create your own robots. 

<br>

## Readings from [6 Reasons for Pair Programming](https://www.codefellows.org/blog/6-reasons-for-pair-programming/)

<br>

### Pair Programming?

<br>

  - The article claims that programming in pairs is a good prctice stating the following arguments:

<br>

  #### How does pair programming work?

<br>

> Pair programming commonly involves two roles: the Driver and the Navigator.

- The Driver's responsibilities:
  - Handling the “mechanics” of coding.
  - Managing the text editor.
  - Switching files.
  - Version control.
  - Writing Code.

- The Navigator:
  - Thinks about the big picture, what comes next.
  - How an algorithm might be converted in to code.
  - Scanning for typos or bugs. 
  - Utilize their computer as a second screen to look up solutions and documentation.
  

<br>

  #### Why pair program?

<br>
> Pair programming touches on all four skills: developers explain out loud what the code should do, listen to others’ guidance, read code that others have written, and write code themselves.

<br>

#### What does pair programming Offer?
 
 <br>

1. Greater efficiency
2. Engaged collaboration
3. Learning from fellow students
4. Social skills
5. Job interview readiness
6. Work environment readiness

<br>

## Conclusion

<br>

- What is node.js?
    - Node.js is a JavaScript runtime built on Chrome’s V8 JavaScript engine.
    - Node.js is an event-based, non-blocking, asynchronous I/O runtime that uses Google’s V8 JavaScript engine and libuv library.

- In your own words, what is Chrome’s V8 JavaScript Engine?
    - An open-source program that is used to operate Chromium-based web browsers. It complies JS into binary directly.

- What does it mean that node is a JavaScript runtime?
    - This means that Node.js is a program we can use to execute JavaScript on our computers.

- What is npm?
    - In addition to being the package manager for JavaScript, npm is also the world’s largest software registry. 

- What version of node are you running on your machine?
    - `v14.17.4`

- What version of npm are you running on your machine?
    - `6.14.14`

- What command would you type to install a library/package called ‘jshint’?
    - `npm install -g jshint`


- What is node used for?
    - They can be used for anything from bundling your JavaScript files and dependencies into static assets, to running tests, or automatic code linting and style checking.

- What are the 6 reasons for pair programming?
    1. Greater efficiency
    2. Engaged collaboration
    3. Learning from fellow students
    4. Social skills
    5. Job interview readiness
    6. Work environment readiness 

- In your experience, which of these reasons have you found most beneficial?
    - Work environment readiness

- How does pair programming work?
    - Pair programming commonly involves two roles: the Driver and the Navigator.
        - The Driver handles the “mechanics” of coding.
        - The Navigator directs him on how to operate.