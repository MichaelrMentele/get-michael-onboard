Design questions are tricky because they are ambiguous and open-ended. I'm going to write a hypothetical back and forth of myself (me) and an interviewer, let's call him Ivan.

*Ivan*: So, Michael, today we are going to do a design problem together. Namely, how would you design imgur?

*Me*: Sure, that's an interesting question. First let's start by clarifying the scope of work so we know what problem we are trying to solve. If we invest that time upfront then we can weigh the tradeoffs of various solutions.

*Ivan* Okay, that sounds like a good plan.

*Me* Correct me if I'm wrong, but Imgur is essentially a giant panel of images sorted or ranked by some criteria, usually popularity, efficiently served. A core feature is that it loads new images async in the client.

*Ivan* More or less.

For the purposes of this question, are we going to focus on how the images are acquired, what websites are scraped, APIs used and that sort of thing? Or are we going to assume we are building a client that has access to an API and focused on that aspect?

*Ivan* Let's assume we want to build a client and an API is provided.

*Me* Sure. In that case, my next thought is what are the concerns of our client. Can I assume the core feature is a single page, with some sorting criteria at the top and that has infinite scrolling. Is that assumption okay or is there some other feature we'd like to focus on?

*Ivan* That sounds good for now.

*Me* Alright, then I'm assuming we want to optimize for user time which means minimal load time. I'm going to assume we can sort by popularity and recency for now and then think about what my API would look like. Then think about how to make it as fast as possible. Probably with some sort of pre-fetching and/or caching.

*Ivan* I agree let's optimize for user time.

*Me* Hmm, what information does my API need to provide? It needs to provide:
- images
- pagination
- categories (popular, recent)

The client or the server need some way of keeping track of what images have been fetched and what haven't been fetched for the given session.

I could increment a count of the number of images. If I've loaded 50 of the most popular images sorted by popularity and have this count be granular one by one. I could 'paginate' and load up 'chunks' of images. This might make request usage more efficient. If I have a fixed number of images per row, and fixed rows per panel. Then I can pre-fetch the *next* panel of images.
