# Week 2 Quiz
1. Name all the 7 (or 8) routes exposed by the `resources` keyword in the `routes.rb` file. 
Also name the 4 named routes, and how the request is routed to the controller/action.

'resources' routes
-------------

<table>
  <tr>
    <th>name</th><th>verb/method</th><th>url</th><th>Controller#Action</th>
  </tr>
  <tr>
    <td>posts_path</td><td>GET</td><td>/posts</td><td>posts#index</td>
  </tr>
  <tr>
    <td></td><td>POST</td><td>/posts</td><td>posts#create</td>
  </tr>
  <tr>
    <td>new_post_path</td><td>GET</td><td>/posts/new</td><td>posts#new</td>
  </tr>
  <tr>
    <td>edit_post_path</td><td>GET</td><td>/posts/id/edit</td><td>posts#edit</td>
  </tr>
  <tr>
    <td>post_path</td><td>GET</td><td>/posts/id</td><td>posts#show</td>
  </tr>
  <tr>
    <td></td><td>PATCH</td><td>/posts/id</td><td>posts#update</td>
  </tr>
  <tr>
    <td></td><td>PUT</td><td>/posts/id</td><td>posts#update</td>
  </tr>
  <tr>
    <td></td><td>DELETE</td><td>/posts/id</td><td>posts#destroy</td>
  </tr>
</table>

2. What is REST and how does it relate to the `resources` routes?

<pre><code>REST stands for REpresentational State Transfer and is a stateless 
architecture that runs over HTTP using a client-server. There is a limited 
number of methods/verbs and flexibility is provided by assigning resources/nouns
 their own unique urls. Because each verb has a specific meaning (GET, POST, 
 PUT and DELETE), REST avoids ambiguity.</code></pre>

3. What's the major difference between model backed and non-model backed form helpers?

<pre><code>Model backed form helpers automatically detect the status of the 
active record object. Upon submitting a form it knows whether to do a create
or update on that object. Model backed form helpers also display any current 
values in the form automatically. Errors are also handled and addedd to html 
elements that can be used to display those errors to the user. 
Non-model backed form helpers only create the html.</code></pre>

4. How does `form_for` know how to build the `<form>` element?

<pre><code>It uses a variable passed into the form_for, usually a instance 
variable created at the controller (ex: @post).  It also has active record 
awareness to see if the variable being passed in has values in the db. If so 
a patch/put is submitted rather than a post.</code></pre>

5. What's the general pattern we use in the actions that handle submission of model-backed 
forms (ie, the `create` and `udpate` actions)?

<pre><code>@post = Post.find(params[:id])
if @post.save
  flash[:notice] = "Your post was created"
  redirect_to posts_path
else
  render :new</code></pre>

6. How exactly do Rails validations get triggered? Where are the errors saved? How do we show the validation messages on the user interface?

<pre><code>Rails validations are define in the model (ex post.rb). They are 
triggered upon creation of a new database entry or update of an exising database
entry. The model backed form helpers created html elements that are used to 
display the errors to the user. The errors are stored in the active record 
model. We use errors.full_messages to loop through them.</code></pre>

7. What are Rails helpers?

<pre><code>Rails helpers are used to extract repititous code. They are also used
to format/modify information after it has been extracted from the database since
 we do not want to modify the database information directly. </code></pre>

8. What are Rails partials?

<pre><code>Partials are common html elements that are shared between views.</code></pre>

9. When do we use partials vs helpers?

<pre><code>Partials are used when the repeated code is html that appears across
 multiple views. Helpers are used when it is non-html code repeated in multiple
  areas of our codebase, and/or we want to modify/format returned database 
  information.</code></pre>

10. When do we use non-model backed forms?

<pre><code>If we are not using instance variables (active record objects).</code></pre>