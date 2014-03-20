---
layout: post
title: "Simple Crud app in Meteor"
category: articles
tags: [meteor]
image: 
  feature: meteor.png
comments: true
share: true
---

We have seen some introduction about Meteor in the previous article now lets create a simple crud application, put the code in GitHub and deploy the app in meteor server.

#### Create

` mrt create meteor-crud `

Lets remove the default content..

<figure>
    <img src ="/images/create.gif">
</figure>

we are going to use <a href="http://beta.atmospherejs.com/package/bootstrap-flatly" target="_blank"> <strong>bootstrap-flatly</strong></a> theme for ui design and CoffeeScript as template manager..

<figure>
  <img src ="/images/coffee-bootstrap.gif">
</figure>

First we can prepare our html file to render our posts then we can use our template manager to make the content reactive..


{% highlight html %}
  # posts.html
  <head>
    <title>meteor-crud</title>
  </head>
  <body>
    <div class="col-md-6 col-md-offset-3">
      {{"{{> postForm"}}}}
      {{"{{> posts"}}}}
    </div>
  </body>
{% endhighlight %}

we have created two <a href="http://handlebarsjs.com/" target="_blank">handlebar templates</a> here, one to hold the form to enter the post and another one to show the posts.

now we can break these into individual templates and start filling it with required html contents.


#### postForm Template
{% highlight html %}
<template name="postForm">
  <div class="form-group">
     <label class="control-label">Create post</label>
     <div class="input-group">
        <input type="text" id="content" class="form-control">
        <span class="input-group-btn">
          <button class="btn btn-success" type="button">Create</button>
        </span>
     </div>
  </div>
</template>
{% endhighlight %}

here we have created one input box with id **content** and one button to submit the post..

#### posts Template
{% highlight html %}
<template name="posts">
  {{"{{#each post"}}}}
    {{"{{> post"}}}}
  {{"{{/each"}}}}
</template>
{% endhighlight %}

in posts template we have created a template helper **post** to iterate through each post and render the **post** template for individual posts..  

#### post Template
{% highlight html %}
<template name="post">
  {{"{{#if editing"}}}}
    <input type="text"  value="{{"{{content"}}}}" />
  {{"{{else"}}}}
    <p>
      <span class="content col-md-10" id="edit"  >{{"{{content"}}}} </span>
      <button class="btn btn-sm btn-danger" id="delete" type="submit">Delete</button>
    </p>
    {{"{{/if"}}}}
</template>
{% endhighlight %}
in post template we have created a simple state called **editing** where user is editing the content of the post..

if editing is set to true we are going to display an input box to change the content, otherwise a list of posts with a delete button.

Our final posts.html file would be like this.
{% highlight html %}

# posts.html
<head>
  <title>meteor-crud</title>
</head>
<body>
  <div class="col-md-6 col-md-offset-3">
    {{"{{> postForm"}}}}
    {{"{{> posts"}}}}
  </div>
</body>

<template name="postForm">
  <div class="form-group">
     <label class="control-label">Create post</label>
     <div class="input-group">
        <input type="text" id="content" class="form-control">
        <span class="input-group-btn">
          <button class="btn btn-success" type="button">Create</button>
        </span>
     </div>
  </div>
</template>

<template name="posts">
  {{"{{#each post"}}}}
    {{"{{> post"}}}}
  {{"{{/each"}}}}
</template>

<template name="post">
  {{"{{#if editing"}}}}
    <input type="text"  value="{{"{{content"}}}}" />
  {{"{{else"}}}}
    <p>
      <span class="content col-md-10" id="edit"  >{{"{{content"}}}} </span>
      <button class="btn btn-sm btn-danger" id="delete" type="submit">Delete</button>
    </p>
    {{"{{/if"}}}}
</template>
{% endhighlight%}
<small> check the code in <a href="https://github.com/rajanand02/meteor-crud/blob/master/posts.html" target="_blank">github</a></small>

now fire up the meteor server by `mrt` command inside your project root directory..
if you have done everything correctly you should see something similar to this in your browser

<figure>
  <img src ="/images/posts_page.png">
</figure>

Lets add a bootstrap navigation bar before our *postForm* template to make the app more elegant..

##### navbar

{% highlight html %}
#post.html
...
...
<body>
  {{"{{> navbar"}}}}
  <div class="col-md-6 col-md-offset-3">
    {{"{{> postForm"}}}}
    {{"{{> posts"}}}}
  </div>
</body>
<template name="navbar">
  <div class="navbar navbar-inverse">
    <div class="navbar-header">
      <button type="button" class="navbar-toggle" data-toggle="collapse" data-target=".navbar-inverse-collapse">
        <span class="icon-bar"></span>
        <span class="icon-bar"></span>
        <span class="icon-bar"></span>
      </button>
      <a class="navbar-brand" href="#">Meteor Crud</a>
    </div>
  </div>
</template>
...
...
{% endhighlight %}

now our posts.html file should be like this..

<figure>
  <a href="">
    <img src ="/images/posts_page2.png">
  </a>
</figure>

Its time to make our static html template reactive using our posts.coffee template manager ..

First lets create a MongoDB collection to hold the posts in the database..
{% highlight ruby %}
Post = new Meteor.Collection "post"

if Meteor.isClient
  ...
  ...
{% endhighlight%}

we just created a MongoDB collection called **post** using the *Meteor.Collection* method..Note that this line of code should be outside our `if Meteor.isClient` block because this collection should be available at both client and server..

#### Create

{% highlight ruby%}
  Template.postForm.events 
    "click button": (e, t) ->
      data = t.find "#content"
      Post.insert content: data.value
      data.value = ""
{% endhighlight%}

we are creating a events method for postForm template and a small click function on the button object..

Whenever the button is clicked we are going find the element with id **"content"** and store its value inside the variable called **data** and then we are inserting the **data** into our **posts** collection using `Post.insert` MongoDB command and finally we changing the value of **data** to null to get the next item..

Now we can able to create posts..
<figure>
  <img src ="/images/mongo.gif">
</figure>

The posts doesn't show up yet in our page but we could see the post inside the mongo console by running `meteor mongo` inside your project directory..

<small>Note: your meteor server should be running while opening mongo console</small>

Now lets make the post available in our page..

#### Read
{% highlight ruby%}
  Template.posts.post = ->
    Post.find()
{% endhighlight%}

We are creating a template helper called **post** that will return the data from `Post.find()`..This **post** helpers is used inside the **posts** template to iterate through each posts..

{% highlight html %}
<template name="posts">
  {{"{{#each post"}}}}
    {{"{{> post"}}}}
  {{"{{/each"}}}}
</template>
{% endhighlight %}

If we switch to the browser we could see all the posts
<figure>
  <img src ="/images/allposts.png">
</figure>

We have completed half of the application now lets add delete function in our template manager..

#### Delete

{% highlight ruby%}
  Template.post.events
    "click #delete": (e, t) ->
      post = Post.findOne(t.data)
      Post.remove _id: post._id
{% endhighlight%}

Whenever the button with id **"delete"** is clicked we are finding the target element and storing it in **post** variable and then we are passing its id to remove the post from the collection using `Post.remove` 
`_id` is MongoDB unique id for each element in the collection..
<figure>
  <img src ="/images/delete.gif">
</figure>

#### Update

Update part is bit tricky 
{% highlight ruby%}
  Template.post.editing = ->
    Session.get "target" + @_id

  Template.post.events
    "click #edit": (e, t) ->
      Session.set "target" + t.data._id, true

    "keypress input": (e, t) ->
      if e.keyCode is 13
        post = Post.findOne(t.data)
        Post.update {_id: post._id}, { $set: content: e.currentTarget.value}
        Session.set "target" + t.data._id, false
{% endhighlight%}

We can split this into three sections

{% highlight ruby%}
  #1 setting the editing state
  Template.post.editing = ->
    Session.get "target" + @_id
{% endhighlight%}

Here we are getting the session variable with a key **target** and its value is mongodb **id** field..This will return either true or false based on the session value it gets..

{% highlight ruby%}
  #2 change span to input box
  Template.post.events
    "click #edit": (e, t) ->
      Session.set "target" + t.data._id, true
{% endhighlight%}
<figure>
  <img src ="/images/input-box.gif">
</figure>

In post template whenever the span with id **"edit"** is clicked we are setting the Session variable *true* thereby the **"editing"** helper is set to true..As per our html template when **editing** state is enabled, input box would appear instead of span..

{% highlight ruby%}
  #3 updating the post on hitting enter
  "keypress input": (e, t) ->
    if e.keyCode is 13
      post = Post.findOne(t.data)
      Post.update {_id: post._id}, { $set: content: e.currentTarget.value}
{% endhighlight%}

Here we are again finding the target element storing it in *post* variable and using its id and value to update the appropriate postwhenever enter key is pressed inside the input box..(<small> keycode for enter key is 13</small>)

MongoDB update query takes two argument 1. the *id* of the target element and 2. *value* to be updated..

MongoDB `$set` operator is used to update the collection..

This would be our final post.coffee template manager..
{% highlight ruby%}
  Post = new Meteor.Collection("post")
  if Meteor.isClient
    # create
    Template.postForm.events 
      "click button": (e, t) ->
        data = t.find "#content"
        Post.insert content: data.value
        data.value = ""
    
    # Read
    Template.posts.post = ->
      Post.find()

    # update
    Template.post.editing = ->
      Session.get "target" + @_id
    
    Template.post.events
      "click #edit": (e, t) ->
        Session.set "target" + t.data._id, true

      "keypress input": (e, t) ->
        if e.keyCode is 13
          post = Post.findOne(t.data)
          Post.update {_id: post._id}, { $set: content: e.currentTarget.value}
          Session.set "target" + t.data._id, false
    
      # delete
      "click #delete": (e, t) ->
        post = Post.findOne(t.data)
        Post.remove _id: post._id
{% endhighlight%}
<small> Check the code in <a href="https://github.com/rajanand02/meteor-crud/blob/master/posts.coffee">GitHub</a></small>

Since we are using CoffeeScript we don't have to write *return* statements and we can also ignore brackets/semicolons etc..

Now our code is pretty clean and it is ready to do **CRUD** operations..
<figure>
  <img src ="/images/crud-final.gif">
</figure>

Its time to deploy our app in remote server and see the code in action.. :D
{% highlight bash%}
  mrt deploy meteor-crud.meteor.com 
  Deploying to meteor-crud.meteor.com. Bundling...
  Uploading...
  Now serving at meteor-crud.meteor.com
{% endhighlight %}

<figure>
  <img src ="/images/crud-server.gif">
</figure>


