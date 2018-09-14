### Week 5 Questions

Re-pull from this repository. Answer the questions to the best of your ability. Try to answer them with limited amount of external research. These questions cover the majority of what we've learned this week (which is a TON!).

Note: When you're done, submit a PR.

### Week 5 Questions
1. How do we make flash messages display on a page?
In the controller, you would write `flash.notce = "You have succesfully saved your edit."` It would go into the
controller action that is creating that message, then whatever page that action redirects to or renders after the action
is complete, is the page the flash would show up on.

2. Where is cart information/temporary information usually stored?
In a session.

3. What might be some reasons not to store a cart in our database? Are there any reasons why we would want to persist that information?
Pros for storing cart in a session is that it's easy to update and can persist from a visitor to a user. Plus, if it were in a database
there would be a lot of calls to the db to change and update the cart as a user peruses the site.
However, if that information was in the db, then you could send follow up reminders to that user reminding them of what is in their
cart. Or you could keep information for them in the db reminding them of items that used to be in their cart that they might
want to revisit.

4. What is the purpose of the asset pipeline?
To speed up load time.  Instead of loading 15 (or hundreds) of CSS files, rails will compile like files into one asset that it will deliver to the browser so it can make
fewer requests.

5. Why do we precompile our assets?
To make less requests from server to client to load all the assets.

6. What do each of the following tags do?

```ruby
<%= stylesheet_link_tag "application" %>
<%= javascript_include_tag "application" %>
<%= image_tag "rails.png" %>
```
All of these are action helpers that tell rails in production to look for the asset with the thumbprint instead of the regular file.

7. What are some of the elements of a great read me? What are some of the benefits of taking the time to update a readme for our project?

8. What are the top four accessibility issues that we as developers should be aware of?

9. `before_save` is an example of a what? Where in our Rails application would we find a `before_save`?
This is a callback. We would find these in our controllers to tell it to do some function before saving an object or object edit.

10. Given the following object, how would we create a scope for all users who are active?

```ruby
User.create(name: "Happy", active: true)
```
User.where(active: true)

11. What is the difference between a scope and a class method?

A scope just limits the amount of objects you would need to sort through in order to get your desired results.  A class method sorts through the entire table to find
your result.

### Review Questions:  
12. Given the following hash:  

```ruby
{cart: {"17" => 4, "204" => 52, "29" => 22}}
```

  12a. How would you add item with id of 48 with a quantity of 4?  
  cart["48"] = 4

  12b. How would you increase the quantity of item 29?  
  cart["29"] += 1

  12c. How would you find out how many items your user is thinking about purchasing?   
  cart.values.sum

13. What is polymorphism? How does it relate to duck-typing? What are two ways you use this in everyday Rails applications?  
Polymorphism refers to being able to use different objects in rails that might have similar attributes to another data structure, in that other way. If it looks like a duck and acts like a duck, then you can treat it like a duck.  For example, a session
is not actually a hash, but it looks like one and acts like one, therefore we can treat it as a hash.  

14. How would you clean the string "(630) 854-5483" to "630.854.5483"?  
gsub(/\D/, "").scan(/(...)(...)(....)/).join(".")
I'm sure there are better ways to do this, but this works for this case!

### Self Assessment:
Choose One:
* I was able to answer most questions independently, but utilized outside resources for a few


Choose One:
* I feel comfortable with the content presented this week
