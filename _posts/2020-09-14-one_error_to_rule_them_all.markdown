---
layout: post
title:      "Only One May Enter Here"
date:       2020-09-14 01:52:51 -0400
permalink:  one_error_to_rule_them_all
---


Well, not really. However, Rails does make it look easy and in this post I'll explain a few of my favorite error methods.

If you're reading this blog entry, chances are that you've encountered at least a few error messages while browsing the internet. For me, probably a few.. hundred ha. No matter how many times I think my password is going to cement itself into my brain, it doesn't. So you can imagine that a lot of the errors I have encountered involved my User logins. Whether it's my Petsmart account or even my Insagram, I'm usually met with an "Email/Password combination invalid. Please try again" message flashing across the screen and then I send myself an email, reset it, and start the cycle all over again the next day.

As annoying as it all may seem, it's extremely necessary. I'd rather have a hard time logging into my own account than give a hacker or anyone else open-door service to my accounts. Plus, it flet good to be on the other side of things as I developed my Rails application. What was one way that I achieved this? Validation errors!

First, what is a validation? Well, let's get a little Disney here and say we have a Cave of Wonders like in Aladdin. The Cave of Wonders is our Database.The look of The Cave of Wonders is unforgettable, it's a sand guardian who takes the form of a Tiger's head. If you don't recall the Tiger's warning, I'll remind you. 

“Know this: only one may enter here, one whose worth lies far within. A diamond in the rough.”

The Tiger is the protector of The Cave of Wonders. Swallowing every unworthy being who tries to enter with a horrifying swiftness. In Rails, our validation code is like our Tiger, protecting our database (The Cave of Wonders) from any and all invalid code that tries to enter. Can you imagine if Jafar was able to enter The Cave of Wonders? There wouldn't even be an Aladdin! That's just not right.

Validations are accessible thanks to Active Record. Afterall, Active Record handles all things database. For my Rails project, I had to think like, well, me. So starting with my User model, I implemented one of my first Validations.

```
class User < ApplicationRecord
	....
	validates :username, uniqueness: true
	...
end
```

Here, `validates` is my mehod and it is taking in two  arguments. The first argument is the attribute name that I want to validate. While the second argument is a hash of options that provide the details of "how" to validate it. In plain english, I'm saying that the User's Username must be unique. Meaning there can only be one person with this Username saved into the database. As simple as this line looks, it's exactly what we experience when signing into a new social network. How can I tag my favorite Cosplayer in a post if ten other people have their same username? The uniqueness: key can be sprinkled throughout a simple web application and it may seem small, but the security it provides is huge.

Another validation that I used for my Rails project was;

```
validates :review, uniqueness: {scope: :user, message: "-- can only be reacted to once."}
```

Here, I am again using the uniqueness validation but in a bit of a different way. I'm not stopping someone from writing the same review. I'm actually stopping a user from leaving multiple comments on the same review. The scope: option inside the curly brackets gives me the ability to choose one or more attributes to aid in verifying the uniqueness of my review's reaction. I only need the user: to ensure that they aren't flooding the Review with comments

Now, in most, if not all, Social Media applications, this IS something that you can do. However, for the sake of my small application, I'd like to limit those reactions for the moment. What's great about validations is, when I am ready to change and perhaps open this part up, I only have to go to one place to remove the code, the model where I placed it. 

As you are familiar with, The Cave of Wonders has an unbelievable amount of "traps" set up to catch any unworthy travellers. Whether, it's at the entrance or inside the cave (should they be tempted with gold). As you can imagine, Active Record also provides numerous ways to validate your code. Even opening the floor for you to create custom validations that better suite your application. If you are interested in using validations yourself, I highly encourage you take a look at the official documentation for Rails Active Record Validations here [https://guides.rubyonrails.org/active_record_validations.html](http://).



