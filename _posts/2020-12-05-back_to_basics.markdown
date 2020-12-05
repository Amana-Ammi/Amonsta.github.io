---
layout: post
title:      "Back To Basics"
date:       2020-12-05 22:47:30 +0000
permalink:  back_to_basics
---


See https://amana-ammi.medium.com/back-to-basics-78cce6c7fed3 for original blog post
---

Back To Basics
Mason Jar. Iced Mocha. Side glass of water. Dutch Shepherd nudging a toy in my side.
"Alexa, play my AfroBeats Playlist."
Open VSCode… and go.
This was my daily scene as I worked on my fourth Flatiron School Project. This time, creating both a backend and frontend environment. In the previous project, I used Rails for both. This time around however, Rails is just going o be my backend environment. This immediately raised my The Rock Johnson eyebrow.
Dwayne "The Rock" JonsonFor my project I decided to keep it simple and host both of my environments in the same project folder. For now, I felt this was the best way to go seeing as I'm already learning JavaScript and the last thing I need right now is an issue with my repos and hours on google. In the future, and as a best practice, it'll be best to keep these more separate than what I have here.
After so many labs and READMEs, I often forget some of the shorthand commands that comes in handy while working on my projects. Here, I'll go over a few of the commands that really helped save me time and headaches.


---

About
My previous projects have been all things of interest for me. A Tattoo Client Scheduler, A Music Review App, etc. However, for this one I really wanted to showcase myself. Since beginning this journey of Software Engineering I've noticed that almost, if not all, developers have turned themselves into a brand. So why haven't I done it yet? Well, with this project I do just that.
My first name is pronounced "uh-mah-nuh" so obviously, I gave myself the moniker, "Amonsta". It's only right. For my JavaScript project, I built my own online merchandise shop with that title. I drew up some lettering and had my best friend draw a version of me as a zombie (because I LOVE Zombies!).
The Bones
My basic structure in VSCode is as follows;
There is definitely a lot more going on in this project than any of the previous builds so it was almost imperative that I became as efficient as I could with shorthand commands. Before, I was used to building my entire project in one directory, however, here, it is important that I use separation of concerns for my front and backend folders.
First, instead of clicking multiple times throughout my VSCode to open and create new folders for my directory, I can easily go into my terminal and type mkdir <directory-name>. mkdir meaning, "make directory". I first created the main directory, that being the project name "amonsta-merch" and then onto the subdirectories for front and backend.
The second and probably most important one was the "change directory" command. As previously noted, my project required three different directories. Although I spent a lengthy amount of time in each area, I still needed to switch between each directory fairly often. Without properly changing directories, you'll quickly realize that certain actions you make in the terminal won't execute. To quickly maneuver from one directory to another, I used these commands in my terminal:
cd ..
cd backend-api
cd frontend-client
cd .. Brings me back up to my root directory and allows me to access either one of my other sub-directories. In my root directory, I also have my Notes file and README so anytime I made changes to those, I would need to be within the root directory to commit those changes to my Github repository.
cd backend-api Takes me over to my Rails Api. I want to be sure I'm within this directory whenever I'm making changes like migrating new activerecord models, adjusting controllers, running my rails server, and anything else dealing with my rails. If you try running rails s and you keep getting a message telling you to create a new Rails application, double check that you're in the right directory.
cd frontend-client Finally, I have my Javascript side. Majority of this project involved working in the frontend so I spent a lot of time here. Even when there were changes to my css, I needed to execute them in this directory.
As we all know, once you get into a flow with your coding, pauses to change things around can get annoying. Instead, you can use the handy tools that VSCode provides and be a true keyboard Warrior.
																										




