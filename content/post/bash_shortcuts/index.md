---
title: Bash Shortcuts
subtitle: 
summary: 'When working in the terminal, the mouse is usually not very useful. Here are a couple of useful shortcuts when working in the terminal.'
authors:
  - admin
tags: ['Tools','Linux']
categories: []
projects: []
draft: false
featured: false
share: false
date: '2023-11-28T00:00:00Z'
lastMod: '2023-11-28T00:00:00Z'
image:
  caption: 'generated by DALL-E'
  focal_point: ''
  preview_only: true
---  

Today's blog post will be a short one. 
When working in the terminal, knowing some keyboard commands can be a huge help.
Keyboard shortcuts save your time (and your sanity).

Here is an overview of the ones that I use most regularly. Some of them are pretty obvious, others might be less common.

## Useful commands

| Shortcut | Effect |
|:-------:| ------------------------------|
|`ctrl+c` |Interrupts the currently running program (in the foreground)|
|`ctrl+d`| End of the input.  `cat` and `wc` will go to work after this if they were started without further arguments.  If ctrl+d is pressed directly in the shell, the shell will terminate.|
|`ctrl+r`|Reverse search. If you type `ctrl+r` the history will be searched for the string typed afterwards.  By typing the `ctrl+r` again the next occurrence will be displayed.|
|`ctrl+g`| Terminates the reverse search.|
|`ctrl+o`| Executes the current command and enters the next command in the history in the prompt. This is especially useful when executing several commands from history in a row.|
|`ctrl+z`| Suspends the current foreground program. For details about jobs and fore-/ background jobs see below.|

### Jobs in the background
Job control in the linux shell amounts to be able to interrupt and resume commands (aka jobs).
Usually, when a command is executed in the shell, it locks the shell and no further commands can be executed until it terminates.
Sometimes this is quite annoying, especially, if the command is long-running and rather boring.
Linux supports to run commands in the foreground and in the background.

By adding an ampersand character `&` after the command, the command starts in the background.
While `sleep 100` blocks the terminal for 100 seconds, `sleep 100 &` runs in the background and does not disturb anyone.
But what if we forgot to type the ampersand character with the command?
Don't despair. That's the job of `ctrl+z`. It suspends the job and gives you back the terminal prompt.
By executing `bg`, you can send the job to the background, problem solved.

To get an overview of currently running jobs, just type `jobs` and have a look at what is running.

## Movement commands
Sometimes, you have to correct a command line or just want to move the cursor around.
These commands make moving the cursor a piece of cake.

| Shortcut | Effect |
|:-------:| ------------------------------|
|`ctrl+a`|Jump to the start of the command|
|`ctrl+e`|Jump to the end of the command|
|`ctrl+k`|Delete the rest of the command behind the cursor|
|`alt+b`|Jump one word back|
|`alt+f`|Jump one word forward|

As you might have noticed, these are the same commands as are used in `emacs`. 
This is not by accident. 
The default setting of most terminals is `emacs` mode.
There is also `vim` mode which introduces the difference between 'normal' and 'insert' mode to the terminal.
I, personally, find that more confusing than useful although I use `vim` for editing whenever possible.
And yes, this post is written with `vim`.