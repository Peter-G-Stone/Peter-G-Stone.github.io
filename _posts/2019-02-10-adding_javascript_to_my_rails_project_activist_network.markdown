---
layout: post
title:      "Adding Javascript to my Rails Project: Activist Network "
date:       2019-02-10 20:54:22 -0500
permalink:  adding_javascript_to_my_rails_project_activist_network
---

## Adding AJAX and Javascript

Hey there! Welcome to another installment of my software blog. Today I’m finishing up another project for the Flatiron School. The goal was to add several features that relied upon AJAX and Javascript to the previous project.

My project, as you may recall was a basic social networking app - Activist Network - intending to provide a space for collaboration between activist groups.

![First Demo Image of App](https://i.imgur.com/Q875cV3.png)

![Second Demo Image of App](https://i.imgur.com/4N7WJrw.png)

### Please see my new video walkthrough by [clicking here](https://youtu.be/I9sjwTNy3Vs).


Now I will discuss a few hiccups I ran into. A discussion that may benefit you, the reader, but which will certainly serve as a useful review for me as I lay them out.

Notably let’s begin with an issue I had using jquery’s $( document ).ready()

### JQuery's $( document ).ready()

I expected that code within $( document ).ready() would fire once the page had loaded the elements. However!

There is a feature of rails called turbolinks.

Turbolinks:
	... makes following links in your web application faster. Instead of letting the browser recompile the JavaScript and CSS between each page change, it keeps the current page instance alive and replaces only the body and the title in the head.


Many thanks to “mu is too short” from this stack overflow post:
https://stackoverflow.com/questions/18769109/rails-4-turbo-link-prevents-jquery-scripts-from-working/18770219#18770219


From experience confirmed by this post, I found from this post that $( document ).ready() does not play nicely with turbolinks. Thankfully, there is a simple solution, which is to use this instead:

$(document).on( ‘turbolinks:load', cbFunction )

(where cbFunction is the code you'd like to run upon the page load)

That solved that nicely.

The other issue I will discuss involved assigning event listeners to dynamically generated div elements.

### Event Listeners on Dynamically Generated Div Elements

I dynamically render my each group’s post index on its show page. I wanted to add Delete buttons to all of the current user’s posts. Each delete button has an event listener so that if clicked, my javascript asynchronously handles the delete action rather than having a page refresh.

Originally I attempted to add these event listeners in a separate function from where the posts’ html was being created and rendered on the page.

I was consistently failing to select the elements using jquery and their id’s - even though I could tell using my browser that the id’s were being set correctly.

The simple solution I realized, was to simply add the event listener as soon as the post was rendered, in the same function that was rendering the post. This solved my issue quite handily.

Further work on this project remains - the styling is still in need of much TLC, and it would be good to add some hashtag-esque feature, as well as things like messaging and ‘following’ users.

Thanks for reading!

#### - Peter Stone
Feb 10, 2019
