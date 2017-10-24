## Week Three Recap

### Instructions
Fork this repository. Be sure to pull the latest changes to your local repo. Answer the questions to the best of your ability.

Try to answer them with limited amount of external research. These questions cover the majority of what we've learned this week.

Note: When you're done, submit a PR with a reflection in the comments about how this exercise went for you.

### Questions

1. What is the entry at the command line to create a new rails app?
- rails new appname
2. What do Models generally inherit from in rails?
- < ApplicationRecord < ActiveRecord::Base
3. What do Controllers generally inherit from in a rails project?
- < ApplicationController < ActionController::Base
4. How would I create a route if I wanted to see a specific horse in my routes fitle assuming I'm sticking to standard conventions and that I didn't want other CRUD functionality?
- resources :horses, only [:show]
5. What rake task is useful when looking at routes, and what information does it give you?
- rails routes : Prefix Verb URI Pattern Controller#Action
6. What is an example of a route helper? When would you use them?
- `new_category_idea` extremely useful for routing when dealing with nested routes and resources. Also useful for shothanding long URI's. For example, we can write the previous instead of writing '/categories/:category_id/ideas/new'
7. What's the difference between what `_url` and `_path` return when combined with a routes prefix?
- root_url   # => 'http://www.example.com/'
  root_path  # => '/'
  _path provide a site-root-relative path whereas _url returns an absolute path, including protocol and server name.
8. What are strong params and why are the necessary?
- Strong params specify the data that a model will accept. This is crucial when dealing with form validations. Validating server side is infinitely better than validating the form itself. This helps prevent various security attacks.
9. What role does `form_for` play in helping us create our forms?
- form_for is a helper that is most often used when dealing with models. They allow us to create or update the attributes of a specific model object. It also buils out HTML with attributes that are intuitive and easy to interact with.
10. How does `form_for` know where to submit the user's input?
- The rails built in method looks at the instance variable passed through and determines what to do with it accordingly.
11. Create a form using a `form_for` helper to create a new `Horse`.
```
<%= form_for @horse do |f| %>
  <%= f.text_field :name %>
  <%= f.text_area  :horsestuff %>
  <%= f.submit "Create" %>
<% end %>
```
12. Why do we want to validate our models?
- For security purposes and so that our views are complete. Meaning, we don't want to be able to create models with empty attributes. We also dont want to be able to create models with attributes that we don't want them to have. This would be devastating security wise.