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
If you are familiar with frame works like Rails or Django you probably know MVC pattern..In MVC

* Model - Contains all the data. 
* Controller - talks with model, perform the logic/actions and prepare the data to be displayed.
* View - display the content and report back to the controller when something happens on the screen(button click, form submission etc..)

<figure>
   <a href= "http://github.com/rajanand02">
    <img src="/images/mvc.png">
   </a>
  <figcaption><a href="http://github.com/rajanand02" title="client/server model"></a>MVC pattern.</figcaption>
</figure>

#### MVVM in Meteor
  As the browser technologies improved drastically developers started to enhance the concept of MVC to bring in MVVM pattern(Nested mvc)..In MVVM the sever side controller performs the business logic/operations on the database(model) and then send the result set(view) to the client..The client which receives the result set(server-view) consider it as its own model and performs the logic required to present the content and finally view is used to display the information on the screen..

<figure>
  <a href= "http://github.com/rajanand02" target="_blank">
    <img src="/images/mvvm.png">
   </a>
<figcaption><a href="http://github.com/rajanand02" title="client/server model"></a>
 Meteor does not strictly follow any pattern but based on the way it works <a href= "http://www.packtpub.com/authors/profiles/isaac-strack" target="_blank">Issac Strack</a> suggesting MVVM model in his book <a href="http://www.packtpub.com/getting-started-with-meteor-javascript-framework/book" target="_blank">Getting started with Meteor.js JavaScript Framework</a></figcaption>
</figure>


### Seven Principles of Meteor
In the Meteor official <a href="http://docs.meteor.com/">documention</a> they have listed out the following <a href="http://docs.meteor.com/#sevenprinciples">7 principles</a>

##### 1.Data on the wire
The only thing that traverse between the server and client after the initial page load in **data**.. Meteor loads all the html,css and other static assets in the initial page load after that it sends only the data to the client and let the client decide how to render the data.

##### 2.One Language
Meteor uses only JavaScript for both client and server side operations..This can be achieved in meteor because it is built on top of NodeJs and it uses MongoDB as default database...

##### 3.Datebase Everywhere
As default Meteor allows you to access the entire database from your client..You might think that it will lead to some serious security issues where any user can delete or modify other uses's details but this is just a default state while creating your application so that you can get the app up and ready in matter of minutes after which you can restrict the access to the database..Accessing the database from client side is achieved by using minimongo(Meteor's client-side Mongo emulator).

##### 4.Latency Compensation
Since database is available at client side whenever the user  do any activity(button click,form submission etc..) the result will be updated immediately in UI even before it receives confirmation from the server, this makes your application instantaneous and more responsive..However if the user is not permitted to do certain operations the changes will revert back after it gets confirmation form the server(just fraction of seconds later)..

##### 5.Full Stack Reactivity
In meteor all the layers form database to html templates everything is even-driven i.e the application will respond based on the activities of the user..

##### 6.Embrace the Ecosystem
Meteor uses other open sources libraries like MongoDB, Handlebars etc instead of making their own, this is because when those libraries improve Meteor will also get improve and moreover the developers would get more community help when they are building applications or learning Meteor..

##### 7. Simplicity Equals Productivity
The key idea of improving the productivity is having a clean and simple API, Meteor core highly follow this principle by providing those kind of simple and beautiful APIs to build the web application..

