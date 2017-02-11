---
layout: post
title:  "Constructors Are Nothing Special"
categories: jekyll update javascript
---

# Constructors

In other languages like Ruby, or Python we have classes. In JavaScript we have constructor functions. Constructors make lazy, bossy, children objects.

A normal function definition in JS looks like:

``` javascript
    function myFunction() {}; // Semicolon optional ;)
```

A constructor looks like:

```javascript
    function MyFunction() {}; // Capitalized by convention
```

What's the difference? Nothing!

Okay, cheap trick, I know. <i>All</i> functions are technically 'constructor functions.' The <b>magic</b> is in the implementation. Let's do another comparison, shall we?

A normal function will do some operation and return a value, mutate some object, or display something. We'll opt for the latter:

```javascript
    function myDancingFunction() {
        console.log("Waltzing...")
    }
    // Waltzing...
```

Now, in contrast, a constructor function returns a new object:

``` javascript
    function Dancer() {
        this.firstName = "Magic"
        this.lastName = "Mike"
        this.dance = function () {
            console.log("Dirty Dancing...")
        }
        // implicitly returns an object unless
        // you specify an explicit return
    }

    var chippendale = new Dancer() // calling the constructor...
```

How does it know to return an object? The `new` keyword does some magic and basically calls the constructor with the <b>context</b> of an empty object to serve as what `this` refers to.

Calling `Dancer()` with `new` is like passing in an object and modifying it like so:

```javascript
    function OtherDancer(ourNewObject) {
        ourNewObject.firstName = "Magic"
        ourNewObject.lastName = "Mike"
        ourNewObject.dance = function() {
            console.log("Other Dirty Dancing")
        }

        return ourNewObject
    }

    var chippendale = OtherDancer({})
    // chippendale is: {firstName: "Magic", lastName: "Mike"}
```

So, we don't really need the `new` keyword at all, it's just a convenience method... right? Not quite. There are a few other thing the `new` keyword does for us.

It also sets the `__proto__` property of our new object to the `prototype` object that every function holds a reference of.

For a quick conceptual introduction (using a Star Wars analogy) of prototypes and their role in behavior delegation click [HERE](https://medium.com/@michaelrmentele/wtf-javascript-8fd6d1aaed71#.pw6jgbze9)

## Constructors and Their Prototypes

Why do we care about the `__proto__` property? So-called 'inheritance' and defining types. Only, it's not <i>really</i> inheritance at all--its <b>behavior delegation</b> (which is one of the reasons javascript is so amazing). For more on this click the link above.

So, what if we want our dancers to get a little more <i>classy</i>? First, let's fix our constructor so we can pass in arguments:

```javascript
    function Dancer(firstName, lastName) {
        this.firstName = firstName
        this.lastName = lastName
        //same dance method...
    }
```

Now, we want to create other types of dancers that reuse the above from dancer. We do that like:

``` javascript
    function Dancer(firstName, lastName) {  ...  }

    function NiceDancer(){
        this.classyDancing = console.log("Waltzing...")
    }
    NiceDancer.prototype = new Dancer()
```

Now, our NiceDancer has a prototype object that is the object literal returned by `new Dancer()`. If we make a call like:

``` javascript
NiceDancer.prototype.dance()
// prints: Dirty Dancing...
NiceDancer.prototype.classyDancing()
// prints: Waltzing...
```

Notice we have access to that method, and all other methods, defined on our prototype from our `NiceDancer`. In classical inheritance methods are copied down to 'children.' In delegation, objects delegate to their 'parents' and search through their parents methods when a method is called--if the method doesn't exist on themselves.

![Lazy Behavior Delegation Chart]
(https://github.com/MichaelrMentele/blog-posts/blob/master/published/constructors_are_nothing_special/prototypalInheritance.png)

Note: We could have also put the dancing method on the `Dancer` prototype like: `Dancer.prototype.dance = function dance() {}`, but the prototype of `Dancer` is the global object, and the global object shouldn't be able to dance!

So, a prototype is an <b>object, linked to a constructor, so the constructor knows to pass that link to objects that it creates</b>. It does this by setting the `__proto__` property on new objects to reference the prototype.

## Analogy
A constructor is kind of like a recruiter, when you get hired she takes you (some roleless person) and says ‘hey, you are now a software engineer and this guy is your boss.’ The difference in Javascript is that a constructor ‘hires’ new objects and says ‘hey, this other object (the boss from before) is your slave, give it as many commands as you want and offload all your work onto it.’ Which, is a brutal, but refreshing model. So, you could say that new objects are lazy because they offload work to prototype (parent) objects in a kind of reverse pyramid scheme.

In essence, JavaScript is a bossy language full of lazy children.

Yup. That pretty much sums it up.
