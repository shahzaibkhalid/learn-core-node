# Learn Core Node.js 🚀 (Note: Work in Progress)
It's time to learn Node core before you bury yourself in npm packages.

## Introduction

### Prerequisites 🚧
Before you jump into the actual content, here is what you need to come up with:

* Familiarity with JavaScript
* Familiarity with Terminal

### Setting Up Your Workstation 💻
Let's set up the development environment before we proceed any further. Here's what you need:

* A text editor
* A terminal
* Node.js, preferably greater than/equal to 8.x.x LTS (Long Term Stable)

### Story of Node.js (Caution: This is so long and only for tech hipsters 👨🏻‍💻)
It all started from Ryan Dahl original Node.js Intro presentation given in 2009: https://www.youtube.com/watch?v=ztspvPYybIY

Initially, Node did not gain much traction, people thought that JavaScript is the language not suited for server-side serious stuff. Ruby on Rails was also a hot thing back then. But Ryan continued evangelizing Node.js

In 2010, Isaac Schlueter created NPM (Node Package Manager) to host reusable Node modules. NPM made Node.js much more practical. So we can say that npm is one of those forces that popularized Node.js back then.

Another project that was being evangelized in early 2009 was MongoDB. Much of the developers were not sold on the idea of the NoSQL database. Why developers would switch to such a database? JSON was not a heavily used data exchange format back then. XML and Soap APIs were largely overtaking the market.

At the same time, social media APIs began to popularize RESTful JSON APIs. As social media sites grew in popularity, the use of JSON became very common to exchange data. At that time, the idea to store JSON documents as persistent data started making perfect sense to developers. Storing and retrieving JSON data in a column of RDBMS started taking a lot of work. So why just store the JSON directly? 
But using JSON directly on the server with languages like PHP, Ruby or Java was still no picnic. These languages do not have JSON like data structure to convert to and from JSON to be used dynamically. Here comes Node.js, as Node.js is JavaScript, JSON (JavaScript Object Notation) was a native feature, using objects format containing key-value pairs. So in Node, MongoDB found a partner in arms. And both projects started benefitting heavily from JSON usage. But as of mid-2010, there was still significant resistance to Node.js

In 2010, Google invited Ryan to give a talk [https://www.youtube.com/watch?v=F6k8lTrAE2g] on Node.js as part of its series on emerging web technologies. The version of Ryan presented back then was still far from production usages. Node was still looking for a miracle to happen and it happened within the next 12 months with the introduction of the following projects:
* ExpressJS
* Mongoose
* AngularJS
* Node for Windows

#### Express
Express extracted away all boilerplate and created somewhat stable APIs on top of unstable Node core. This largely simplified the usage of Node.js for the masses. As ExpressJS was an MVC framework, it provided an easier path to Full-Stack Ruby on Rails engineer to get interested in Node.

#### Mongoose
Mongoose came out in 2010 and made it very easy to use MongoDB with Node.

#### AngularJS
Similarly, in 2010, Google released AngularJS and this put the move forward of JSON and a common form of data sharing that’s understood natively by both front-end and back-end.
So the people who adopted this stack got an extra benefit that was not available on other platforms. Hence, the MEAN stack was born.

#### Node for Windows
Although things were pretty good in MEAN stack those who were using raw Node outside of MEAN stack had some instability issues because Node, back then, was a project of an individual. It needed core contributors and a governing body.
This path was paved by Joyent, ultimately. Joyent hired Ryan Dahl and also purchased the trademark for Node. Joyent also confirmed the stability, reliability, and security of the Node.
And within a year, Joyent delivered on this promise and in partnership with Microsoft, Joyent released Node for Windows, opening Node to a much wider audience.

#### From 2011 to 2015: Node.js getting matured
From 2011 until now, Node has progressed in largely predictable ways.
In 2015, there was a rift among developers and doubts were raised that Joyent wanted to take Node in a different direction as compared to developers needs, so some devs forked Node and named it as io.js but later, it was merged back and the governance of the project was taken from Joyent to a unanimous body called The Node.js Foundation and till today, it’s being maintained by the Node.js Foundation.
Similarly, in 2015, the first non-beta version of Node was released.
Despite the great advancements, not all the changes have been worth celebrating. Most of the people/companies who adopted Node after 2012, didn’t adopt it for its runtime, CLI or built-in modules, but because of its largest ecosystem and the speed with which they can build applications using npm modules even without knowing how Node.js works.

Today we have an entire generation of developers who know MEAN stack, Mongoose, Bootstrap but they don’t know Node. The reason is obvious, some 5% of hipsters developed npm packages and the other 95% just used them without knowing how they work. People adopted Node, not because of Node but because of npm.

This ecosystem although it was very important and necessary at the start, for example, if there wouldn’t have been npm, Node might not have been at the same place it’s today. But it doesn’t mean that we should keep on relying on plenty of frameworks now as the core Node.js APIs are very much stable now. But most Node developers don’t even know about core Node APIs. They’re just an expert of Express and Mongoose, not necessarily Node.

*We’re going to reverse this trend in this writeup! 😎*

### What is V8, exactly?

Node, as you may have heard, is built on top of the Chrome V8 JavaScript engine. So to properly understand Node, we should understand V8 and JavaScript engine first.

Here is a takeaway: Modern computers only understand "machine code" natively. But developers, on the other hand, tend to write code using high-level languages like JavaScript, Python, etc, because the low-level code only consists of 0s and 1s and not super fun to write stuff directly.

In reality, there is no clear distinction among low-level and high-level languages, for people working directly on machine code, C++ might be a high-level language and for people working with Node.js, C++ might be a low-level language.

But one thing is obvious, code written in languages like JavaScript, C++, Python or Ruby, etc. is "alien" to a computer and it can't understand it.

So, the question is, from what steps a code (written in languages mentioned above) follows through before it becomes "native" for computers to understand.

In order to execute high-level code, the computer uses:

* Interpreters
* Compilers
* Transpilers

There are also other things in between, but we're not considering them for the sake of brevity.

#### Compiler
Takes source code and turn it into an executable file (a file full of machine code that a computer can understand)

#### Transpiler
Takes source code and turns it into the source code of another type. A common example of transpiling is turning CoffeeScript into JavaScript.

#### Interpreter
Takes source code and directly executes it by taking real-time intermediate steps such as compiling and optimizing on runtime. But they don't leave any artifacts behind as compiler does.

*So, what is V8?*

V8 is a JavaScript engine that converts JavaScript into machine code by using a Just-in-Time (JIT) compiler. The main difference here is that it does not produce any bytecode or executable.

If you ever interacted with Chrom DevTools Console REPL, that's V8 behind the scenes, executing your JavaScript.

However, V8 is not the only JavaScript engine, there are some other engines as well:

* JavaScriptCore (developed by engineers at Apple to power JavaScript in iOS and Safari)
* SpiderMonkey (developed by engineers at Mozilla and being used in Firefox browser)
* Chakra (developed by engineers at Microsoft and being used there)

Interestingly, SpiderMonkey was the first JavaScript engine, written by Brenden Eich, the same guy who initially developed JavaScript. He was working at Netscape and developed SpiderMonkey to be used in Netscape Navigator.

So, browsers, apart from doing plenty of other things, embeds JavaScript engines within them to execute JavaScript.
Node.js does exactly the same, it also does a lot of things and in order to execute JavaScript it embeds V8.

### What is Node.js, exactly?
Node.js is a server-side JavaScript runtime environment.
If you recall what V8 is, V8 is the car's engine and drivetrain. Node.js is everything else that makes the care and you're the driver.

In more technical terms, Node.js is a C++ application that embeds V8.
Node.js now presents itself as two applications:

* A script processor
* A REPL (Read Eval Print Loop)

#### Script Processor
You call the script processor from Terminal or CMD as follows:

```bash
node {script name}
```

For example:

```bash
node index.js
```

When you invoke such a script, Node.js does not just directly pass `index.js` to V8 but it first initializes a process named as `Event Loop`.

#### Event Loop
The simplest explanation of Event Loop could be:
The event loop is "continually" checking if there's any new task for Node.js to do.
Each pass, or in technical terms, each "tick" of the event loop checks if there's anything else is pending to do.

##### Event Queue
Now you might be thinking that `index.js` should be processed right away. And the answer is both, yes and no.
Remember that JavaScript contains two kinds of tasks, synchronous and asynchronous. Synchronous tasks are processed right away, but asynchronous tasks are placed in the event queue and are executed later in time.

As soon as task lengths in event queue downs to 0, the event loop process finishes, because there's no event left.

Many applications like servers that continually needs to listen to the requests, they continually create new tasks in event queue in order to keep running event loop otherwise it will exit the process.

None-blocking asynchronous tasks such as `setTimeout`, `setInterval`, API calls using `fetch` or any such asynchronous primitive, gets added to event queue and Node process them whenever it can.

In many programming languages, everything you do is blocking. For example, if you have a sequence of tasks, then the single thread will execute the first task and other tasks will be blocked. In some cases, this behavior is recommended but in the case of modern web apps, they need to handle and process multiple things at a single time.
