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

<pre><code></code></pre>

3. What's the major difference between model backed and non-model backed form helpers?

<pre><code></code></pre>

4. How does `form_for` know how to build the `<form>` element?

<pre><code></code></pre>

5. What's the general pattern we use in the actions that handle submission of model-backed 
forms (ie, the `create` and `udpate` actions)?

<pre><code></code></pre>

6. How exactly do Rails validations get triggered? Where are the errors saved? How do we show the validation messages on the user interface?

<pre><code></code></pre>

7. What are Rails helpers?

<pre><code></code></pre>

8. What are Rails partials?

<pre><code></code></pre>

9. When do we use partials vs helpers?

<pre><code></code></pre>

10. When do we use non-model backed forms?

<pre><code></code></pre>