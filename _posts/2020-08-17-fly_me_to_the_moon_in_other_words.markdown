---
layout: post
title:      "Fly Me To The Moon(In Other Words)"
date:       2020-08-17 00:54:57 -0400
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


Within my user_controller, I created a `GET` request to render a signup form that I created in a Views folder titled "Users". After rendering my form, I needed to create a `POST` request in order to actually "create" my user. Those actions looked like this;

```
class UserController < ApplicationController

    #Renders sign up form
		
    get '/users/signup' do 
        erb :'/users/signup'
    end 
   
		
    post '/users/signup' do 
				
        if params[:name] == "" && params[:email] == "" && params[:password] == ""
            redirect '/users/signup'
        else
            @user = User.create(
                name: params[:name],
                email: params[:email],
                password: params[:password]
            )
            session[:user_id] = @user.id
            redirect "/users/#{@user.id}"
        end
    end
```

The actions for creating a new client were almost identical. The main changes lie in the View file rendered and the params data that I wanted to create for each Client.

READ

The reading action is easily understood as the user ability to view the data they have created. Take our clients for example. It wouldn't make much sense to manage your clients within an app if you could never go back and see those clients. 

For my application, the user has a few places where they can see clients. They are able to see the individual client's information immediately after creation and they are also able to view an index of all created clients via an index route ('/clients'). These are two separate routes that render two different view files. 

The index route, '/clients', was built simply like this:

```
get '/clients' do
        if logged_in?
            @clients = Client.all
            erb :'/clients/index'
        else
            erb :welcome
        end
    end
```

Within the embedded Ruby file (erb :'clients/index'), I didn't crate a form like in the previous CRUD action. Instead, I just iterated through the Client.all method using plain ole Ruby.

UPDATE

For now, the main way I implemented the Update action is through the Clients Controller. As a tattoo artist and honestly, anyone who deals with customers, we know things change often. Dates change, addresses change, ideas change, etc. It's life. Also a very important feature that my Sinatra Application needed. Again, I have the action of rendering my edit form from a view file. 

Then, instead of a 'post' action, I have to implement 'patch'. The 'post' action in my application "creates" an client, whereas the "patch" action modies a client. 

```
patch '/clients/:id' do
        find_client
        if params != ""
            @client.update(
                first_name: params[:first_name],
                last_name: params[:last_name],
                description: params[:description],
                location: params[:location],
                price: params[:price],
                appt_date: params[:appt_date],
            )
            redirect "/clients/#{@client.id}"
        else
            redirect "/clients"
        end
    end
```

All together, this reads like;

"First, we need to find the client that needs to have informationation changed. (find_client is  a helper method I created to do just that, find the client). Then, if the update form isn't blank, let's go ahead and update our listed values then send them back to the individual client page that now has the updated information. However, if the update form was made blank, let's take the user back to the index page where they'll see no changes were made to that client."

DELETE

Just as the word implies, this action will delete the requested information. The delete request however does not need it's own view file nor does it use a GET, POST or PATCH request. It uses a, simply put, DELETE request.

```
delete '/clients/:id' do 
        find_client
        if authorized?(@client)
            @client.destroy
            redirect '/clients'
        else
            redirect "/users/#{current_user.id}"
        end
    end
```

An important thing to note with Delete and Patch requests is that they are only possible if I update my config.ru file with the line `use Rack::MethodOverride` This along with some additional coding in our View files, allows for our objects to be overridden.


In other words, it reads just like english.


