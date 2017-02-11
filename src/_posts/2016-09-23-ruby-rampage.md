---
layout: post
title:  "Hackathon: Getting Burned"
categories: jekyll update ruby rails planning
---

I was wrapping up 310 (Robust Production Quality Applications with Rails) after 3 busy weeks and 168 hours of work. I felt very comfortable building modest applications end-to-end and integrating with third party API's like Stripe and Twilio.

I was considering the review project I was going to build (#spaced repetition anyone?) that would encapsulate the course. As I'm reaching this point Gavin McGimpsey (we know him, we love him) posted about Ruby Rampage--a 48 hour hackathon.

Serendipity! It's always nice to outsource motivation for mundane work so you can save a portion of your willpower (AKA glucose/ketones) to stay mentally 'frosty' (we are all cognitive misers, so sayeth Nobel Psychologist Daniel Kahneman).

Plus, it was a chance to compete--iron sharpens iron and all that.

## The Verdict
So how did it go? Well, I went into the weekend confident, slipped on the starting line, and failed completely. It was terrific.

My project was incomplete, bolts exposed and no paint. I was too embarrassed to submit it!

Let's explore why this happened.

## First, The Project
What was I building? In the spring I'd built a simple Python agent to randomly send my girlfriend SMS messages (so I didn't have to) and I wanted to make it into a real application.

It seemed simple: an SMS batching app where you could write up a pool of messages, drag and drop them into different dispensers, configure the dispenser, and then use a clock process to spawn Sidekiq processes that would query the DB for overdue messages and use Twilio's API to send them.

And so, <b>Emote!</b> was born.

## Day 1: Grand Disillusionment

Something absurd happened; in a 48 hour contest I'd somehow managed to miss the first 16 hours. I'd tripped over my own feet from the starting block on a 100m dash. Despite constant reminders I'd somehow mixed up the time conversion. Wow, this was really stupid. I thought it was such a trivial thing that I gave it 3 seconds of attention.

That was mistake number one. But hey, it could have been fine, I could have adapted pretty easily. I'd only missed about 6 hours of actual work (due to the way it overlapped with my schedule).

But I didn't.

Did I learn from that mistake and go: 'hey, I have less time, maybe I should rescope.' Sanity check my feature list.' Nope, I was behind and the panic monster was roaring in my ear.

I entered into a code frenzy. I wrote some broken HTML/CSS, then some broken server side code, a few tests, and basically jumped around my code base like a chimpanzee chasing a squirrel through a tree. I spent most of the day flailing around. I made bugs and the more bugs I made the more I wanted to rush. It was a vicious cycle.

It was possibly the most unproductive 14 hours of coding ever. A day of temporary insanity.

## Day 2: All I can do, is all I can do
When I woke up the next day, yesterday seemed like a bad dream. Had I really panicked? That wasn't me--t was completely illogical! I then, rationally reminded myself, that I was a human being, driven by emotions, and therefore very probably just as capable of being irrational as any person--yesterday, being case in point.

I ran my fingers through my hair, blew out a breath and reminded myself of two things: 1) I was doing this project as a review project and the outcome of the hackathon was ultimately irrelevant and 2) that it the hackathon a new context for me and sucking at something new is always step one.

Immediately, the pressure lifted. I looked at my code, thoughts flashing like lighting bugs, and inspiration ignited. I simplified the scope of my project and got to work, fingers flying across the keyboard, the code singing to me like some kind of MVC choir. Miraculously I finished my project and won first place.

Oh, no, wait a minute. I forgot life isn't a movie. Damn.

So, I didn't miraculously finish but the code that I re-factored was a great foundation for finishing the project later. And if I hadn't panicked I could have produced a tightly made little app that would have been competitive with apps made by people who were far senior to myself.

I learned some lessons from this trial run and I'll do better next time.

## Failure + Reflection = Growth
Sometimes you know something theoretically but it hasn't been anchored by experience. This was one of those moments.

I'm happy it happened because the sooner the flaws in my thinking are exposed the sooner I can progress. I'd like to share a few tips and timely reminders brought home from this exercise:

* <b>Expect to suck</b> Learning and doing new things under pressure is a bad idea. This was a new context that I was unfamiliar with. I reminded myself of one of my most treasured beliefs (that I've carefully cultivated in myself) which is being okay with sucking at new things. I've actually begun to take pride in failing, because 'failing' is step one and success is step two. Bottom line: this belief takes the pressure off--which is good for learning.
* <b>Eustress vs Panic</b> Pressure is created by expectations that help drive you forward (much like TDD). It is right and proper to have have expectations but sometimes they need to be calibrated. Pressure is positive as long as it doesn't tip into anxiety...
* <b>Anxiety is Sneaky</b> This isn't the first time something like this has happened to me but it doesn't happen often. The panic monster roared when I said: OMG! I have 32 hours to build this project and my rationality when running to hide in the cupboard. I should have reduced scope. But I let the pressure block me from considering alternative solutions.
* <b>Scope Tightly and Give yourself Margin for Error</b>. Basically, follow Agile methodologies: build an MVP, have a tight feedback loop, and iterate. There will be problems. Have time for debugging and margin for mistakes.
* <b>Slow is smooth and smooth is fast.</b> This is something my skydiving instructor told me that I repeat to myself often. Apparently, in this case, it still didn't stick. Don't build garbage, build on axiomatic* code.

<small>Axiomatic: Usually used in math or logical reasoning, an axiom is an irrefutable argument. Here I mean orthogonal, well composed, robust code.</small>

## Conclusion
This experience was a real gem for me. And a wake up call--I really, really, really don't want to be the type of person who learns fire is hot from getting burned. The importance of strategizing upfront, before any endeavor, cannot be understated.

Next time I begin to rush I will remember this experience and remind myself that slow is smooth and smooth is fast. My hope is that next time you feel pressure and panic you will trigger (brain callback anyone?) and remind yourself of this as well.
