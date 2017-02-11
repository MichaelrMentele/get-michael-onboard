## What is a First-Class Function?
A callback is a function reference or definition passed into another function (let's call it `OtherFunction`) as a closure and executed at some arbitrary time in that `OtherFunction` and so is said to have been 'called-back.' Callbacks are often anonymous but can be a named function as well.

# What is a closure?
A closure is a function that is said to remember its original context by binding to the surrounding 'artifacts' a fancy way of saying all the stuff (variables and objects) that existed in it's scope.

# What is a callback?
A callback is literally any function definition (or reference to a definition) passed to another function that is run at some arbitrary time in that other function. 

This 'passed in' function is termed a 'callback' because it is 'called-back' (AKA ignored until it is called--I imagine someone checking in for a flight then wandering around and waiting until he is 'called-back' to board).

It is also a closure in javascript because it shares the context, through lexical scoping, of the 'other function' it is called within.

It's funny, I thought callbacks were some more specific type of behavior but they are actually pretty generic and simple, by definition anyway. I've been using callbacks for years without even realizing it.
