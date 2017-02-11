---
layout: post
title:  "Do You Really Know How Functions Work in Javascript?"
categories: jekyll update javascript
---

A function is pretty simple, right? It's just a reference to a block of code that get's executed when called...

Kind of, but not quite. You see, functions also remember scope and bind to that scope when called, even when the context has changed, they can remember their local context. This is called a closure.

## Lexical Scope of Nested Functions

What happens in the following code?

``` javascript
var greeting = "How do you do?";
function howdy() {
    var greeting = "howdy";
    function speak() {
        console.log(greeting);
    }
    return speak();
}

howdy();
```

If your answer was it returns `howdy` then congratz! Now, what if we make one small tweak?

``` javascript
// code omitted...
    return speak;
```

This time instead of returning the evaluation of the `speak` function we return a reference (notice the missing parens). If we invoke that function with `howdy()();` in the global context, what will our greeting be?

Hint: it will still be `howdy`.

Hmm, it seems that somehow we are retaining information with our reference to speak. To prove this to you, let's look at another example.

What if we called `howdy` as an anonymous IIFE like this:

``` javascript
var greeting = "How do you do?";
var im_an_IFFE = function () {
    var greeting = "howdy";
    function speak() {
        console.log(greeting);
    }
    return speak;
}();
```

So, we define the funtion and call it on the same line (IFFE) and our `im_an_IFFE` variable gets a reference to the nested `speak` function whose context is gone forever. Right?

Nope! Guess what, calling `im_an_IFFE()` still returns "howdy".

How is this happening?

## Closures

If you haven't heard of closures this may have been very confusing. Afterall, context in JS is important, especially for functions that make use of the `this` keywords like with the Constructor Pattern.

But, when a function is created it doesn't just remember the block of code inside it, it also remembers its environment. It is said to 'bind' (following lexical scoping rules AKA inside out) to its surrounding artifacts AKA variables. This is also true in Ruby procs and lambda functions. Also, Python handles closures much like JS.

Why do all these languages use closures? They are especially useful for things like callbacks and functions as first-class objects (more on this later).

## Why is it Called a 'Closure'?
So, a closure is a function along with its environment. But why do we call it a closure? A function is like us, it doesn't like unanswered questions, like free variables and so searches for answers. When it finds them it is completely defined and, thus, finds 'closure.' And couldn't we all use a little bit more closure in our lives?

If you are a programmer, then the answer is a definite *yes*.

Yeah. I went there.

Anyway, that is a quick definition of closures. If you know callbacks and how first-class objects first then you're probably a Jedi master programmer.

As for me, I'm a sith...(\#lightning is cool)

### Notes
For an excellent dive into closures (and JS in general) I recommend checking out 'Headfirst into Javascript.'
