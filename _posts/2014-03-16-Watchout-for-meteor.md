---
layout: post
title: "Watch out for Meteor...!"
category: articles
tags: [meteor, meteor tutorial, meteor introduction]
description: "Meteor detailed introduction with mvvm architecture and creating first meteor app"
image:
  feature:  meteor1.png 
comments: true
share: true
---


### Meteor
Meteor is a complete web stack built on top of Node.js for building real time web applications..It sits between app's database and its client and make sure that both are kept in sync..

### Why Meteor....?!

* Meteor is easy to learn...:D
* It is an  <a href="http://isomorphic.net/javascript" target="_blank"> isomorphic Javascript</a> platform.
* Meteor make it possible to create MVP(Minimum Viable Product) up and running in matter of hours..
* No need to learn a new language if you have some prior experience with JavaScript..
* It follow Model View View-Modal pattern(not exactly)..

### History of Web applications..

Before we jump into the nuts and bolts of meteor it is important to know how web applications evolved..

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

* Model - Handles all the data. 
* Controller - talks with model, perform the logic/actions and prepare the data to be displayed.
* View - display the content and report back to the controller when something happens on the screen(button click, form submission etc..)

<figure>
   <a href= "http://rajanand02.github.io/images/mvc.png">
    <img src="/images/mvc.png">
   </a>
  <figcaption><a href="http://github.com/rajanand02" title="client/server model"></a>MVC pattern.</figcaption>
</figure>

#### MVVM in Meteor
  As the browser technologies improved drastically developers started to enhance the concept of MVC to bring in MVVM pattern(Nested mvc)..In MVVM the sever side controller performs the business logic/operations on the database(server-model) and then send the result set(server-view) to the client..
  
  The client which receives the result set(server-view) consider it as its own model(client-model) and performs the logic required to present the content and finally view is used to display the information on the screen..

<figure>
  <a href= "http://rajanand02.github.io/images/mvvm.png" target="_blank">
    <img src="/images/mvvm.png">
   </a>
<figcaption><a href="http://github.com/rajanand02" title="client/server model"></a>
 Meteor does not strictly follow any pattern but based on the way it works <a href= "http://www.packtpub.com/authors/profiles/isaac-strack" target="_blank">Issac Strack</a> suggesting MVVM model in his book <a href="http://www.packtpub.com/getting-started-with-meteor-javascript-framework/book" target="_blank">Getting started with Meteor.js JavaScript Framework</a></figcaption>
</figure>


### Seven Principles of Meteor
In the Meteor official <a href="http://docs.meteor.com/">documention</a> you could find the following <a href="http://docs.meteor.com/#sevenprinciples">7 principles</a>

##### 1.Data on the wire
The only thing that traverse between the server and client after the initial page load is **data**.. Meteor loads all the html,css and other static assets in the initial page load after which it sends only the data to the client and let the client decide how to render the data.

##### 2.One Language
Meteor uses only <strong>JavaScript</strong> for both client and server side operations..This can be achieved in meteor because it is built on top of NodeJs and it uses MongoDB as default database...

##### 3.Datebase Everywhere
As default Meteor allows you to access the entire database from your client..You might think that it will lead to some serious security issues where any user can delete or modify other uses's details but this is just a default state while creating your application so that you can get the app up and ready in matter of minutes after which you can restrict the access to the database..Accessing the database from client side is achieved by using <a href="http://docs.meteor.com/#dataandsecurity"><strong>minimongo</strong></a>(Meteor's client-side Mongo emulator).

##### 4.Latency Compensation
Since database is available at client side whenever the user  do any activity(button click,form submission etc..) the result will be updated immediately in UI even before it receives confirmation from the server, this makes your application instantaneous and more responsive..However if the user is not permitted to do certain operations the changes will revert back after it gets confirmation form the server(just fraction of seconds later)..

##### 5.Full Stack Reactivity
In meteor all the layers form database to html templates everything is <strong>event-driven</strong> i.e the application will respond based on the activities of the user..

##### 6.Embrace the Ecosystem
Meteor uses other open sources libraries like MongoDB, Handlebars etc instead of making their own, this is because when those libraries improve Meteor will also get improve and moreover the developers would get more community help when they are building applications or learning Meteor..

##### 7. Simplicity Equals Productivity
The key idea of improving the productivity is having a clean and simple API, Meteor core highly follow this principle by providing much simple and beautiful APIs to build the application..

### Getting Started
Its quite a lot of text...:D Lets get started by installing Meteor..                

##### Installation
Installing meteor can't be more easier..Simply coping the below code and pasting it in your terminal will make your operating system ready for meteor development..

{% highlight bash%}
curl https://install.meteor.com | /bin/sh

# Check meteor version
meteor --version
Realease 0.7.1.2
{% endhighlight%}

Meteor 0.7.1.2 is the current stable version and it supports GNU/Linux and Unix by default, for windows you can check the unofficial version here <a href="http://win.meteor.com/" target="_blank">win.meteor.com</a>

#####Create a project

{% highlight bash%}
  meteor create app_name
{% endhighlight%}

<figure>
  <img src="/images/mrt.gif">
  <figcaption>
    <a href="rajanand02.github.io/images/mrt.gif" title="">creating meteor application.</a>
  </figcaption>
</figure>

Meteor allows you create 4 pre-build examples where you can play around and understand its basic working principles...

{% highlight ruby%}
  # to check available examples
  meteor create --list

  # create an example application
  meteor create --example todos
{% endhighlight%}

<figure>
  <img src ="/images/leader.gif">
  <figcaption>
    To checkout other examples vist 
    <a href="https://www.meteor.com/examples" title=""> <strong>here.</strong></a>
  </figcaption>
</figure>


#### Meteorite
<a href="https://github.com/oortcloud/meteorite">Meteorite</a> is a Meteor Version Manager which is similar to RVM/Rbenv available for maintaining ruby versions for individual projects..      
Using Meteorite we can easily maintain multiple versions of Meteor, install non-core and third party packages from <a href="http://beta.atmospherejs.com/" target="_blank"> <strong>Atmosphere</strong></a>


##### Installing Meteorite
Meteorite installation is also similar to Meteor installation in which a single command is enough to do the magic..

{% highlight bash%}
sudo -H npm install -g meteorite
{% endhighlight%}

Once Meteorite is installed we can use `mrt` command to create projects as well as to install packages..it will act like an alias to `meteor` command..

<figure>
  <img src ="/images/mrtinstall.gif">
  <figcaption>
    <a href="rajanand02.github.io/images/mrtinstall.gif" title="">meteorite.</a>
  </figcaption>
</figure>

##### Packages
Packages in Meteor is something similar to ruby gems or node packages..Adding packages to the application can be done by `meteor add package_name` command or `mrt add package_name` command if it is a third party package from Atmosphere..Installing packages can also be done manually by including it in smart.json  file and running `mrt` inside the application directory..This will create a `/packages` directory and includes all the required dependencies and files of the packages..

##### Types of packages
*  *Core Packages* - Meteor itself is a combination of various packages and those packages are called core packages..These core packages are included in every meteor applications..

*  *Smart Packages*- Smart packages are about 42 packages created by meteor team that comes bundled with meteor..You can view these packages by `meteor list` command..

* *Atmosphere Smart Packages*- These are third party packages from <a href="http://beta.atmospherejs.com/">Atmosphere</a> which are built by Meteor community..

* *Local Packages*- Local packages are custom packages for the application that can be included by putting inside `/packages` directory..

* *NPM Packages*- Node.js packages can also be integrated in the application by using above packages..

Lets include some packages to our leaderboard application..

<figure>
  <img src ="/images/packages.gif">
  <figcaption>
    <a href="rajanand02.github.io/images/packages.gif">adding packages.</a>
  </figcaption>
</figure>

##### Deploying Meteor
Meteor gives you free server space to deploy and check your application, you don't have to spend time in setting  up your server or configure heroku..This could be very useful while you are prototyping your application or creating MVP to get confirmation form clients...

{% highlight bash%}
  meteor deploy app_name.meteor.com
{% endhighlight%}

<figure>
  <img src ="/images/deploy.gif">
  <figcaption>
    <a href="rajanand02.github.io/images/deploy.gif">deploying in meteor server.</a>
  </figcaption>
</figure>

You can also deploy the application in your own server by bundling the app and run it as a simple node application...

{% highlight ruby%}
  meteor bundle app_name.tar.gz
{% endhighlight%}

<figure>
  <img src ="/images/bundle.gif">
  <figcaption>
    <a href="http://rajanand02.github.io/images/bundle.gif" title="">bundling the application.</a>
  </figcaption>
</figure>

##### Resources
* <a href="http://yauh.de/articles/376/best-learning-resources-for-meteorjs">yet another useless homepage</a> by<a href="https://plus.google.com/+StephanHochhaus" target="_blank"> <strong>Stephan Hochhaus</strong></a> 
