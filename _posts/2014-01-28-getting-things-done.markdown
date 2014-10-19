---
date: '2014-01-28 23:17:24'
layout: post
slug: getting-things-done
title: Getting things done
categories:
tags:
- bash
- productivity
---

Sometimes it's difficult being productive. Procrastination can be a nasty problem. So, to help, I've made a simple script to keep me on track. It's much like the [pomodoro technique](http://pomodorotechnique.com/) but without all the excess theory and pretense. It's really just a command line egg timer that integrates with `tmux`, `mpd`, `libnotify`, `espeak` and any other custom commands you might like. It would not be difficult to extend its functionality either. The basic usage looks like this:

    USAGE:

       gtd [ -bcmnst ] [ work length ] [ break length ]

    OPTIONS:

       -b : start on a break
       -c : custom command (defaults to "clear")
       -m : toggle MPD on change
       -n : notify on change
       -s : speak command
       -t : show time in tmux status bar

The `tmux` integration really just updates a temporary file with the time remaining on the timer and refreshes your tmux session. You could use this in your `tmux` status bar like this for example:

    set-option -g status-right "#(cat /tmp/gtd)#[fg=colour15,noreverse,bg=colour233] #(date '+%a %m/%d %I:%M %P') "

This sets the right side of your status bar to the time remaining in the timer (if the timer is on) and then the date and time. You could just as easily read this into `conky` or [GeekTool](http://projects.tynsoe.org/geektool) (the OSX equivalent).

You can find the project [here](https://github.com/connermcd/gtd) and add any suggestions to the issue tracker. Hope it helps someone else!
