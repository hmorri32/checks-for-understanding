## Week One - Module 2 Recap

Fork this respository. Answer the questions to the best of your ability. Try to answer them with limited amount of external research. These questions cover the majority of what we've learned this week (which is a TON!).

Note: When you're done, submit a PR.

1. List the five common HTTP verbs and what the purpose is of each verb.

* **GET POST PUT PATCH DELETE**
* GET is used to read or inspect a ceratin endpoint or resource
* POST is used to create a resourse at a specific URI
* PUT is used to edit an entire resource at a specific URI
* PATCH is used to edit a specific part of a resource at a URI
* DELETE destroys a resource at a certain URI

2. What is Sinatra?

* Sinatra is an ultra light, rack based, ruby specific, MVC, web application framework

4. What is MVC?

* MVC stands for model view controller. This is an architectural pattern used to design applications. It breaks the application into three seperate logical components.
* The model component handles all data related logic that the user works with. It also acts as a go between for the DB and the controller.
* The view component is used for all the UI and UI logic of the app.
* The controller acts as an interface between the model and the views. Routes and URIs are defined here. The controller also allocates resources to certain views.

5. Why do we follow conventions when creating our actions/path names in our Sinatra routes?

* So that our team does not hate us. Also, following predefined schemas and patterns helps the team work in unison, with a clear goal, and with clear expectations and procedures. Furthermore, convention dictates WHERE code should live. And this makes navigating a codebase easier.

6. What types of variables are accessible in our view templates without explicitly passing them?

* Class methods are avalaible. ie `Station.all` or `Station.average` or what have you.

7. Given the following block of code, how would I pass an instance variable `count` with a value of `1` to my `index.erb` template?

  ```ruby
  get '/horses' do
    @count = 1
    erb :index
  end
  ```

8. In the same code block, how would I pass a local variable `name` with a value of `Mr. Ed` to the view?

  ```ruby
  get '/horses' do
    @count = 1
    @name  = 'Mr. Ed'
    erb :index
  end
  ```

9. What's the purpose of ERB?

* ERB lets use write ruby code inside of an HTML environment like so

```erb
<% @stations.each do |thing| %>
  <p><%= thing.name %></p>
<%end>
```
10. Why do I need a development AND test database?

* you need both DBs so that you dont accidentally torch your entire database while running your tests. Having two seperate environments let us test functionality without compromising our DB.

11. What is CRUD and why is it important?

* CRUD stands for create read update delete. It is important because, if you think about it, the entire internet is nothing but CRUD-ing stuff.

12. What does HTTP stand for?

* HYPERTEXT TRANSFER PROTOCOL

13. What are the two ways to interpolate Ruby in an ERB view template? What's the difference between these two ways?
```erb
<!-- this allows us to run ruby methods -->
<% @stations.each do |thing| %>
<!-- this `=` allows us to render a value -->
  <p><%= thing.name %></p>
<%end>
```
14. What's an ORM?

* ORM is a program that connects disparate data sources by defining relationships between them.

15. What's the most commonly used ORM in ruby (Sinatra & Rails)?

* ACTIVE RECORD

16. Let's say we have an application with restaurants. There are seven verb + path combinations necessary to provide full CRUD functionality for our restaurant application. List each of the seven combinations, and explain what each is for.

```ruby
class CoolRestaurantApp < Sinatra::Base
  get '/' do
    #stuff and things
    erb :'some-index-page'
  end

  get '/restaurants' do
    erb :restaurants
  end

  get '/restaurants/new' do
    erb :new
  end

  get '/restaurants/:id' do
    @restaurant = Restaurant.find(params[:id])
    erb :show
  end

  post '/restaurants' do
    Restaurant.create(params[:restaurant])
    redirect '/restaurants'
  end

  get '/restaurants/:id/edit' do
    erb :edit
  end

  set :method_override, true
  put '/restaurants/:id' do |id|
    Restaurant.update(id.to_i, params[:restaurant])
    redirect "/restaurants/#{id}"
  end

  delete '/restuarants/:id' do |id|
    Restaurant.destroy(id.to_i)
    redirect '/restaurants'
  end
end
```

17. What's a migration?

* Migrations manage the evolution of a schema and are used to define update or destroy tables and their attributes.

18. When you create a migration, does it automatically modify your database?

* NO, it does not. You must rake db:migrate post creation

19. How does a model relate to a database?

* A model serves as the go between between the app and the DB. For our purposes, our model interacts with active record, which then interacts with our DB.

20. What is the difference between `#new` and `#create`?

```ruby
# if we want to instantiate and then save it to the DB we must:
thing = Station.new(stuff)
thing.save
# If we want to do that in one fell swoop we can:
Station.create(stuff)
```