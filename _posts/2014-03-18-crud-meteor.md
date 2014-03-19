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


