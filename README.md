# squish
Quick simple GUIs so you don't have to remember command flags

## Concept
This is an idea I'm working on. Basically, there are a lot of CLI commands that I don't use often enough to remember the exact format of their command flags. I'll know exactly what I want to do, but it'll take me a couple minutes of scouring the man page or googling to figure out how exactly to do that. This is annoying.

My solution to this issue is to create very simple GUIs for these commands. These GUIs will be specified by a config file that sorta just lists flags, what they do, and what type of value they take. This won't create beautiful, easy-to-use GUIs meant for an end user, but that isn't the point. This will create barebones GUIs that will help command-line-friendly power users do what they need to do faster.

My plan is to implement this in Python3 with whatever the most popular GUI toolkit is for Python. Basically, the hope is that you'll type `squish somecommand` and a simple little pop-up GUI for _somecommand_ will appear. All of the options will appear at the top, and it'll show you the raw command that'll be executed at the bottom. You can run it with an Execute button, or you can just copy-paste the command and run it in a terminal yourself. The goal is that squish is just a crutch to get you going; once you've oriented yourself with the syntax of _somecommand_, you might very well close squish and go back to typing that command manually. 
