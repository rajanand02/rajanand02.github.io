---
layout: post
title: "Watch out for Meteor...!"
category: articles
tags: [meteor]
image:
feature: meteor.png 
comments: true
share: true
---

Few months back I read a blog post ["Why meteor will kill Ruby On Rail"](http://differential.io/blog/meteor-killin-rails){:target="_blank"}  by [Josh Owens](https://plus.google.com/102580086338708965582/posts){:target="_blank"} i was so curious after reading the post..It was the time i started working on production level Rails applications..i decided to give a try and created a simple [twitter follow application](http://twitter-login.meteor.com/){:target="_blank"} within few minitues by following [Sacha Greif's](http://www.smashingmagazine.com/2013/06/13/build-app-45-minutes-meteor/){:target="_blank"} tutorial..Meteor is no way near Rails but still it has some killer features like full stack reactivity, latency compensation etc.. which would take at-least a couple of years to bring in rails core..If you are Rails guy meteor might not seem very powerful but for a javaScript dev meteor is a real gift..

### Meteor
Meteor is a complete web stack built on top of Node.js for building real time web applications..The major advantage of Meteor is One language(javaScript) everywhere(both server/client)..It sits between app's database and its client and make sure that both are kept in sync...

### Why Meteor....?!

* Meteor is easy to learn...:D
* Meteor make it possible to create MVP(Minimum Viable Product) up and running in matter of hours..
* No need to learn a new language if you have some prior experience with javascript..
* It follow Model View View-Modal pattern(not exactly)..

### History of Web applications..

Before we jump into nuts and bolts of meteor it is important to know how web applications evolved..

#### Client/Sever model..

In Client/Server model the server performs almost all the operations on data and clients were used only to display the result from the servers..

<figure>
   <a href= "http://github.com/rajanand02">
    <img src="/images/client-server.png">
   </a>
<figcaption><a href="http://github.com/rajanand02" title="client/server model"></a>client/server model.</figcaption>
</figure>

#### MVC(Model View Controller)
If your familiar with frame works like Rails or Django you probably know MVC pattern..In MVC

* Model Contains all the data 
  * Controller talks with model, perform the logic/actions and prepare the data to be displayed and finally 
* View display the content and report back to the controller when something happens on the screen(button click, form submission etc..)

<figure>
   <a href= "http://github.com/rajanand02">
    <img src="/images/mvc.png">
   </a>
  <figcaption><a href="http://github.com/rajanand02" title="client/server model"></a>MVC pattern.</figcaption>
</figure>

#### MVVM



<figure>
  <a href= "http://github.com/rajanand02">
    <img src="/images/mvvm.png">
   </a>
<figcaption><a href="http://github.com/rajanand02" title="client/server model"></a>MVC pattern.</figcaption>
