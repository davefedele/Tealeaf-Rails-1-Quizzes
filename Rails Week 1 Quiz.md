# Rails Week 1 Quiz
1. Why do they call it a relational database?

<pre><code>A relational database is based upon the relational model. It is a 
type of database that arranges data into tables and links them together based
on a defined relationship.</code></pre>

2. What is SQL?

<pre><code>SQL (Structure Query Language) is the standard language for accessing
 databases.</code></pre>

3. There are two predominant views into a relational database. What are they, 
and how are they different?

<pre><code>They are the schema view and that data view. The schem view displays
the table within the database and the attributes and their respective type. Data
view displays the actual information stored within those tables.</code></pre>
4. In a table, what do we call the column that serves as the main identifier 
for a row of data? We're looking for the general database term, not the column 
name.

<pre><code>It is called the primary key.</code></pre>

5. What is a foreign key, and how is it used?

<pre><code>It is used to set up an association between two tables. The foreign
 key is used to link to data in another table to maintain associations.</code></pre>

6. At a high level, describe the ActiveRecord pattern. This has nothing to do 
with Rails, but the actual pattern that ActiveRecord uses to perform its ORM 
duties.

<pre><code>ActiveRecord is an abstracted way to interact with data in a 
  database where each table is is wrapped in a class. Every line in a database
   table is treated as an object instance. These instance objects get also have
   accessor methods that are implemented through the class. </code></pre>

7. If there's an ActiveRecord model called "CrazyMonkey", what should the table 
name be?

<pre><code>"crazy_monkeys"</code></pre>

8. If I'm building a 1:M association between `Project` and `Issue`, what will 
the model associations and foreign key be?

<pre><code>class Project << ActiveRecord::Base
  has_many  :issues
end</code></pre>

<pre><code>
class Issue << ActiveRecord::Base
  belongs_to  :project
end
</code></pre>

<pre><code>
The foreign key will be: project_id
</code></pre>

9. Given this code

  <pre><code>class Zoo < ActiveRecord::Base
      has_many :animals
end</code></pre>

<pre><code>
    - What do you expect the other model to be and what does database schema look like?
    - What are the methods that are now available to a zoo to call related to animals?
    - How do I create an animal called "jumpster" in a zoo called "San Diego Zoo"?
</code></pre>

<pre><code>class Animal < ActiveRecord::Base
    belongs_to  :zoo
  end</pre></code>

<pre><code>
I expect the schema for zoo is id:integer type:string zoo_id:integer 
created_at:datetime updated_at:datetime

For Animal I expect just id:integer name:string created_at:datetime 
updated_at:datetime
</code></pre>

<code><pre>Zoo.first.animals.first.type</code></pre>

<pre><code>zoo = Zoo.create(name: 'San Diego Zoo')
  jumpster = Animal.create(type: 'jumpster')
  jumpster.zoo = zoo
  jumpster.save
  zoo.save</code></pre>

10. What is mass assignment? What's the non-mass assignment way of setting 
values?

<pre><code>Mass assignment is setting multiple values at once through the use
of a hash. 
Without mass assignment we set attributes one at a time using a string or value:
  attributes=(new_attributes)</code></pre>

11. What does this code do? `Animal.first`

<pre><code>It gets the first animal (id=1) from the animals table.</code></pre>

12. If I have a table called "animals" with columns called "name", and a model 
called `Animal`, how do I instantiate an animal object with name set to "Joe". 
Which methods makes sure it saves to the database?

<pre><code>joe = Animal.new(name: 'Joe')
  joe.save

  or

  joe = Animal.create(name: 'Joe')
</code></pre>

13. How does a M:M association work at the database level?

<pre><code>You create a join table that contains two foreign keys. These foreign 
  keys are the id's (primary keys) of the respective information you wish to 
  associate.
</code></pre>

14. What are the two ways to support a M:M association at the ActiveRecord model
 level? Pros and cons of each approach?

<pre><code>
has_and_belong_to_many => does not require a join table. Simpler to setup. 
Cannot add additional attributes.

has_many :through => you must create the join table. More complicated to setup
but more powerful. Can add as many attributes as you wish.
</code></pre>

15. Suppose we have a `User` model and a `Group` model, and we have a M:M 
association all set up. How do we associate the two?

<pre><code>class Connection < ActiveRecord::Base
    belongs_to  :user
    belongs_to  :group
  end
</code></pre>

<pre><code>class User < ActiveRecord::Base
    has_many  :connections 
    has_many  :users through: connection
  end
</code></pre>

<pre><code>class Group < ActiveRecord::Base
    has_many  :connections
    has_many,  :groups through: connection
  end
</code></pre>