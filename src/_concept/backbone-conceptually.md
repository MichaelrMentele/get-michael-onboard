Backbone is a library that makes client-side JavaScript apps easier to develop by providing boxed Javascript object in the Model-View design pattern. 

This pattern is similar to the Model-View-Controller pattern but much of the control logic is distributed throughout the views while business logic is pushed to the models. Our views have to be smart in order to react effectively to user interaction via event callbacks and ajax calls to the server.

So, what does Backbone provide?

#### Models & Collections
What is a model, what does it provide.

A model is useful as a unit sized container for data AKA an object. But more than that it can be implicitly bound to any view that renders it. This automagicness is extremely useful as it allows easy model updates from a view that contains the model without any need to search elsewhere for a reference to that model.

##### What is a collection, what does it provide.
A collection just provides some convenience methods to group together models. They are something of a glorified array with over 45 underscore methods to allow you to easily search and contort your collection. This is nice for cleanly categorizing rendering for applications with multiple types of objects. For example, if I had a website with posts, videos, and audiofiles I might want to do operations that act on all media of a certain type. I might want to filter searches based on media type and category. If I was looking for only audiobooks to listen to while I was in the car then I can easily select all books, and videos and hide them or remove them from view using selection criteria that passes a filtered version of my collection to my list rendering view.

Why use backbone models and collections?

Stable, convenient, code. Why use any library? Because you don't have to reinvent the wheel (poorly).

Note about sync...

Collections and models also autosync when modified sending out an ajax call to the server to sync their state between the browser and the server.

#### Views & Events
What are views?

These are objects that contain a reference to a dom element.

What are events?

Why use them? 

How do you use them?

Why would you want to use an events object?

#### Router/History

