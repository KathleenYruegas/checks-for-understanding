## Week Two - Module 2 Recap

Fork or re-pull this respository. Answer the questions to the best of your ability. Try to answer them with limited amount of external research. These questions cover the majority of what we've learned this week (which is a TON - YOU are a web developer!!!). 

Note: When you're done, submit a PR.


### Week 2 Questions

1. At a high level, what is ActiveRecord? What does it do/allow you to do?

AR is an ORM (Object Relational Mapper) which allows us to talk to the database without using raw SQL.  It wraps the 
SQL in Ruby objects so we can easily interact with the database. It also allows us to switch out the database
without having to change all of our code.

2. Assume you have the following model:

```ruby
class Team << ActiveRecord::Base
end
```

What are some methods you can call on `Team`? If these methods aren't defined in the class, how do you have access to them?

Team.new, Team.create, Team.destroy, Team.all, Team.count 
We can call these because our class Team is inheriting from ActiveRecord::Base which gives us access to all of these AR methods.

3. Assume that in your database, a team has the following attributes: "id", "name", owner_id". How would you find the name of a team with an id of 4? Assuming your class only included the code from question 2, how could you find the owner of the same team?

team = Team.find(4) would allow you to find the team with id of 4. 
team.owner_id would give you the id of the owner of that team, that would be all you could get for now, unless you did a .joins with 
Team and Owner.

4. Assume that you added a line to your `Team` class as follows:

```ruby
class Team << ActiveRecord::Base
  belongs_to :owner
end
```

Now how would you find the owner of the team with an id of 4?

Assuming the Owner class has a :name attribute, you could say:
team = Team.find(4)
team.owner.name 

And this should spit out the name of the owner for that specific team.

5. In a database that's holding students and teachers, what will be the relationship between students and teachers? Draw the schema diagram.

This would be a one to many relationship. A teacher has many students, and a student has one teacher.  
Schema:
teachers
  t.text :name 

students
  t.text :name
  t.integer :teacher_id


6. Define foreign key, primary key, and schema.

A foreign key is a column of id's in one table that is the primary key for the table of the same name as 
that column, for example, the "teacher_id" column in the students table is a foreign key since it is the same as the "id"
from the teachers table.
A primary key is the column of ids in that table. So in the teacher's table, their "id" column is the primary key.
A schema shows you how your database looks at that point in time. It shows you the tables and all of their columns.

7. Describe the relationship between a foreign key on one table and a primary key on another table.

This is how these tables are connected in a relationship.  If a table contains a foreign key, then we know that
table has a one-to-many relationship with the table whose primary key the foreign key came from.  So we know the students
belong to a teacher because the teacher_id (foreign key) is in the students table.  The teacher table does not have the student_id, 
that table only has it's own primary key, so we know the teachers have many students.

8. What are the parts of an HTTP response?

There are 3 parts.  The first part gives the status code and message (like 200, OK; or 404, Not Found; or 303, redirected). 
The second part of the response is the header which contains a set of key/value pairs to tell the browser what to do with the 
response, how to process it.
The third part is the body which will contain the actual resource (HTML, image, etc.).


### Optional Questions

1. Name your five favorite ActiveRecord methods (i.e. methods your models inherit from ActiveRecord) and describe what they do.

2. Name your three favorite ActiveRecord rake tasks and describe what they do.
`rake db:reset` is a good one, it does a `rake db:{drop,create,migrate,seed}` all in one command!

3. What two columns does `t.timestamps null: false` create in our database?
I believe you only need `t.timestamps` now, but this command creates 'created_at' and 'updated_at' columns in our database.

4. In a database that's holding schools and teachers, what will be the relationship between schools and teachers?
One to many. (Typically), a teacher will belong to ONE school, and a school will have MANY teachers.

5. In the same database, what will you need to do to create this relationship (draw a schema diagram)?
You would need to make sure you have the school_id as a foreign key in the teachers table.
teachers
  t.text :name 
  t.integer :school_id

schools
  t.text :name

6. Give an example of when you might want to store information besides ids on a join table.
If your joins table joined pets and owners, then you might want the joins table to also store 'created_at' so you
could access the date of adoption for that pet.

7. Describe and diagram the relationship between patients and doctors.
This would probably be a many to many. A patient has many doctors and a doctor has many patients.  You could join 
them in a joins table named DoctorPatients and this table would contain 2 foreign keys, the patient_id and the 
doctor_id.  I could see this being used for an Insurance company!

8. Describe and diagram the relationship between museums and original_paintings.


9. What could you see in your code that would make you think you might want to create a partial?
If you have a form to create a new thing and a form to edit a thing and all the fields are the same,
then you would want to use a partial to DRY up your code. 

### Self Assessment:
Choose One:
* I was able to answer every question without relying on outside resources

Choose One: BOTH!
* I feel comfortable with the content presented this week
* I feel overwhelmed by the content presented this week
