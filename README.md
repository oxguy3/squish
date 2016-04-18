# squish
Quick simple GUIs so you don't have to remember command flags

## Concept
This is an idea I'm working on. Basically, there are a lot of CLI commands that I don't use often enough to remember the exact format of their command flags. I'll know exactly what I want to do, but it'll take me a couple minutes of scouring the man page or googling to figure out how exactly to do that. This is annoying.

My solution to this issue is to create very simple GUIs for these commands. These GUIs will be specified by a config file that sorta just lists flags, what they do, and what type of value they take. This won't create beautiful, easy-to-use GUIs meant for an end user, but that isn't the point. This will create barebones GUIs that will help command-line-friendly power users do what they need to do faster.

My plan is to implement this in Python3 with whatever the most popular GUI toolkit is for Python. Basically, the hope is that you'll type `squish somecommand` and a simple little pop-up GUI for _somecommand_ will appear. All of the options will appear at the top, and it'll show you the raw command that'll be executed at the bottom. You can run it with an Execute button, or you can just copy-paste the command and run it in a terminal yourself. The goal is that squish is just a crutch to get you going; once you've oriented yourself with the syntax of _somecommand_, you might very well close squish and go back to typing that command manually. 

Another goal is to make it very easy to build a GUI for a new command. The config files will probably be YAML, and the idea is that it should only take like 10 minutes to figure out the config format and write a config file for a new command. Again, our target audience is power users, so we don't need the ability to create fine-tuned perfect GUIs -- we just need something that works.

# Config format (WIP)
Here's what a config for youtube-dl might look like:
```
meta:
  title: 'Download videos from YouTube (and more sites)'
  command: 'youtube-dl'
  flagSyntax: ' --%FLAG%=%VALUE%'
args:
  url:
    label: 'Video URL'
    widget: 'textbox'
    position: 10
    category: '__TOP__'
    output:
      filled: '%VALUE%'
    required: true
  format:
    label: 'Video format code'
    widget: 'textbox'
    position: 20
    category: 'videoformat'
    flag: 'format'
    required: false
  all-formats:
    label: 'Download all formats'
    widget: 'checkbox'
    position: 20
    category: 'videoformat'
    flag: 'all-formats'
    required: false
  prefer-free-formats:
    label: 'Prefer free formats'
    widget: 'checkbox'
    position: 20
    category: 'videoformat'
    flag: 'prefer-free-formats'
    required: false
  merge-output-format:
    label: 'Output format if a merge is required'
    widget: 'dropdown'
    position: 20
    category: 'videoformat'
    flag: 'merge-output-format'
    required: false
    widgetOptions:
      listSource: 'values'
      listValues:
      - 'mkv'
      - 'mp4'
      - 'ogg'
      - 'webm'
      - 'flv'
categories:
  videoformat:
    label: 'Video Format Options'
```

**position**: Every option/arg can have a position. This should be an integer. The higher the integer, the more left the option appears in the output
