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
  <head>
    <title>meteor-crud</title>
  </head>
  <body>
    {{"{{> navbar"}}}}
    <div class="col-md-6 col-md-offset-3">
      {{"{{> postForm"}}}}
      {{"{{> posts"}}}}
    </div>
  </body>
{% endhighlight %}

we have created three template here

* *navbar* -  to hold navbar,
* *postForm* - a simple form to enter our post content
* *posts* - to show the all posts

now we can fill these templates with the required html contents

{% highlight html %}
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
{% endhighlight %}

the above code is simple navigation bar code from bootstrap so there is nothing complex to explain.

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
</template>
{% endhighlight %}


  {% highlight html %}
  <head>
    <title>meteor-crud</title>
  </head>
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

  <template name="postForm">
    <div class="form-group">
      <label class="control-label">Create post</label>
      <div class="input-group">
        <input type="text" id="content" class="form-control">
        <span class="input-group-btn">
          <button class="btn btn-success" type="button">Create</button>
        </span>
      </div>
  </template>

  <template name="posts">
    {{"{{#each post"}}}}
      {{"{{> post"}}}}
      {{"{{/each"}}}}
  </template>

  <template name="post">
    <li>
      {{"{{#if editing"}}}}
        <input type="text"  value="{{content}}" />
      {{"{{else"}}}}
        <p class="content" id = "up">{{content}}</p> 
        <button class="btn btn-sm btn-danger" id = 'delete' type="submit">Delete</button>
      {{"{{/if"}}}}
      </li>
  </template>
{% endhighlight%}

