# Wizardy & Rails

If programmers are modern day wizards then rails is a Grimoire for Ruby branded magic.

For example, in Rails the single line in your routes file (the director of the Rails show), that is written like so:

```ruby
# /config/routes.rb
YourApp::Application.routes.draw do
    root to: 'posts#index' # defines the route action for '/'
    resources :swords # MAGIC
end
```

Is the equivalent of: 

```ruby
get '/swords', to: 'swords#index'
get '/swords/:id', to: 'swords#show'
get '/swords/:id/edit', to: 'swords#edit'
get '/swords/new', to: 'swords#new'
put '/swords/:id', to: 'swords#update'
post '/swords', to: 'swords#create'
delete '/swords/:id', to: 'swords#destroy'
```

That's a 7:1 gain! 

But all magic has a cost.

# Convention == Magic
A brief preface; the main tenet of Rails is 'convention over configuration.' And this is where all the magic is in Rails--the assumptions it makes about what you are trying to do. 

These work out to the spells you can cast, with the simple incantation above `resources :swords` you get those seven lines. But beware! All magic has it's price--especially blood magic--but for Rails the cost is memorizing conventions that are syntatically specific to the Rails DSL (Domain Specific Language).

For someone who likes to absorb principles over methods this is a cost worth considering. Learn to write your own spells before diving into Rails!

Anyway, for now let's accept we want to pay the cost and learn a bit more about Rails Magic...

# Alacadabra!
So, what else does Ruby provide us?

Auto rendering.

[auto rendering]