---
layout: post
title:  "Mental Models: The Dom"
categories: jekyll update javascript browser DOM
---

# The DOM is an Idea… Not a Thing
When I first learned about the DOM I was confused about how it was referred to as a ‘thing’ that could be accessed (false) and as a way of representing things (true).

The keyword is ‘model’ AKA representation. The DOM is a blueprint but often it is used to refer to the object tree that is the result of parsing markup. So, I thought I’d share this distinction.

# What is the DOM?
The DOM is a way of representing a HTML document as a collection of nodes where each node is an object. This collection is organized into a tree based on how the HTML elements were nested. Everything is a node in the DOM. Each node contains, as properties, it’s parent, siblings, and children nodes (among other properties and methods).

It is important to note that the DOM is language agnostic. That is, it is a convention, with which any programming language can generate a tree of nodes that represents some mark up. Most commonly this is done with Javascript.

# What Does it Look Like <i>Really</i>?
When we read about the DOM we typically see something like this:

<img src="/assets/posts/2016-08-17-mental-model-of-the-dom/dom.png" caption="Image from Kirupa.com">

This image is not what we are interacting with. When the HTML is parsed it creates a global object we refer to as the window (AKA context) for Javascript that lives in the browser. By default all other JS objects will delegate to the window as their prototype. You could say that all other objects extend this global object.

Okay, so what does the thing we interact with actually look like? Just a bunch of objects. In JS it would look something like:
``` javascript
// our page content
var body = { children: [h1, articl, div] };

// meta information and links
var head = { children: [link, script] };

// contains the html
var im_like_the_html = { children: [head, body] };

// contains the html and a bunch of methods
var im_like_the_document = { children: [html] };

// global object
var im_like_the_window = { children: [document] };
```

Of course each object would have many more methods and many more attributes (and probably extend a node object) but you get the idea. The document is really just some HTML parsed into a series of objects that you can use JS (and libraries like jQuery) to perform operations on.

It’s simple, but if you’re like me, it’s easy to overthink and overcomplicate what is going on behind the scenes. 

# Resources
https://www.kirupa.com/html5/traversing_the_dom.htm 
https://dom.spec.whatwg.org/
