---
layout: post
title:      "Cooking Up Something Good"
date:       2018-11-19 17:23:52 +0000
permalink:  cooking_up_something_good
---

### Ingredients - Gems and Learning Web Development

One of the most useful and exciting things about software development is the magic of frameworks and gems. These bits of pre-existing code are given to us by the benevolent open-source gods:  the programmers who have come before. The Forerunners. The Precursors. 

![Precursors](https://i.imgur.com/m0TEDou.jpg)
> Precursor artifacts.

In my recent projects I've taken advantage of a number of excitingly useful gems. In this blog post, I will discuss a few of the notable suspects. These are examples of gems that you may want to familiarize yourself with if you have not already.


### Sinatra

![Piano player](https://i.imgur.com/0ofogca.jpg)
> The bandleader.

[Sinatra](https://github.com/sinatra/sinatra) is essentially a simplified, less powerful, less magical (ie less complex), little brother to the more famous "Rails" framework. At the Flatiron School they encourage picking up this framework first. Removing some of the 'magic' of Rails allows one to familiarize oneself with more of the inner workings of web development, allowing a deeper understanding of the functioning of these large code libraries. 

For example, in Sinatra when you want a User class that will be saved in your database correctly, you've got to... 
* create an Active Record migration file using the gem 'rake' (rake db:create_migration NAME=create_users)
* fill out that migration file accordingly
* create a User model file
* in that file have the class User inherit from the gem 'activerecord' (class User < ActiveRecord::Base)
* then run the migration with a rake task (rake db:migrate)

In Rails you would just run

> rails g model User name:string email:string
>

That command would create the model file, as well as an appropriately setup migration file. There are other commands which would also set up the controller actions (ie handle the http requests for the web app using these models and databases). 

Essentially, Sinatra is a lower level of abstraction.

Via Sinatra and its connections to other gems, including the ones mentioned, one is able to very quickly pick up the concepts inherent in Rails, and one can explore the interrelations between http requests, databases, database queries, Ruby classes, and interactions of Ruby objects.



### Active Record
![Quill and Parchment](https://i.imgur.com/lS394gz.jpg)
> The magic of data on the internet: information storage and access. The printing press taken to the millionth dimension; the written word taken to the billionth dimension; the spoken word to the trillionth. You know what I'm sayin'.


[Active Record](https://api.rubyonrails.org/classes/ActiveRecord/Base.html) can handle the database portion of web apps. We use it in Sinatra, and it is also used in Rails. Peruse the docs - this gem provides you with the functionality to dynamically define objects that come with a lot of preexisting capability.

For instance, let's say you define a "model" class, such as User, and have that class inherit from ActiveRecord::Base, and create a "migration" to create a table in your database representing that class and its attributes. Let's say your migration specifies that you would like two attributes, both strings, called "name" and "email".

This command would create a new instance of the class User, assign its name to "NAMEHERE", and assign its email to "EMAILHERE", but would not save it into the database:

>User.new(name: "NAMEHERE", email: "EMAILHERE")

 In order to create and save the instance, you'd want to use this command instead:

>User.create(name: "NAMEHERE", email: "EMAILHERE")


Or you could instantiate the object, then save it: 

>u = User.new(name: "NAMEHERE", email: "EMAILHERE")
>
>u.save

You can use the preexisting Active Record finder methods:

>u = User.find_by(name: "NAMEHERE")
>
>u = User.find_by_id(1)

You can update the record:

>u = User.find_by(name: "NAMEHERE")
>
>u.update(name: "Peter")

You can even DELETE the record:

>u = User.find_by(name: "Peter")
>
>u.delete


These collection of handy database actions are collectively referred to as CRUD -> CREATE, READ, UPDATE, and DELETE.


As you can see this Active Record gem thing is really handy and will surely save you many, many hours.



### Tux
![Tuxedo](https://i.imgur.com/jeWMOYb.jpg)

[Tux](https://github.com/cldwalker/tux) allows us to interact with our models (such as "class User") and our database via our command line. This is incredibly useful when it comes to debugging and testing your web app. It loads up the state of your database (which ANOTHER gem, rake, allows you to 'seed' with data). It loads up all your classes and their connections. You can explore the related classes you've defined, mess with the data in your database, all within your console. It's magnificent.  Require it in your gemfile and type "tux" into the command line. 

### Bcrypt
![Woman shushing](https://i.imgur.com/9dkWxx4.jpg)

Require bcrypt in your gemfile. Add this to your User class:

>has_secure_password

Add a column of type string to your User table. Call it:

>password_digest

In your application controller (the file which will handle some or all of our http requests in Sinatra), add this:

>configure do
>
     >    enable :sessions
>    
     >    set :session_secret, "secret"
>    
>end

Your User class will now have the following functionality:

>u = User.new
>
>u.password = "mypass"
>
>u
>
> --> User id: nil, name: nil, email: nil, created_at: nil, updated_at: nil, password_digest: "$2a$10$dG4TN2UuPwp5ONMRBQQFcO/Etxubri/h8gde5DmnYyN..."
> 
> 

You see how the password "mypass"  was not stored in our database. It was "salted" and "hashed".

If we then do this:

> u.save
> 
> User.all.last.password
> 
> // ( this will get the user we just saved from the array of all Users, and ask for it's password )
> 

We get this:

> nil 
> 

We can not simply ask the User array for the password of the User.

What we can do is this:

> u = User.all.last
> 
> u.authenticate("mypass")
> 

Which will return the user:

> User id: 5, name: "David", email: "dmail", created_at: "2018-11-19 17:02:00", updated_at: "2018-11-19 17:02:00", password_digest: "$2a$10$dG4TN2UuPwp5ONMRBQQFcO/Etxubri/h8gde5DmnYyN..."
> 

If we give it the wrong password:

> u.authenticate("badpass")
> 

We get "false". 


Pretty useful stuff here. 

There are a number of other gems I have been finding quite helpful:

* Corneal - sets up the file structure for a Sinatra app
* Rake - provides console tasks to create migration files, run migrations (ie setup and edit tables in the database), seed the database with information
* Pry - allows us the run the program to a certain point (a Binding)  and then enter a command line interface at that spot in the program.



I encourage you to explore these gems and discover their wondrous applications to web dev!

Thanks for joining me on this here blog post.

#### Gratefully yours, 
#### Peter Stone

