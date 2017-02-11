---
layout: post
title:  "Use Wishes to Solve Programming Problems"
categories: jekyll update ruby rails planning
---
Code is hard. Some problems just seem like too much and you don't know where to start. The complexity is overwhelming or the topic is just too new.

Make a wish I say--make a wish!

Not upon a star or to your fairy god mother; I'm talking about every programmers friend--abstraction.

## The Wishlist
The idea is simple, when you have a problem statement; write a highlevel list of functions you wish you had to solve the problem for you. This is call declarative abstraction.

Meaning, you 'declare' that there is this black box that crunches widgets into what-chits.

Let's say I had to write a program that would run the matrix. Now, I have no idea how to code the Matrix but I can probably break it into a abstractions I wish existed and pretend some other smart guy would write them.

It might be like:

```javascript
runTheMatrix(){
    while (matrixExists()) {
        updateEnvironment(); // I have no idea how to write this code
        trackPeopleStates();
    }    
}
```

Now, right now I've just broken the problem into two problems by 'wishing' I had a function that could handle the environment object and handle the people objects--the agents might do their own separate thing and interact with the environment through events. Again, no clue. The important thing is the problem space just got cut in half.

Alright, now we do the same thing for our updateEnvironment function. What does this funciton even do? Well, it like handles all the things not having to do with people. So things like buildings, weather, temperature of rooms and places, the night sky, physics etc.

We are assuming the matrix isn't deterministic and that people will basically need event handlers for all of their actions. So the environment is a purely reactive environment.

```javascript
function updateEnvironment() {
    handlePhysics() // tracks the status of all molecules
    handleAnimals()
    handleWeather()
    ... // The list goes on... how did those computers do it? Probably not functionally, probably with some kind of dynamically driven code that wrote itself and spawned the necessary functions to motivate the world but I digress.
}
```

Great, now we write a wishlist for handlePhysics(), and then... You guessed it! We do it again and again until we get to a problem we know how to solve.

From handlePhysics we might drill down to a function like:

```javascript
function computeForce(mass, acceleration) {
  mass * acceleration
}
```

That's it! This is a recursive problem decomposition algorithm. Start at the top, your high level 'wishlist' and keep going until you find something simple enough you can solve.

Now, go create the matrix!
