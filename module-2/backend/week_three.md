## Week Three Recap

### Instructions
Fork this repository. Be sure to pull the latest changes to your local repo. Answer the questions to the best of your ability.

Try to answer them with limited amount of external research. These questions cover the majority of what we've learned this week.

Note: When you're done, submit a PR with a reflection in the comments about how this exercise went for you.

### Week 3 Questions

1. What is the entry at the command line to create a new rails app?

rails new <project name> -T -d="postgresql" --skip-spring --skip-turbolinks

2. What do Models generally inherit from in rails?

class ModelName < ApplicationRecord

3. What do Controllers generally inherit from in a rails project?

class ControllersName < ApplicationController

4. How would I create a route if I wanted to see a specific horse in my routes file assuming I'm sticking to standard conventions and that I didn't want other CRUD functionality?

`class Horse < ApplicationRecord
  def show
    @horse = Horse.find(params[:id])
  end
end`

5. What rake task is useful when looking at routes, and what information does it give you?

`rails routes` gives you a list of all routes available along with their prefix for how to call them with
path helpers.  The path also shows you if you need to pass an argument for the id when using the path helper.
This also shows you which controller the call will go to and which method will be performed from that controller.

6. What is an example of a route helper? When would you use them?

A route helper would be like `students_path` which would take you to the student index page.  You would
want to use these route helpers (specifically the path helpers) whenever you reference a uri path.

7. What's the difference between what `_url` and `_path` return when combined with a routes prefix?

`_url` will build the entire URL, including the protocol, whereas `_path` only builds the relative path.

8. What are strong params and why are they necessary?

strong params are a private method in rails that restricts access to the params of our object. It also restricts
what attributes can be updated. This is a security measure.

9. What role does `form_for` play in helping us create our forms?

`form_for` is a form helper in rails that builds the form for whatever object we pass it.  It also knows, based on
the view the form is in, if it's to edit or create a new thing! It also takes care of passing the params for that
object to the controller after user hits submit.

10. How does `form_for` know where to submit the user's input?

This is based off of what we pass form_for.  If I pass it `@students`, then it knows to send the info to the student
controller.  If it was in an `index.html.erb` file, then it knows it's passing to the `students#create` whereas if we
were in `show.html.erb`, it would know to send it to `students#update`.

11. Create a form using a `form_for` helper to create a new `Horse`.

`<% form_for @horse do |f| %>
<%= f.label :name %>
<%= f.text_area :name %>
<%= f.label :breed %>
<%= f.text_area :breed %>
<%= f.submit %>
<% end %>``

12. Why do we want to validate our models?

We want to ensure they are created with all fields so there are no `nil` cells in our db for that object.
This also helps us declare when an object is valid, and when it's invalid.

13. What are the steps of the DNS lookup?

When you type in a web address into your browser and hit enter, first the browser will look in it's cache to see if it knows
the IP address for that url. If not, it looks to the OS to see if it knows the IP address.  If not, then it asks the router and ISP if they
know the IP. If not, the server will first go to the Root Name Servers, then the Top Level Domain servers, then the Authoritative Name Servers
which will then return back along the chain, the IP address of that requested URL, all the way back to the user's browser.  

### Review Questions
14. Within a feature test and given the following HTML, write the code necessary to target the following section and check the person's name?

  `<section id="personal-info">
    <h3><%= @person.name%></h3>
   </section>
  `
Test:
`within('#personal-info') do
  expect(page).to have_content(person.name)
end`

15. How would you call the method `prance` from within the method `move` on a `Horse` instance?

def move
  prance
end

16. Given the following hash:

```ruby
furniture = {table: {height: 3, color: "red"}, purchased: true}
```
What is the different between how you would return true vs returning 3?  

To return true: `furniture[purchased]`
To return 3: `furniture[table][height]`
The 3 is in a nested hash so takes an extra step to get that value back.

17. What is inheritance?

This is where the parent class' methods "trickle down" to their children.  So if you have a
parent class with a method `average_items`, then any subclasses or children of that class
automatically have the method `average_items` as well, without it being explicitly defined within
that child class.

### Self Assessment:
Choose One:
* I was able to answer every question without relying on outside resources

Choose One:
* I feel confident about the content presented this week
