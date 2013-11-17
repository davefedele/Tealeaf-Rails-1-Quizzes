# Week 3 Quiz
1. What's the difference between rendering and redirecting? What's the impact with regards to instance variables, view templates?

Rendering is displaying the current controller#action's view template. If we want
 instance variables they must be declared in the controller#action.
Redirecting is routing the user to another url.

Instance variables are lost when redirecting, but are kept when rendering a view template.

2. If I need to display a message on the view template, and I'm redirecting, what's the easiest way to accomplish this?

flash

3. If I need to display a message on the view template, and I'm rendering, what's the easiest way to accomplish this?

flash.now

4. Explain how we should save passwords to the database.

We implement has_secure_password in the user model. When the user inputs their
password, rails has built in helpers to create a hash of the password and save
it to our password digest. When the user tries to login, we run the authenticate
 helper that compares a hash of their submitted password against the hash in the
 database password digest. If they match, the user is authenticated.

5. What should we do if we have a method that is used in both controllers and views?

We should add it to the Application Controller as a helper method.

6. What is memoization? How is it a performance optimization?

It is a way of retrieving database information once and saving it for further 
access in the current request. That way we reduce the number of calls/read on
the database. 

7. If we want to prevent unauthenticated users from creating a new comment on a post, what should we do?

Setup a session to authenticate users througout our program and reidrect if they 
 are unauthenticated. Also, hid the ui items for unauthenticated users.

8. Suppose we have the following table for tracking "likes" in our application. How can we make this table polymorphic? Note that the "user_id" foreign key is tracking who created the like.

    | id  | user_id | photo_id | video_id | post_id |
    |:---:|:-------:|:--------:|:--------:|:-------:|
    | 1   | 4       |          | 12       |         |
    | 2   | 7       |          |          | 3       |
    | 3   | 2       | 6        |          |         |


Answer:

    | id  | user_id | likeable_type | likeable_id | 
    |:---:|:-------:|:-------------:|:-----------:|
    | 1   | 4       |     video     |     12      |
    | 2   | 7       |     post      |     3       |
    | 3   | 2       |     photo     |     6       |


9. How do we set up polymorphic associations at the model layer? Give example for the polymorphic model (eg, Vote) as well as an example parent model (the model on the 1 side, eg, Post).

<pre><code>
class Vote < ActiveRecord::Base
  belongs_to  :creator, class_name: 'User', foreign_key: 'user_id'
  belongs_to  :voteable, polymorphic: true

  validates_uniqueness_of :creator, scope: :voteable
end</code></pre>

<pre><code>class Post < ActiveRecord::Base
  belongs_to  :creator, foreign_key: 'user_id', class_name: 'User'
  has_many    :votes, as: :voteable
end</code/></pre>

<pre><code>class User < ActiveRecord::Base
  has_many  :posts
  has_many  :votes
end</code></pre>

10. What is an ERD diagram, and why do we need it?

It is a diagram that gives a visual representation of our application models 
(posts, comments, users, etc.). It helps us figure out our schema to properly 
setup the database as well as to figure out the necessary relationships between 
our data.