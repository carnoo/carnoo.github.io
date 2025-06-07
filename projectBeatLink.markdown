---
layout: post
title: project:beatLink
permalink: /beatlink/
css: ./_site/css/main.css
image: /assets/images/bll2.png
---

![header]({{page.image}})

## Yep, it's yet another discord music bot.

### Overview

BeatLink will be an application, or bot, for Discord that will allow users to stream audio to voice channels from certain media streaming services.

Currently, the goal is to only use YouTube for audio streaming. Other sources (specifically Spotify) may be added in post-launch support. I’ve wanted to build beatLink for a very long time, as I use Discord to stay in touch with friends and communicate with them when we play games online. 

The commands I’m targeting to build out within the context of a final project are /about, to claim the project as my own,  /commands, to list the commands usable by the client, and /play, which will serve as the core of the application. 

Queueing is the immediate goal; once the project is out the door for this class, I plan on continuing to work on beatLink for a while, until it is a stable, robust product. 
Finally, once the bot is done and stable locally, I plan on pushing the project to a remote hosting solution, to ensure a 24-hour uptime. 


### Production Cycle

#### Preproduction
I started out my production of beatLink by learning quickly that getting a bot of this scale off the ground and feature complete was going to be a lot more difficult than I imagined. When I looked up solutions to the goal I had, I found about a dozen ways of doing what I wanted, all with varying difficulties of execution. I ultimately want this project to be something that I put together, not some copy-paste job where I take someone else’s bot and host it myself on an Amazon EC2 instance. I needed something to consolidate all this information I had in front of me and push me in one direction so I could get started. 

Initial research wasn’t very productive. There’s a lot of ways to build an application that serves the needs I wanted to address. But with the breadth of options came a minefield of solutions that have been depreciated, don’t do exactly what I need,  or copy-paste jobs that don’t allow me to learn anything.  If I went with the last option,  then post launch support wouldn’t be easy or viable for later. I want to stick with this project long term, and expand its offerings down the road, after this class. 

For Project:beatLink,  I wanted to create a script that would become a bot for Discord, that would have commands to find audio on YouTube, join a voice channel, and then stream that audio to said voice channel, and finally be hosted on a cloud server. After extensive searching, I found my starting point through Discord.js’s  documentation. The best thing it did for me was break down the prompt into different steps. I’ll elaborate on this in my conclusions, but I severely underestimated how big this project was going to be. 

#### Production

The first step was to get a bot registered with the Discord Developer Portal. I’ve used the Developer portal in the past, as I made a Discord bot during the pandemic, but that one was much smaller and limited in scale than what beatLink was going to become.  Registering a bot is by far the easiest part of this process. It’s only a bit of a headache if your bot gains serious traction and you need to get it verified.  
Here's where I went ahead with branding. I’m not much of a graphic designer, but I spent ten thousand years in Photoshop and produced the logo you saw on the cover page of this paper. 

The next (long) step is building the thing. Most Discord bots are written in either Node.js or Python, but in my experience, there’s more resources out there for Node.js, so I went with that. Node.js has a library that’s used to hook up to the Discord API called Discord.js. After setting up Node.js locally and then installing Discord.js, I was ready to start building the foundation of the bot. 
Foundational work mostly consisted of getting the bot connected to Discord  by adding it’s authentication token to certain spots in the bot’s code. Since the bot will be of some scale, commands aren’t stored in the central index.js file, but rather in a folder and cataloged subfolders. From this point, I took a step back to test before continuing with implementing the next two libraries that I’d be using: ffmpeg and youtube-dl. 

Here's where I ran into my first real bug that wasn’t syntax or something small: I had the bot up and active on Discord, the bot would attempt to answer questions, but it didn’t. After a day and a half of not being able to find the issue, I eventually cracked it as I was not pathing to the commands I had in folder correctly. It was a huge relief to finally get that out of the way, because that meant that the foundational work for the bot was done. I could finally move on to implementing the libraries needed for core functionality. 

Finding the right code was a nightmare. I had to take several days to find the right solution for the job. As of writing, the bot queues the song correctly, the bot can join the discord voice call (see below), but the audio isn’t playing audio. The bot leaves the channel as the song (or queue) ends but I don’t know why the sound isn’t audible.

Maybe it’ll work when I move it away from all its local restraints to a permanent, global solution. Right now, the bot is only compatible with my personal discord server. I need to change the config.json file in the root directory of the server to allow it to work on any server.

#### Conclusions

The single biggest lesson I learned from this project has to do with scale. When you say something like, “This is a music bot that streams music to voice channels,” you’re not looking at the entire thing from an eagle’s eye. Rather, you’re looking at one zoomed in look at a project. As you start building the thing out, you start slowly zooming out and seeing the scale of your project as it comes together. 

There’s a lot that I’d do differently with this project. For starters, I’d take size into account. Trying and retrying solutions to my issues with different libraries that  had to be installed via NPM meant that the project exploded in file size and library count. A count shows that I had 196 different node modules installed as a part of beatLink, but I know there are libraries in there that I didn’t use, such as oceanic.js.

I should’ve stuck to the plan better, and worried about major changes to that plan after the current iteration was done. BeatLink will ship with one core command, /play, which will be replaced by /queue and /stop as I work on the project over the summer. I’m fully committed to keep working on this, since I’ve wanted to build a project like this for a while and I’d get some use out of it on the servers I frequent. Eventually, it would also be cool if I could get it to read Spotify links so it could pull the correlating audio from YouTube. For now though, I need to make sure that it’s stable and working consistently. One annoying bug is the need for  a user to be in the voice channel before the bot is started, not even prompted. Otherwise, the bot thinks no one’s home. 

#### Link to beatLink: 
[...can be found here.](https://discord.com/api/oauth2/authorize?client_id=1100569135437594704&permissions=3147776&scope=bot%20applications.commands)