---
layout: post
title:      "What to study for Project 2 Review"
date:       2020-11-08 09:18:43 -0500
permalink:  what_to_study_for_project_2_review
---


Sinatra is a Domain Specific Language implemented in Ruby
Any application that requires the sinatra library will get access to methods like: get and post. These methods provide the ability to instantly transform a Ruby application into an application that can respond to HTTP requests.

we define a class App and have it inherit from Sinatra::Base. This way, any instance of our class App will have all the functionality of the Sinatra class.
Inside our class we have a Sinatra method define our controller action. This method responds to a GET request to the root url and displays the text Hello, World! in the browser.

The purpose of config.ru is to detail to Rack the environment requirements of the application and start the application.
A common 'config.ru' might look like:
File: config.ru
require 'sinatra'
require_relative './app.rb'
run Application
config.ru requires a valid Sinatra Controller to run. A Sinatra Controller is simply a Ruby Class that inherits from Sinatra::Base

Controllers define an HTTP method using the sinatra routing DSL provided by methods like get and post. When you enclose these methods within a ruby class that is a Sinatra Controller, these HTTP routes are scoped and attached to the controller.

Routes are the part of an application that connect HTTP requests to a specific method in your application code built to handle responding to such a request (that part of code is called a Controller Action).

 a route is an HTTP method paired with a URL-matching pattern. Each route is associated with a block. The matching route defined in the controller would look like this:

get '/medicines' do
    # some code to get all the medicines
	 some code to get all the medicines
 end
-----
get '/medicines' do
  @medicines = Medicine.all
  erb :'medicines/index.html.erb'
end

**Models**: The 'logic' of a web application. This is where data is manipulated and/or saved.
Views: The 'front-end', user-facing part of a web application - this is the only part of the app that the user interacts with directly. Views generally consist of HTML, CSS, and Javascript.
Controllers: The go-between for models and views. The controller relays data from the browser to the application, and from the application to the browser.

 a single file, **layout**.erb, that contains all of the code we want to exist on every single web page.
 
 In layout.erb, we need to add a **yield** wherever we want the other page content to be loaded:
 
 In web apps, we use **forms** to create **objects**. To create these two different classes of objects, we need to create two models, Student and Course.
 Our Student class, with name and grade attributes, will look something like this:

class Student
  attr_reader :name, :grade
 
 @@all = []
 
  def initialize(params)
    @name = params[:name]
    @grade = params[:grade]
    @@all << self
  end
 
  def self.all
    @@all
  end
 
end
In this model, we have an attr_reader for name and grade
 
 




user relationships, sessions and authentification

Walk through application in browser going over login and basic CRUD

Application controller- sessions, enable sessions, set session secret(explain what these are)

helper methods(explain what these are)

models-inherited from, has_secure_password, validate, has many and belongs to

DB-folder what are the files for?, what is the schema?, password and digest and the importance of the belongs_to object having a foreign key and user id

config.ru- mounting controllers, use vs run? rack method override, pull up and explain a form and where the form goes and what is done in the route after the form, what is params and how the name on the form is set to the key and the user input is the value
run vs use in config.ru
restful routing
redirect vs erb
bcrypt
password digest
sessions
get vs post
patch vs put
params
session secret in app controller
rack::override





12:36
when we call .tap on an Object, we can insert extra operations before any other code executes
seed file is dummy data so the app can function
interpolate
ActiveRecord can use ruby method sqlite
run vs use
What is Active Record?
Is a ruby gem
Active Record is the M in MVC - the model - which is the layer of the system responsible for representing business data and logic. Active Record facilitates the creation and use of objects whose data requires persistent storage to a database. It is an implementation of the Active Record pattern which itself is a description of an Object Relational Mapping system.
CRUD
Create
Read
Update
Delete
trainer = Trainer.create(:username => "Jake", :email => "jake@gmail.com", :password => "123")
pokemon = Pokemon.create(:name => "Charmander", :pokemon_type => "fire")
Child does not know who it is until they know who they belong to
trainer.pokemon << pokemon  to give him the variable of pokemon we just made
This should give the pokemon an ID
can use .new then .save
Trainer.last.update(:username => "Cheese")
Trainer.find(4).update(:username => "Pasta")
Trainer.find(4).delete
Class Trainer
has_many: pokemon
Trainer is the parent class and knows their child
Class Pokemon
belongs_to: trainer
Pokemon is the child class and doesn’t know who it belongs to so you let em know by “<<“
Restful routing is a convention to help keep clear naming routes like /signup is to the signup page
when we call .tap on an Object, we can insert extra operations before any other code executes
Config.ru is the .exe file
mapped the to Run app controller or use the other controllers because trainer and pokemon controllers inherit from app con
[7:49 PM] .
[7:49 PM] .
[7:49 PM] .
[7:49 PM] .when we call .tap on an Object, we can insert extra operations before any other code executes
seed file is dummy data so the app can function
interpolate
ActiveRecord can use ruby method sqlite
run vs use
What is Active Record?
Is a ruby gem
Active Record is the M in MVC - the model - which is the layer of the system responsible for representing business data and logic. Active Record facilitates the creation and use of objects whose data requires persistent storage to a database. It is an implementation of the Active Record pattern which itself is a description of an Object Relational Mapping system.
CRUD
Create
Read
Update
Delete
trainer = Trainer.create(:username => "Jake", :email => "jake@gmail.com", :password => "123")
pokemon = Pokemon.create(:name => "Charmander", :pokemon_type => "fire")
Child does not know who it is until they know who they belong to
trainer.pokemon << pokemon  to give him the variable of pokemon we just made
This should give the pokemon an ID
can use .new then .save
Trainer.last.update(:username => "Cheese")
Trainer.find(4).update(:username => "Pasta")
Trainer.find(4).delete
Class Trainer
has_many: pokemon
Trainer is the parent class and knows their child
Class Pokemon
belongs_to: trainer
Pokemon is the child class and doesn’t know who it belongs to so you let em know by “<<“
Restful routing is a convention to help keep clear naming routes like /signup is to the signup page
when we call .tap on an Object, we can insert extra operations before any other code executes
Config.ru is the .exe file
mapped the to Run app controller or use the other controllers because trainer and pokemon controllers inherit from app con
Rack is the middleware and sinatra just "rides" on tip of it.
Rack, a modular Ruby webserver interface Rack provides a minimal, modular and adaptable interface for developing web applications in Ruby. By wrapping HTTP requests and responses in the simplest way possible, it unifies and distills the API for web servers, web frameworks, and software in between (the so-called middleware) into a single method call.
Rack is a bare-bones middleware and therefore a bit more lightweight but doesn't help you that much when building complex applications.
Sinatra is a Domain Specific Language (DSL) for quickly creating web-applications in Ruby.
It keeps a minimal feature set, leaving the developer to use the tools that best suit them and their application.
Sinatra is a small "framework" on top of Rack providing you with nifty methods to get up running quickly. It's not that lightweight as Rack but still as light as a cloud in the sky.
redirect vs erb
redirect is used to go to a specific route with a user id in the url
erb is just a view page
what does bcrypt encripts salts(adds extra characters) and hashes created password for comparing to your password when you log in. Hashes of same password would be same but after salting would be different
Works with 'bcrpyt' gem
Has_secure_password is a MACRO of 'bcrypt' is a built in validator
comes with method called authenticate which takes in argument of password
what does authentication do
when creating a password for a user it gets hashed,  salted and encrypted
when you log in,  your entry gets hashed
authentication compares the 2 hashed passwords
similar to validates_uniqueness
params are hashes that have key value pairs just like sessions
Where do you get key name for params
Params keys based on input name on forms
What is Method override - overrides methods concerned with delete and patch
use Rack::MethodOverride
allows us to you patch and delete requests
Schema passsword_digest is where they store the hashed salted encrted pasword
cannot just be password since it would literally show password
has_many and belongs to are a part of  Active Record associations::base
TrainersController < ApplicationController
Trainer INHERITS from application controller
register Sinatra::Flash allows error messages
models are chef
controllers are waiters
views are the plate
models are ruby objects
database is just raw data
Get post put etc are HTTP verbs
POST vs GET
Get brings up the page requested
post takes user entered data and route to the correct view afterward
GET is used to request data from a specified resource http. it routes to the ACTION of ?whatever
POST  used to send and post user data to a server to create/update a resource.
The browser makes an HTTP get request. The Sinatra controller (ie: app_controller.rb) takes that request and routes it to to the appropriate action (ie: /users)
This action then requests these objects from the models (ie: user.rb)
The model requests for the data from the database
The database responds and then the models send the objects to the action
The action sends the objects to the view for rendering (ie: erb: welcome)
The view responds with HTML
The controller takes that HTML and sends an HTTP response
Patch vs put
put - put all completely different parts (builds completely new car, put on the same plate)
Patch - fixes a few things here and there but (mostly the same car)
why use sessions? keeps track of user since http is stateless
session begin at signup
what is sessions
 is a hash that has key and value pairs, allows you to store sensitive data in a server. Will allow you to perform CRUD functions for the duration of the session. Session begins with logging in and ends at logging out.
cookies vs sessions
sessions save everything client side and server side
anything you do in that session will be saved
cookies only saves for that specifc page client side only
session "secret"(secret can be whatever) allows us to have passwords - extra layer of security
relationships in active record
Object Relational Mapping
Object Relational Mapping, commonly referred to as its abbreviation ORM, is a technique that connects the rich objects of an application to tables in a relational database management system. Using ORM, the properties and relationships of the objects in an application can be easily stored and retrieved from a database without writing SQL statements directly and with less overall database access code.
makes join tables easier instead of doing it the harder way (create_table if does not exist)
when we call .tap on an Object, we can insert extra operations before any other code executes
Tells application control where to find public and app views
  set :public_folder, 'public'
    set :views, 'app/views'
ActiveRecord::Base.establish_connection(
  :adapter => "sqlite3",
  :database => "db/#{ENV['SINATRA_ENV']}.sqlite"
establishing connection to sql lite and connection to database
dont forget to open your flow chart
open requirements page on learn to follow
flash[:error] = "#{trainer.errors.full_messages.to_sentence}. Please try again."
<% if flash[:error] %>
<h3 style="color:red;"><%= flash[:error] %>
<% end %>
pokemon new for creating new pokemon
pokemon edit for edit pokemon
pokemon show here is your newly created pokemon. Get sent here after after editing and creating a new pokemon
trainers show is the logged in user front page
trainer login is the login page
trainer create_t is the create user page
index is the main homepage for logging in or signin up
Yield in html
It tells sinatra to put your view content to this block (which is called by yield) at that place in the layout file.
view.html.erb:
<p>Hello there!</p>
<p>I'm a content from view</p>
layout.html.erb:
<!DOCTYPE html>
<html>
  <head>
  </head>
  <body>
    <%= yield %>
  </body>
</html>
Now the results will be like this:
<!DOCTYPE html>
<html>
  <head>
  </head>
  <body>
    <p>Hello there!</p>
    <p>I'm a content from view</p>
  </body>
</html>
rack up vs shotgun
added this line to view pages to prevent showing buttons to users on other users pages
<%if current_user == @pokemon.trainer%>
8:54
.
8:54
.
8:54
.
8:54
when we call .tap on an Object, we can insert extra operations before any other code executes
seed file is dummy data so the app can function
interpolate
ActiveRecord can use ruby method sqlite
run vs use
What is Active Record?
Is a ruby gem
Active Record is the M in MVC - the model - which is the layer of the system responsible for representing business data and logic. Active Record facilitates the creation and use of objects whose data requires persistent storage to a database. It is an implementation of the Active Record pattern which itself is a description of an Object Relational Mapping system.
CRUD
Create
Read
Update
Delete
trainer = Trainer.create(:username => "Jake", :email => "jake@gmail.com", :password => "123")
pokemon = Pokemon.create(:name => "Charmander", :pokemon_type => "fire")
Child does not know who it is until they know who they belong to
trainer.pokemon << pokemon  to give him the variable of pokemon we just made
This should give the pokemon an ID
can use .new then .save
Trainer.last.update(:username => "Cheese")
Trainer.find(4).update(:username => "Pasta")
Trainer.find(4).delete
Class Trainer
has_many: pokemon
Trainer is the parent class and knows their child
Class Pokemon
belongs_to: trainer
Pokemon is the child class and doesn’t know who it belongs to so you let em know by “<<“
Restful routing is a convention to help keep clear naming routes like /signup is to the signup page
when we call .tap on an Object, we can insert extra operations before any other code executes
Config.ru is the .exe file
mapped the to Run app controller or use the other controllers because trainer and pokemon controllers inherit from app con
12:36
Rack is the middleware and sinatra just "rides" on tip of it.
Rack, a modular Ruby webserver interface Rack provides a minimal, modular and adaptable interface for developing web applications in Ruby. By wrapping HTTP requests and responses in the simplest way possible, it unifies and distills the API for web servers, web frameworks, and software in between (the so-called middleware) into a single method call.
Rack is a bare-bones middleware and therefore a bit more lightweight but doesn't help you that much when building complex applications.
Sinatra is a Domain Specific Language (DSL) for quickly creating web-applications in Ruby.
It keeps a minimal feature set, leaving the developer to use the tools that best suit them and their application.
Sinatra is a small "framework" on top of Rack providing you with nifty methods to get up running quickly. It's not that lightweight as Rack but still as light as a cloud in the sky.
redirect vs erb
redirect is used to go to a specific route with a user id in the url
erb is just a view page
what does bcrypt encripts salts(adds extra characters) and hashes created password for comparing to your password when you log in. Hashes of same password would be same but after salting would be different
Works with 'bcrpyt' gem
Has_secure_password is a MACRO of 'bcrypt' is a built in validator
comes with method called authenticate which takes in argument of password
what does authentication do
when creating a password for a user it gets hashed,  salted and encrypted
when you log in,  your entry gets hashed
authentication compares the 2 hashed passwords
similar to validates_uniqueness
params are hashes that have key value pairs just like sessions
Where do you get key name for params
Params keys based on input name on forms
What is Method override - overrides methods concerned with delete and patch
use Rack::MethodOverride
allows us to you patch and delete requests
Schema passsword_digest is where they store the hashed salted encrted pasword
cannot just be password since it would literally show password
has_many and belongs to are a part of  Active Record associations::base
TrainersController < ApplicationController
Trainer INHERITS from application controller
register Sinatra::Flash allows error messages
models are chef
controllers are waiters
views are the plate
models are ruby objects
database is just raw data
Get post put etc are HTTP verbs
POST vs GET
Get brings up the page requested
post takes user entered data and route to the correct view afterward
GET is used to request data from a specified resource http. it routes to the ACTION of ?whatever
POST  used to send and post user data to a server to create/update a resource.
The browser makes an HTTP get request. The Sinatra controller (ie: app_controller.rb) takes that request and routes it to to the appropriate action (ie: /users)
This action then requests these objects from the models (ie: user.rb)
The model requests for the data from the database
The database responds and then the models send the objects to the action
The action sends the objects to the view for rendering (ie: erb: welcome)
The view responds with HTML
The controller takes that HTML and sends an HTTP response
Patch vs put
put - put all completely different parts (builds completely new car, put on the same plate)
Patch - fixes a few things here and there but (mostly the same car)
why use sessions? keeps track of user since http is stateless
session begin at signup
what is sessions
 is a hash that has key and value pairs, allows you to store sensitive data in a server. Will allow you to perform CRUD functions for the duration of the session. Session begins with logging in and ends at logging out.
cookies vs sessions
sessions save everything client side and server side
anything you do in that session will be saved
cookies only saves for that specifc page client side only
session "secret"(secret can be whatever) allows us to have passwords - extra layer of security
relationships in active record
Object Relational Mapping
Object Relational Mapping, commonly referred to as its abbreviation ORM, is a technique that connects the rich objects of an application to tables in a relational database management system. Using ORM, the properties and relationships of the objects in an application can be easily stored and retrieved from a database without writing SQL statements directly and with less overall database access code.
makes join tables easier instead of doing it the harder way (create_table if does not exist)
when we call .tap on an Object, we can insert extra operations before any other code executes
Tells application control where to find public and app views
  set :public_folder, 'public'
    set :views, 'app/views'
ActiveRecord::Base.establish_connection(
  :adapter => "sqlite3",
  :database => "db/#{ENV['SINATRA_ENV']}.sqlite"
establishing connection to sql lite and connection to database
dont forget to open your flow chart
open requirements page on learn to follow
flash[:error] = "#{trainer.errors.full_messages.to_sentence}. Please try again."
<% if flash[:error] %>
<h3 style="color:red;"><%= flash[:error] %>
<% end %>
pokemon new for creating new pokemon
pokemon edit for edit pokemon
pokemon show here is your newly created pokemon. Get sent here after after editing and creating a new pokemon
trainers show is the logged in user front page
trainer login is the login page
trainer create_t is the create user page
index is the main homepage for logging in or signin up
Yield in html
It tells sinatra to put your view content to this block (which is called by yield) at that place in the layout file.
view.html.erb:
<p>Hello there!</p>
<p>I'm a content from view</p>
layout.html.erb:
<!DOCTYPE html>
<html>
  <head>
  </head>
  <body>
    <%= yield %>
  </body>
</html>
Now the results will be like this:
<!DOCTYPE html>
<html>
  <head>
  </head>
  <body>
    <p>Hello there!</p>
    <p>I'm a content from view</p>
  </body>
</html>
rack up vs shotgun
added this line to view pages to prevent showing buttons to users on other users pages
<%if current_user == @pokemon.trainer%>
