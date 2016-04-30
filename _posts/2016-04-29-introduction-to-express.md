---
layout: post
title: "An Introduction to Express.js"
date: 2016-04-29
tags: [javascript, node, express, backend, beginner]
---

# What is Express?

Express.js is a "Fast, unopinionated, minimalist web framework," as advertised on their [webpage](expressjs.com).

So what does that mean?

A framework is like a half-built house, where all the walls are in place, but the rest is up for you to build. The rest, like doors, windows, what kind of wallpaper or flooring you want, is your decision.

You can imagine a web framework like a website already half-built for you. You don't have to build the controllers for handling GET and POST requests, nor do you have to write code for how routing will work in your app. Instead, you get to code the important stuff, like what to do when a GET request is received from a particular URL.

While other frameworks give you more capabilities at your fingertips as one package, Express prefers to keep everything as lightweight as possible and lets you add modules as you see fit. For instance, you won't find authentication capabilities in Express, but you can certainly install [Passport](passportjs.org) to handle this.

# Getting Express

This is going to require a bit of command line work. I'll be referring to the command line prompt as Terminal, as it is the OSX/Linux implementation of the command line. On Windows, it's called the Command Prompt, and can easily be run by pressing the Start button and typing `cmd`, then pressing Enter. The commands will be the same regardless of operating system, but I'll have two version of each step if they differ across OS's.

First, you'll need Node.js and npm installed, which is quite easy. Download and install Node from [here](nodejs.org).

To check if everything installed correctly, you can run `node -v` in your Terminal to get the version number.

Installing Node this way should also install the Node Package Manager (npm). You can confirm this by running `npm -v` in Terminal.

After confirming your Node/npm installation, create a new folder wherever you like, then navigate to it using Terminal and execute the following:

```
npm init
```

This will add a `package.json` that will describe the dependencies of your project, as well as some basic info about the project.

To install the Express package, execute

```
npm install express --save
```

This will add Express to your `node_modules` folder. The `--save` adds Express as a dependency to your `package.json`.

# Your First Server

Create a new file called `app.js` in your base directory. Now, we need to tell Node, which we will use to run our server, that our app will require Express.

In your `app.js`, add the following:

```javascript
// app.js

var express = require('express');
// Now Node will know to pull in Express into this app.
```

Then, we can run the top-level function `express();` and assign the returned object to `app`.

```javascript
// app.js

var express = require('express');
var app = express();
```

# GET Requests

Now, our `app` object has several very useful methods that tell the application what to do when a user arrives at your webpage (among other things).

One of those things is the method `app.get()`, which handles GET requests to a specified URL.

Here's how to use it:

```
app.get(path, callback [, callback...])

path (String): the URL
callback (Function): what to do when the user arrives at the URL
```

The callback function should take in a request (`req`) object and a response (`res`) object. For example:

```javascript
app.get('/', function(req, res) {
    // what to do when the user arrives at the URL
});
```

`req` is the request object, which may contain HTTP headers, form data, etc.

`res` is the response object, which may contain data that is sent back to the user's browser.

For this exercise, let's do something simple. When the user arrives at `example.com`, we'll respond with a short message by using the `res.send()` method.

```javascript
// app.js

var express = require('express');
var app = express();

app.get('/', function(req, res) {
    res.send('Hello there!');
});
```

# Listening to a Port

However, this app still won't do anything yet. We need to have the app listen in on a port number.

We can do this using the `app.listen()` method, like so.

```javascript
// app.js

var express = require('express');
var app = express();

app.get('/', function(req, res) {
    res.send('Hello there!');
});

app.listen(3000);
```

Now the app will only respond if you connect via port 3000.

# How Do I Know When My Server is Running?

If you run `app.js` as it is right now, you won't have any indication it is running.

To fix this, we can add the following function to `app.listen()` that will put some text in your command line so you know the server is running without error:

```javascript
// app.js

var express = require('express');
var app = express();

app.get('/', function(req, res) {
    res.send('Hello there!');
});

app.listen(3000, function() {
    console.log('Server is running!');
});
```

To start the server and see your handiwork, go back into the command line and ensure you're in your base project directory.

Then, run

```
node app.js
```

Go into your browser and type in `localhost:3000` into your URL bar. You should see a message that says "Hello there!"
