---
layout: post
title:      "Another Project: PicList!"
date:       2019-03-07 12:44:42 -0500
permalink:  another_project_piclist
---


## React with redux on the frontend and rails API on the backend.

Welcome, welcome, welcome. Today I'll write about another project that has been in the works. I call this one PicList. It uses some popular technologies: React, Redux, Rails.

This project sets out to implement a type of content and UI with which many of us will now be familiar. An app where you seamlessly scroll through a series of images. The images are available to view if you simply visit the page, and you can click the artists' names to see all the images by that specific artist. More features become available when you create an account or login.

![screenshot of picList app](https://i.imgur.com/UksQXYa.png)

#### Accounts

Account creation neatly handles email validity and uniqueness, as well as username uniqueness. Logins are handled securely using JSON Web Tokens to pass authentication between the front and back ends. The gems knock and bcrypt are incorporated to manage these features. 

One important thing to note about the current state (in March 2019) of knock and rails: 

There was a compatibility issue introduced in a recent update, but there is already a fix. I'll post this here should it be helpful as a reminder or to anyone searching around for the fix.

Part of configuring knock involves running this command:

```
rails generate knock:install
``` 

As it says in the knock READ_ME, this will create the following initializer: ``` config/initializers/knock.rb ```

The fix was to add this additional line of code in the block found within that initializer (so it'll be just the second line of code)

```   config.token_secret_signature_key = -> { Rails.application.credentials.read } ```


That was fun trying to debug. Since it was my first time using knock I thought it was something I had done wrong in the setup. Thanks to my teacher Enoch for the assist on that one.

#### Features


Once you've got your account setup and logged in, you gain access to 'save' and 'unsave' images to your collection. This allows you to keep track of artists and works of art that you come across, revisit them later, etc. This is implemented with an instantly responsive single page web app on the front end, and all data manipulation and persistence being handled with fetch requests to the rails api back end. 


#### Notes from working on this project

One thing that tripped me up again was correct naming conventions for rails join tables. I use a join table to map the many-to-many relationship between pictures and users who have saved those pictures. I'd like to point to this (WARNING) vulgar but extremely helpful and simple article explaining them:

[Join Tables Naming Conventions](https://www.bhalash.com/archives/13544808137)


Something to come back to and refactor on this project would be the way that I am loading artist show pages. I'd like to implement a way to ensure the component unmounts and remounts when the artistPics fetch request is complete. Currently there are a series of conditionals ensuring that the ArtistContainer waits for the artistPics to be received before rendering its children components. I think there is likely a cleaner way to handle this, as mentioned.


Please check out the [github repository](https://github.com/Peter-G-Stone/proj-photo-feed) and this [demo video](https://youtu.be/3HY50qqVFgY)!

Thanks for reading!

#### - Peter Stone
March 7, 2019
