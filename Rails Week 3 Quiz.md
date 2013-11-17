# Week 3 Quiz
1. What's the difference between rendering and redirecting? What's the impact with regards to instance variables, view templates?

2. If I need to display a message on the view template, and I'm redirecting, what's the easiest way to accomplish this?
3. If I need to display a message on the view template, and I'm rendering, what's the easiest way to accomplish this?
4. Explain how we should save passwords to the database.
5. What should we do if we have a method that is used in both controllers and views?
6. What is memoization? How is it a performance optimization?
7. If we want to prevent unauthenticated users from creating a new comment on a post, what should we do?
8. Suppose we have the following table for tracking "likes" in our application. How can we make this table polymorphic? Note that the "user_id" foreign key is tracking who created the like.

    | id  | user_id | photo_id | video_id | post_id |
    |:---:|:-------:|:--------:|:--------:|:-------:|
    | 1   | 4       |          | 12       |         |
    | 2   | 7       |          |          | 3       |
    | 3   | 2       | 6        |          |         |

9. How do we set up polymorphic associations at the model layer? Give example for the polymorphic model (eg, Vote) as well as an example parent model (the model on the 1 side, eg, Post).
10. What is an ERD diagram, and why do we need it?
