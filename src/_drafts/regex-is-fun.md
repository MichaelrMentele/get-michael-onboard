# Why Writing Gibberish is Smart
You know those crazy people who write stuff that we don't understand and looks like nonsense? Maybe they are smarter than they look.

I used to think that regex was baffling but then I spent about an hour (maybe two) learning about character classes, alternation, anchors, quantifiers, and that thing where you track the pattern between two parens. 

Now, I know gibberish--and it's awesome!

## Why It's Awesome
So we all know how to split a sentence into an array of words by spliiting on spaces, right?

```javascript
var sentence = "Hello, I am piece of wood--please don't split me."
wordSplinters = sentence.split(" ") // Argh, why?!
// ['Hello,', 'I', 'am', 'a', 'piece', 'of'...]
```

But 