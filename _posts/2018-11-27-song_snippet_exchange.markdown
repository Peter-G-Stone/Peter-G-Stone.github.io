---
layout: post
title:      "Song Snippet Exchange"
date:       2018-11-27 10:27:45 -0500
permalink:  song_snippet_exchange
---




I set out to solve a problem I've seen with songwriters. At times, it is possible to create many, many song ideas, and one is filled with inspiration. However, more often than not there is not enough time to fully develop and explore all the song ideas that a songwriter jots down or sings into their voice memo app. These song snippets are often lost as the artist moves onto new and exciting ideas, or as they get honed in on whichever composition they choose to dive into.


.
 
  
	 
![Notebooks](https://i.imgur.com/iwjtkYQ.jpg)



.



Conversely, there are certainly times when it feels impossible to decide where to even start with writing. One may feel overwhelmed, frozen, petrified. Just in my experience I've had periods of discouragement and writer's block that have lasted more than a month.


.



![Snowy branch](https://i.imgur.com/2m0O1sc.jpg)


.



My app is the beginnings of a forum where fledgling, incomplete compositions can be shared. Where songwriters can find collaborators and potentially break their blocks by browsing other writers' nascent ideas. Users can create snippets with the following attributes...
* Title
* General Description
* Chart filename - this will turn into an image uploader where one can add images of sheet music
* Audio filename - similarly, for audio files
* Lyrics

.

![Image from my webpage showing the creation page for a song snippet](https://i.imgur.com/qEnaA5M.png)


.


Here are some images of the current forum layout and menu bar, with some dummy data.


.





![Demo image from app](https://i.imgur.com/hUBSMhN.png)


.


![Demo image from app](https://i.imgur.com/FHycqoL.png)


.



In creating this app, I am solidifying my knowledge of ActiveRecord, Ruby, Sinatra and their interactions. There are Active Record tables setup for Users and Snippets. A user "has_many" snippets and a Snippet "belongs_to" a User. The http pathways and views are all setup to allow functioning navigation and CRUD functionality for the available data types. Users can follow and unfollow other users. Fun stuff!


.


I intend to return to improve styling, add a functioning messaging system, and to create a mobile version. 

[Here's a video walkthrough.](https://youtu.be/zaqJIufcCss)


Thanks for reading.

#### - Peter Stone
November 27th, 2018
