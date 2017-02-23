---
layout: post
title:  "WTF Javascript!?"
categories: javascript 
---

This was my initial reaction when introduced to prototypal inheritance. I was like, jeez, do you have to make it so awkward to instantiate objects? Why can’t you just be like everyone else.

I feel vaguely guilty now, a little like that teacher who called young Einstein dumb. Turns out prototypal inheritance is awesome. Cue Highschool Musical and other stories of upsetting the status-quo.
So…
# What is Prototypal Inheritance?
In a word it’s delegation — not inheritance at all.

In Javascript ‘ancestor’ (prototype) objects are generic workhorses that do the common tasks that all its bossy ‘children’ don’t want to do. The ‘children’ are snowflakes that have their individual unique methods — or should; I mean, you’re not duplicating code are you?

Well, if you are using classes… then you are.

# Classes vs Prototypes
In class based inheritance everything is a clone (think Star Wars). Each clone shares the same behaviors (methods) as Boba Fett. They look like Boba Fett, talk like Boba Fett, and shoot like Boba Fett.

In contrast Javascript prototypes are slaves to any object that extends them. Imagine every clone telling the original Boba Fett to shoot whenever they need to shoot. The analogy breaks down here a bit because Boba can only fly so fast with his jetpack but in code we don’t have that limitation…

Anyway, the advantage of this tyranny (who knew there were advantages to tyranny?) is that your code is DRY. Think about the case when you have a 1,000 or a 1,000,000 instances (clones) — do you really want to duplicate shared behavior? Since we are all obsessive about computational efficiency… the answer is no.

So, with classes, we have a thousand clones running around shooting guns. In Javascript all the clones just tell Boba to take care of it. Finally, clones have the time to take that pottery class they’ve always wanted to…
