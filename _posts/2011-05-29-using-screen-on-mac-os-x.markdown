---
layout: post
title: Using Screen on Mac OS X
description: Screen is a simple tool for managing your terminal windows. Here's a simple tutorial for getting you up and running.
keywords: screen,gnu screen,os x,terminal management,using screen,screen how to, using screen on os x,maintain terminal state,terminal long running processes
change_frequency: monthly
---

For the last week, I have been using GNU Screen to help me manage my terminal windows. Although there is a slight learning curve with Screen, there is one major advantage that more than makes up for the extra effort.

Suppose you want to SSH to a computer, start some long-running process, and not have to worry about keeping the connection open for that process to finish. Wouldn't it be great if you could just reconnect later and not only check on the progress, but also have all of your terminal windows in the same state as how you left them?

Here's a similar scenario that I ran into recently. Suppose you're running a script in the background that monitors a folder and compiles CoffeeScript files into JavaScript as the files change. If you simply ran the script from the terminal, the script would need to be restarted every time you closed the terminal window. What if you could start the script once and know it's still running in the background even if you've opened and closed the Terminal application many times since the script was started?

Screen is able to solve both of these problems simply and elegantly. Now, if I ever accidentally close the Terminal application or get disconnected over SSH, the state of all my windows and processes will remain the same. To me, that's a major selling feature.

Is Screen right for you? Here is a simple guide to get you started quickly and help you decide if it fits your workflow.

### Getting Started

To get started, simply type `screen`. The first thing you will see is the startup screen, which you can dismiss by pressing either space or return. I explain how to disable this screen later in the article. 

What you see afterwards should look very familiar. It's the same exact terminal you're already familiar with. However, you now have many different options that weren't available before. To see a list, you can view the help by pressing `Ctrl-a ?` (control-a followed by a question mark).

### Creating and Naming Terminal Windows

Screen provides a couple useful ways of managing multiple terminal windows.

While in screen, type the command `Ctrl-a "` to see a list of open terminals. Currently, you should only have one terminal open, with the number 0 and a default name of the shell you are using. In my case, this is bash. Press enter to go back to your terminal. To rename this terminal, type `Ctrl-a A`. You should see a prompt appear at the bottom asking you to give the window a title. Call it Terminal 1. If you press `Ctrl-a "` again, you should see the terminal listed by the title we gave it.

Now, let's create two more terminals and give them different names. The first way to create a new terminal is by typing `Ctrl-A c`. Rename it one more time by typing `Ctrl-a A` and calling it Terminal 2. You should now be able to type `Ctrl-a "` again and see both terminals. You can use the up and down arrow keys or j/k to move between them.

Now let's create one more terminal and name it at the same time. You can do this by typing `screen -t "Terminal 3"`. This will create another terminal named Terminal 3. You can check this by typing `Ctrl-a "`. 

You can also use the -t flag to provide a number for the terminal window. For instance, `screen -t "Terminal 9" 9` will create a new terminal window called Terminal 9 with a terminal number of 9. I will show you why this can be useful in the next section.

### Navigating Between Terminal Windows

There are a number of different methods for navigating between windows. One simple way is using `Ctrl-a n` and `Ctrl-a p`. This simply switches between the previous and next window. Another method is by selected `Ctrl-a [terminal-number]`. For instance, to navigate to Terminal 9 that we created earlier, you can simply type `Ctrl-a 9`.

You can also have more than one terminal window open at the same time. To do this, split the terminal window using `Ctrl-a S`. Once you have split panes, you can easily switch between them using `Ctrl-a [Tab]`. Once you are in the second pane, you need to select the terminal you want to see in that pane. You can do this using any of the methods described above: `Ctrl-a "`, `Ctrl-a n`, `Ctrl-a p`, or `Ctrl-a [term-num]`. If at any point you want to exit out of split-pane view, simply navigate to the pane you want and type `Ctrl-a Q`. If the other pane doesn't disappear right away, it should get overwritten as you keep using the terminal window or you can type `Ctrl-L` or `clear` to reset the screen.

One cool feature is that you can use these navigation tools even while you have other programs open within your terminal. Try this example: open up a couple terminal windows and open `vi` in one of them. You should be able to navigate back and forth between the different terminals without having to close `vi`.

### Detaching and Reattaching Your Screen Session

This is my personal favorite feature of screen. Type Ctrl-a d to detach from your screen session. You are now back to your standard terminal. Type `screen -list`. It should list that you have one screen session open. Type `screen -r` to reattach to this session. Once you reattach, you should see that all of the state of your terminal windows has been maintained. If you had more than one screen session open, you would have to provide the process id (PID) following `screen -r` to select which session you want to reattach.

It's important to note that you don't necessarily need to type Ctrl-a d to detach the screen session to use this feature. If you accidentally close the Terminal application while you have important work open (as I have done many times), you will still be able to reattach and resume your work if you were using screen.

### More Tips

#### Removing the Startup Message

To remove the startup message, add the following line to your `.screenrc` in your home folder:

`startup_message off`

If the `.screenrc` file doesn't already exist, simply create it.

#### Recognizing Different Sessions

If you want to run multiple screen sessions at the same time, it's important to have a better way to differentiate screen sessions than by PID. To do this, start screen by using the -S flag. For instance, `screen -S rubyterms` will start the screen session with the session name rubyterm. This name will be displayed when you type `screen -list` and can be used as an argument to `screen -r` to start it back up.

#### Knowing Where You Are In Screen

To view which terminal you are currently using, you can use `Ctrl-a i`. If you always want to see the terminal you are on and all open terminals by default, add the following line to your `.screenrc` file:

`caption always "%{= Wk}%-w%{= Bw}%n %t%{-}%+w %-="`

#### Setting Up A Startup Configuration

A couple more small edits to your `.screenrc` can make sure that a few default terminals are automatically created and named for you on startup. Simply add a few `screen -t` lines in your `.screenrc` file. Here is an example:

`screen -t "server" 1`<br />
`screen -t "logs" 2`<br />
`screen -t "ruby" 3`<br />
`screen -t "coffeescript" 4`

#### Exiting Screen

If you want to exit screen without detaching, you must simply exit all of the open shells by typing exit in each. After the last one is closed, screen will terminate.