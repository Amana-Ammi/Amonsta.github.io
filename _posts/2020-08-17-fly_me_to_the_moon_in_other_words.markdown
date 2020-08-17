---
layout: post
title:      "Fly Me To The Moon(In Other Words)"
date:       2020-08-17 04:54:56 +0000
permalink:  fly_me_to_the_moon_in_other_words
---


After completing my Sinatra Portfolio Project, I do feel like I landed on the moon. There were so many new concepts introduced that I'm sure this is similar to building a spaceship. From Databse Management, to the (so far) frustrating world of CSS, a moon landing was well deserved.

However, using the Sinatra Framework to create my first website wasn't as scary as I thought. The goal of this project was to use the Sinatra Framework to build our own MVC (model, view, controller) app that tracked something important to us while also applying ActiveRecord's CRUD (create, read, update, delete) actions.  

Immediately, I reached out to my friends who are almost all entrepreneurs. The main questions I asked involved how they managed their inventory and clients outside of social media. My feeds are flooded with the businesses of my friends and I always find myself resharing multiple posts a week to help them with exposure. Needless to say, they have that side covered. Client management, though? Their mostly scheduling via DM's and emails. It's working for them but they all expressed the wish of something more organized and contained.

That's where I came in. For my first shot at this, I decided it was best to narrow the business types down to a single business. This way, I could wrap my head more easily around what I needed to build. Sticking with this idea I also feel will make it much easier to expand in the future so that I can tailor to the needs of multiple business owners.

!nk Complete.

A simple way for Tattoo Artist's to keep track of their clients. 

To no surpirse, the best way to explain my application is simply through it's CRUD actions. 

CREATE

What I've come to realize during this Sinatra journey is that a website just isn't too fun if you can't interact with it and build your own little profile within it. So that was my first step. I wanted my users/Tattoo Artist's to be able to create thier own account in which they could also create or book thier new clients. It's a multi-step process but when broken down using the single responsibilty principle, it comes together pretty smoothly.

Using this principle, I created two separate files to hold my User and Client's create actions. A `user_controller.rb` and a `clients_controller.rb`. It's also important to note my association between the two. A User `has_many :clients` and a Client `belongs_to :user`. 


Within my 

READ

UPDATE

DELETE

In other words... it's really just English.

