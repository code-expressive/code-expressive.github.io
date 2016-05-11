---
layout: code
title: "A Fast Introduction to Express.js"
description: "For more experienced users"
date: 2016-04-29
tags: [javascript, node, express, backend, beginner]
---

If you're familiar with Node.js and just want a quick introduction to Express.js's capabilities, this is for you!

* TOC
{:toc}

# Prerequisite: Install Node + npm
<div class="row content-row">
<div class="col-md-6 col-sm-12" markdown="1">

Ensure Node and npm are installed. You can download and install them both from [here](nodejs.org) and run the following.

You should see version numbers. If there are errors, the installation likely failed, or the PATH variable must be updated.

</div>
<div class="col-md-6 col-sm-12" markdown="1">

```
// Terminal
node -v
npm -v
```

</div>
</div>



# Getting Express
<div class="row content-row">
<div class="col-md-6 col-sm-12" markdown="1">

Create a new folder as your base directory. Run `npm init` , then run

</div>
<div class="col-md-6 col-sm-12" markdown="1">

```
// Terminal
npm install express --save
```

</div>
</div>

# Creating Your First App
<div class="row content-row">
<div class="col-md-6 col-sm-12" markdown="1">

Create a new `.js` file in your project directory and initialize the Express application like so.

</div>
<div class="col-md-6 col-sm-12" markdown="1">

```javascript
// app.js
var express = require('express');
var app = express();
```

</div>
</div>

# Handle a GET Request
<div class="row content-row">
<div class="col-md-6 col-sm-12" markdown="1">

Handle a basic GET request like so.

The callback function of `app.get()` takes in two arguments: a `request` object and a `response` object.

`request` contains data such as form data, URL visited, the remote IP address, and others.

`response` can send a simple string, an HTML file, JSON, or render from a templating engine.

Here, the `res.send()` function is passing a string to the client's browser.

</div>
<div class="col-md-6 col-sm-12" markdown="1">

```javascript
var express = require('express');
var app = express();

app.get('/', function(req, res) {
    res.send('HTTP 200');
});
```

</div>
</div>

# Listen to a Port
<div class="row content-row">
<div class="col-md-6 col-sm-12" markdown="1">

Upon initializing `node app.js`, we want our application to listen to a port on `localhost`.

`app.listen()` takes a port number and an optional callback function. This callback function is useful for posting a message to your console to ensure the server is running.

</div>
<div class="col-md-6 col-sm-12" markdown="1">

```javascript
var express = require('express');
var app = express();

app.get('/', function(req, res) {
    res.send('HTTP 200');
});

app.listen(3000, function() {
    console.log('Listening on port 3000...');
});
```

</div>
</div>
