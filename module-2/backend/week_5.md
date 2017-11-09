1. How do we make flash messages display on a page?
we would have to specify, within our application.html.erb layout that we are expecting flash messages. Like so: 
```
    <% flash.each do |type, message| %>
      <%= content_tag :div, message.html_safe, class: "alert alert-#{type}" %>
    <% end %>    
 ```
 And then, usually attach a flash message to an action in a controller. like so :
 ``` def create
      flash[:success] = "successfully created whatever thing"
     end
```
2. Where is cart information/temporary information usually stored?
Our cart is stored in the session and our cart information is typically abstracted to an ID and a corresponding value. These attributes would be stored in a hash like so { 1 => 2 } where one is the id and 2 is the quantity.
3. What might be some reasons not to store cart in our database? Are there any reasons why we would want to persist that information?
Say for instance we had a guest to our site and our guest wanted to add items to the cart... They did so and then had to log in to check out. So they logged in, and their cart data persisted. This was made possible by storing our cart in the browser session. Without doing so, we wouldnt have been able to have that data persist. 

4. What is the purpose of the asset pipeline?
The asset pipeline is basically a recursive compiler of assets. So it will search through your stylesheets, javascripts, and so on and include them all in your rails app. Not only will it include them, but it will also compile and minify them. Neat. 
5. Why do we precompile our assets?
It's more performant. 
6. What do each of the following tags do?

```ruby 
<%= stylesheet_link_tag "application" %>
<%= javascript_include_tag "application" %>
<%= image_tag "rails.png" %>
```
the first tag loads all of our stylesheets located within app/assets/stylesheets. the next does that same for javascript file. The third seems to be rendering an image with the name of rails.png

7. What are some of the elements of a great read me? What are some of the benefits of taking the time to update a readme for our project?
An outline, using badges, using images, gifs, videos, etc, having explicit instructions and or an explicit summary of the project, listing technologies used, having developer specific instructions for running the application. 
8. What are the top four accessibility issues that we as developers should be aware of?
Having elements with proper contrast, making all elements tabbable.  
9. `before_save` is an example of a what? Where in our Rails application would we find a `before_save`?
before save is a rails helper that runs a specified method before something is saved to the DB.
We used it in little-shop to run a method that defined an item price like so 
```
  before_save :get_price

  def get_price
    item = Item.find(item_id)
    self.price = item.price
  end
```
Very useful. 
10. Given the following object, how would we create a scope for all users who are active?

```ruby 
User.create(name: "Happy", active: true)
```
```
Class User < Application record
  scope :active, -> { where(active: true) }
end
```
11. What is the difference between a scope and a class method?
many people say “there is no difference between them” or “it is a matter of taste”.
