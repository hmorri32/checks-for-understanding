## Week Two - Module 2 Recap

Fork this respository. Answer the questions to the best of your ability. Try to answer them with limited amount of external research. These questions cover the majority of what we've learned this week (which is a TON - YOU are a web developer!!!).

Note: When you're done, submit a PR.

1. At a high level, what is ActiveRecord? What does it do/allow you to do?
Active record is an ORM and it allows us to interact with a database by using it's built in methods. It acts like a translator between sql and ruby.
2. Assume you have the following model:

```ruby
class Team << ActiveRecord::Base
end
```
Team.all, .average, .find, .group, .join, .select, .where, .count. These arent definied in our class but as we inherit from ActiveRecord::Base, we have the methods set forth in that module.

3. Assume that in your database, a team has the following attributes: "id", "name", owner_id". How would you find the name of a team with an id of 4? Assuming your class only included the code from question 2, how could you find the owner of the same team?

`find(id).name`

`Owner.find(Team.find(id))`

4. Assume that you added a line to your `Team` class as follows:

```ruby
class Team << ActiveRecord::Base
  belongs_to :owner
end
```

Now how would you find the owner of the team with an id of 4?

`team = Team.find(4) team.owner`

5. In a database that's holding students and teachers, what will be the relationship between students and teachers? Draw the schema diagram.
A student has many teachers and a teacher has many students.
This is known as a many to many relationship. We would have to specify a joins table to accurately model this relationship. Maybe with a teacher_students table?
6. Define foreign key, primary key, and schema.
A foreign key is how we can access another tables primary key. It acts as the link between two tables. A primary key is a resources primary identifier, usually an ID. A schema is the current 'blueprint' for the database. it defines the tables and the rows and columns inside those tables as well as the relationships between said tables.

7. Describe the relationship between a foreign key on one table and a primary key on another table.
A foreign key on one table is the primary key on a seperate table.
8. What are the parts of an HTTP response?
status, headers, body

### Optional Questions

1. Name your five favorite ActiveRecord methods (i.e. methods your models inherit from ActiveRecord) and describe what they do.

`find_or_create` is a wonderful method that cancels out the need to do an if else blah blah blah when creating a new resource.
Want an array of column values for certain records? => => `pluck`


2. Name your three favorite ActiveRecord rake tasks and describe what they do.

`rake db:drop db:create db:migrate` "I messed everything up horribly. please help"

3. What two columns does `t.timestamps null: false` create in our database?

two timestamps => created at and updated at.

4. In a database that's holding schools and teachers, what will be the relationship between schools and teachers?

A school has many teachers and a teacher belongs to a school

5. In the same database, what will you need to do to create this relationship (draw a schema diagram)?

School  => has_many   :teachers

Teacher => belongs_to :school

6. Give an example of when you might want to store information besides ids on a join table.

We joined on date for bike share. That was interesting.

7. Describe and diagram the relationship between patients and doctors.

patients have many doctors doctors have many patients.

We'd need to create a `patient_doctors` or `doctor_patients` joins table. this all seems pretty silly to me at the moment. definitely need to brush up on this concept. then we would specify that a patient has_many doctors through that specified joins table and that a doctor has many patients through that same table.

8. Describe and diagram the relationship between museums and original_paintings.

A musem has many original paintings and an original painting belongs to one museum. => painting`belongs_to :museum` museum `has_many :paintings`
9. What could you see in your code that would make you think you might want to create a partial?
a repeated form or reused view. Can be made a partial and render said partial instead of repeating the html over and over again.
