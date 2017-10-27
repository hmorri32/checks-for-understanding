## Week Four Recap

### Instructions
Fork this repository. Answer the questions to the best of your ability.

Try to answer them with limited amount of external research. These questions cover the majority of what we've learned this week.

Note: When you're done, submit a PR with a reflection in the comments about how this exercise went for you.

### Questions

* What is a cookie?
A cookie is used to store persistant data across page loads. Cookies are little chunks of data that are stored client side and are used to validate information between server and client such as cart history or what have you.
* What’s the difference between a session and a cookie?
The information packet for a session is stored server side while for a cookie it is stored client side.
* What’s a flash and when do you want to use flashes?
The flash is a built in rails method that allows us to pass temporary hashes around our application. They are usually (at least as far as we know...) used to flash messages for actions, IE error messages or success messages for creating updating deleting resources.
* Why do people say “HTTP is stateless”?
Not sure actually, seeing as how introducing cookies and sessions introduce state to HTTP. Would love more insight into this.
* What’s authentication? Explain.
Authentication allows us to specify what users are allowed to access our application. It basically answers the question - are you allowed to be here?
* What’s the difference between authentication and authorization?
While authentication opens the door to the party, authorization specifies what you are actually allowed to do at said party. If my party were an idea box, say, authorization would specify what actions an authenticated user is allowed to do.
* What’s a before filter?
Before filters run before any of our controllers crud like methods.(Unless explicitly stated.) They are fabulous for refactoring purposes and also to keep our controller clean. So we could say, before each of our crud actions, please go and find this specific resource we are looking for and make it available everywhere. As opposed to writing that over and over in each method.
* How do we keep track of a user once they’ve logged in?
Usually by specifying what actions they can do in our ApplicationController. As all other controllers inherit from this one, we can just declare behavior there and not have to worry about it again. Unless we want to conditionally render things and stuff in our views.
* When do you want to namespace a resource? When do you want to nest a resource? What's the differences between those two approaches?
namespace :stuff { resources :things }
new_stuff_thing    GET   /stuff/things/new(.:format)   stuff/things#new
This approach offers a way to organize our information more than anything. It allows us to create nested views and nested controllers. THis is a fantastic approach when dealing with admin users and so forth.
When we nest resources, we have to specify an ID for each of the resources. meaning, where as before we had the above, now if we did...
resources :stuff { resources :things}
we would have
new_stuff_thing GET /stuff/:stuff_id/things/new(.:format)  things#new
So namespacing seems to be a better approach when we have ONE 'stuff' as opposed to many.

* At a high level, what tools can you use to implement authorization? How would you use them?
Bcrypt...To specify what sort of user roles exist and to then specify what each role is capable of. At a super high level.
* What's an enum, and what advantages does it offer? What data type needs to be in your database to use an enum? Where do you declare an enum?
Enums are super spicy and allow for translation of integers in our DB, to words or other such things in our views and models and so on.
So, in our db, if we had a user role with a default int of 0, we could specify an enum that would translate that 0 to ['cooluser', 'whatever user', 'ultra admin'] or whatever you please.
* What are some strategies you can use to keep your views DRY?
Form partials... Or, rather, I guess any repeated view can become a partial.
