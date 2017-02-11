---
layout: post
title:  "Javascript Context"
categories: jekyll update javascript 
---

# Scope in JavaScript
Scoping rules in any language are critical to understanding the context your code is operating in and what variables functions have access to.

In JavaScript everything lives inside a global object. Even the variables that you define are really just parameters on the global object. In the browser this global object would be `window.`

Within the global object each function has its own locally nested scope. Make sure when defining variables in a localscope you do so with `var` to prevent it from jumping to a globally scoped variable.

``` javascript
// Global scope out here
var foo = function () {
    // Local scope in here
}
```

Now, this is fairly typical among most programming languages but Javascript has some quirks. You can also access global variables within your local scope. Typically, languages such as Ruby have a special notation to denote globals `($global`), but in JS there is no such distinction. All variables declared outside a function are available to it.

``` javascript
var global = "I am global"

var foo = function () {
    var local = "I am local"
    console.log(global)
    console.log(local)
}

>> "I am global"
>> "I am local"
```

This is called lexical scoping.

## Lexical Scoping
Every time you define a function within a function it can access the variables of the function it is nested within. This is different from a language like Ruby whose functions aren't first class objects and don't have lexical scope (but its closures--blocks and procs--do).

Lexical scoping just means, that in the look up chain, the furthest nested function has access to variables all the way up the chain to the top but functions above it can't access *its* variables. This works well with JavaScripts prototypal inheritance (more on that later).

Accessing variables outside of the immediate scope is the behavior of a closure (more on this later as well).

## What is Wrong with This?
### Implicit Function Context
`this` is a reference to the context of the current object in lexical scope. But it doesn't work as nicely as you would expect. `this` doesn't refer to the current function or object it is contained in but rather the object or context with which it was *called.*

```javascript
var myFunction = function() {
    console.log(this); // this === the global object
};
myFunction(); // returns global object [object Window]
// this makes sense because myFunction() is equivalent to window.myFunction()

var myObject = {
    myMethod: function() {
        console.log(this); //this = Object {myObject}
    };
};
```

No surprises here. But something strange happens when we nest a function within a function.

``` javascript
var test_context = {
    foo: function() {
        console.log(this);
    }
};

object.foo(); // this is object test_context
var bar = object.foo;
bar(); // this object Window
```

Why did the context change for the function call? When we reassigned the method to bar we didn't take the object with it. Just the function. Now when it is called it is bound to the global object's context. The binding happens when the function is executed--not defined.

### Explicit Function Context
There a several ways we can use to minimize context loss for functions. We can use the `call`, `apply`, and `bind` methods.

``` javascript
foo = function(){
    console.log(this);
};

foo.call(object); // calls a function with a specific object as the context would log object
foo.apply(object, []); // same as call
foo.bind(object); // permanently binds object to foo so that whenever it is called it is called within that context.
```

Context loss can be very confusing once you start passing things around but the thing to remember is that the context binding happens when a function is called or executed and not when it is defined.

Next week I'll be diving more in depth into closures and context loss.
