## Week Four Recap

### Instructions
Fork or re-pull this repository. Answer the questions to the best of your ability.

Try to answer them with limited amount of external research. These questions cover the majority of what we've learned this week.

Note: When you're done, submit a PR with a reflection in the comments about how this exercise went for you.

### Week 4 Questions

1. What is a cookie?
A cookie is a tiny file and is how we mimic state in our browsers and with using HTTP.  The cookie is stored
on the client's browser and is sent in all requests to that domain.

2. What’s the difference between a session and a cookie?
A session is on the server side and is how the server "remembers" who a user is.
You can set the session in the app, then a cookie is sent to the client, then when
they make another request, their cookie is sent back and the session can see that info and keeps
track of that user and any other information we'd want to store.  

3. What’s a flash and when do you want to use flashes?
A flash is a type of session that typically expires after one request.  We usually use this to alert
the user to an error or success in creating or doing some other kind of action.

4. Why do people say “HTTP is stateless”?
Because it is! HTTP doesn't remember states or attributes.  Every time a request comes in,
HTTP treats it like a brand new thing!  This is why we need sessions and cookies, to keep our users
logged in so they don't need to verify their credentials every click.

5. What’s authentication? Explain.
Authentication is the process of verifying that a user is who they say they are.  We would use
a gem, like bcrypt, to hash that users password and store it in that encrypted state, then whenever
that user logs in, the password they type in is hashed and then compared to the hashed password in the
database and if they match, then the server knows that person is who they say they are.

6. What’s the difference between authentication and authorization?
Authentication is WHO someone is.  Authorization is WHAT that person can do and what they have access to.

7. What’s a before filter?
This is a statement that you can put in a controller that says before every (or a set) action, perform this
other method first, like authorization.

8. How do we keep track of a user once they’ve logged in?
Once they're logged in, we set the session with that user is.  Typically something like
session[:user_id] = user.id.  Then this session will persist until the user logs out and we set
the session[:user_id] = nil.

9. When do you want to namespace a resource? When do you want to nest a resource? What's the differences between those two approaches?
You would namespace a resource when it's not a separate resource on it's own.  For example, an admin is
a type of user. User is a model, but we wouldn't not also create an admin model.  Admin is a TYPE of user,
so we would namespace it.  
Nested resources can be used when we want to reflect the two resources relationships within our uri.  For example, if a job
belongs to a company and there is a one to many relationship, we might want to nest job within the company resource so
the company and job information is passed together within the uri.
If a resource is nested within a namespace, it changes the uri, but it doesn't necessarily pass that namespaced information,
like user_id, with it.

10. At a high level, what tools can you use to implement authorization? How would you use them?
Any kind of encryption gem would be good, like devise or bcrypt.  You'd add these as gems, then use their specific
methods and DSLs to ensure all passwords are hashed.

11. What's an enum, and what advantages does it offer? What data type needs to be in your database to use an enum? Where do you declare an enum?
An enum is something that allows us to associate an integer with a given value (like a string), so we can easily refer
to these items in the database and the model.  The datetype in the db would be an integer.  The enum part is declared within the model
that will contain the enum.

12. What are some strategies you can use to keep your views DRY?
Partials are a great option since view code is often reused.  You can also use if statements to specify
if something can be seen by only an admin or a user or a visitor, instead of making a new view for each
kind of user.


### Reviews Questions
13. Given the following array of hashes, how would I print an alphabetical list of holidays?
```ruby
[
 {holiday: {name: "St Patrick's Day", supplies: ["Corned Beef and Cabbage"]}},
 {holiday: {name: "Halloween", supplies: ["Candy", "Costume"]}},
 {holiday: {name: "Hanukkah", supplies: ["Menorah"]}}
]
```  
ActiveRecord: Holiday.order(name: :asc)
Ruby:

  holiday.map do |h|
    h[:holiday][:name]
  end.sort

14. How would you clean incoming data to ensure "$300" or "300.00" is stored as 300?

gsub(/\D/,'').to_i  but that only works for the first example...
The other one you could just do to_i.

### Self Assessment:
Choose One:
* I was able to answer most questions independently, but utilized outside resources for a few

Choose One:
* I feel comfortable with the content presented this week
