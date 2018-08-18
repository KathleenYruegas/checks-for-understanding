## Week One - Module 2 Recap

Fork this respository. Answer the questions to the best of your ability. Try to answer them with limited amount of external research. These questions cover the majority of what we've learned this week (which is a TON!).

Note: When you're done, submit a PR.

### Week 1 Questions

1. List the five common HTTP verbs and what the purpose is of each verb.
GET - read resource
PUT - updates resource
POST - create resource
DELETE - deletes resource
PATCH - updates some of the data whereas PUT will change all the data

2. What is Sinatra?
This is a web-app framework build on Rack which allows us to build web-apps with
Ruby.

3. What is MVC?
This is a design pattern, stands for Model, View, Controller. It separates functions
to maintain SRP in our code.

4. Why do we follow conventions when creating our actions/path names in our Sinatra routes?

We need to match up with HTTP verbs that come through and with Sinatra and Rack's frameworks.

5. What types of variables are accessible in our view templates without explicitly passing them?

Instance variables.  Also local variables if they've been defined correctly.


6. Given the following block of code, how would I pass an instance variable `count` with a value of `1` to my `index.erb` template?

  ```ruby
  get '/horses' do
    @count = 1
    @name = "Mr. Ed"
    erb :index
  end
  ```

7. In the same code block, how would I pass a local variable `name` with a value of `Mr. Ed` to the view?

8. What's the purpose of ERB?

This is Embedded Ruby, it tells our html to run the code inside the <% %> as Ruby code.

9. Why do I need a development AND test database?

The development db gets built throughout your app, the test db is built and destroyed
with each test.  This allows you to input information that might not be there yet
in your development db to ensure it will work once it gets there.

10. What is CRUD and why is it important?

Create, Read, Update, Delete.  This is important for many reasons. These are the main functions
of the db and they align with the http verbs.

11. What does HTTP stand for?

Hyper Text Transfer Protocol.

12. What are the two ways to interpolate Ruby in an ERB view template? What's the difference between these two ways?

<% %> will run the Ruby code
<%= %> will echo the Ruby code and display it in our view

13. What's an ORM? What does it do?

Object Relational Mapper. This allows us to make models out of our db so we're working with
our Ruby objects instead of the relational language of SQL.

14. What's the most commonly used ORM in ruby (Sinatra & Rails)?

ActiveRecord (AR)

15. Let's say we have an application with restaurants. There are seven verb + path combinations necessary to provide full CRUD functionality for our restaurant application. List each of the seven combinations, and explain what each is for.

GET '/restaurants' Will allow us to view all restaurants
GET '/restaurants/new' Will take us to the page where we can create a new restaurant
POST '/restaurant' Will allows us to save a new restaurant
GET '/restaurant/:id' Will allow us to view a specific restaurant
GET '/restaurant/:id/edit' Takes us to page where we can make edits to that restaurant
PUT '/restaurant/:id' Will save and actually make the edits to that restaurant.
DELETE '/restaurant/:id' Will allow us to delete a specific restaurant


16. What's a migration?

This is like a blueprint for creating our database.  Every creation, modification, and deletion to our database will be made with a new migration.

17. When you create a migration, does it automatically modify your database?

No, you have to run rake db:migrate.

18. How does a model relate to a database?

The model is how we interact with our database, how we manipulate and process all the data which the model will then give to the controller.

19. What is the difference between `#new` and `#create`?

`#new` will create a new instance of that class and `#create` will do both
`#new` and `#save` for that instance.

20. Given a table named `animals`, What is the SQL query that will return all info from that table?
    `id     name        number_of_legs
    -----   ------      --------------
      1     panda       4
      2     giraffe     4
      3     whale       0
      4     bird        2
    `
SELECT * FROM animals;


21. Using the same table, What is the SQL query that will return only the animals that have 4 legs?

SELECT * FROM animals WHERE number_of_legs=4;


### Review Questions:  
22. Given a CSV file (“films.csv”) with these headers [id, title, description], how would you load these into your database to create new instances of Film?  

File.foreach('/films/csv', headers: true, header_converters: :symbol) do |row|
  Film.create(row)
end


23. Given the following hash:
```
activities = {
  hiking: {cost: $0, supplies: ['hiking shoes', 'water', 'compass']},
  karaoke: {cost: $10, supplies: ['courage', 'microphone']},
  brunch: {cost: $35, supplies: ['mimosa flutes']},
  antiquing: {cost: $200, supplies: ['list of antique stores']}
}
```
How would I add 'granola bar' to things you should have when hiking?

activites[hiking][supplies] << 'granola bar'

24. What are the 4 Principles of OOP? Give a one sentence explanation of each.

Encapsulation - this is the process of deciding which data is accessible to
the public and what data is private.

Abstraction - This is the idea of each class only knowing enough about another
class to be able to interact with it, it does not need to know the inner workings
of that class, it only needs to be aware of the interface.

Inheritance - expresses the 'is-a' or 'has-a' relationships between objects. This
allows us to reuse code which is given from the parent to the children and helps
us DRY up our codebase.

Polymorphism - this is closely related to inheritance and allows us to write
code that works for a superclass and should then work with any subclass as well.


### Self Assessment:
Choose One: (erase the others)
* I was able to answer most questions independently, but utilized outside resources for a few

Choose One:
(I know it says one, but I feel both overwhelmed and comfortable.)
* I feel comfortable with the content presented this week
* I feel overwhelmed by the content presented this week
