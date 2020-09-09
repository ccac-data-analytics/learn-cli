Intro to the Command Line
=========================

## Assumptions: 
1. If you're on Windows, you have downloaded and installed Git Bash (which comes with [Git for Windows](https://gitforwindows.org/)). If you're on a Mac or Linux machine you won't need to bother&mdash;you already have a Linux-style command line interface.
1. You've gone through [this deck](https://docs.google.com/presentation/d/14oisMTEG-O-_DnHSfBRCLsuRq041VnJt9qFOAiVhdpI/edit?usp=sharing), ideally with an instructor or at least on your own.

## Reminder:
* **Don't type the &gt; that appears before commands.** That just indicates the existence of the command prompt.

## Getting started and finding our bearings
1. **Windows:** open Git Bash.<br />**Mac:** [open Terminal](https://support.apple.com/guide/terminal/open-or-quit-terminal-apd5265185d-f365-44cb-8b09-71a064a42125/mac)<br />**Linux:** open your terminal, which might work with ctrl-alt-T, or you might have to go searching for it 
1. Usually, the terminal will open up at the home directory for the user who is using it, but let's be really sure:<br />
```> cd ~``` &lt;- this says "change my working directory to my home directory"; **remember not to type the &gt;**
1. Now, let's see where home is:<br />
```> pwd``` &lt;- this stands for "print working directory"<br />
On my CCAC Windows machine, what prints is ```/c/Users/csheldon-hess/```; yours will be different depending upon your username, your operating system, and how you've got things configured. That's fine. But **you will need to know where your home directory is (write it down if you think you'll forget) and that ```cd ~``` is the shortcut to get there.**
1. Is your username part of your home directory? Let's find out what your username is, shall we?<br />
```> whoami```<br />
For me, the output was ```csheldon-hess```, which is, indeed, part of my home path. 
1. What else is here? <br />
```> ls```  &lt;- this lists the contents of the directory<br />
This should give you a list of all of the files and directories inside your home directory. But we can add flags! <br /> 
```> ls -ahl``` &lt;- this lists them, even the hidden files(!!), with a LOT more details<br />
Fiddle around with the flags until you get a version of ```ls``` that you like. Git Bash is a pretty friendly command line interface, with color-coding for different types of files, so I'm generally pretty happy with ```ls -a``` &mdash; unless I need to know file permissions for some reason, in which case I pop the ```l``` back on.

## Getting some files we'll need
Now we're going to take a quick break from the command line. Using the browser of your choice, visit [the GitHub page that goes with this lesson](https://github.com/ccac-data-analytics/learn-cli) and **click the green button on the right hand side of the screen (it shows a downward-pointing arrow and the word "Code"), and then choose "Download ZIP."** Go ahead and save it; it doesn't matter too much where the zip file goes, but I want you to **unzip the file, and save its contents into a directory named "learn-cli" that sits in your home directory.** In my case, I had everything saved into C:\\Users\\csheldon-hess\\learn-cli, like so:

![a screen shot showing learn-cli directory inside Windows Explorer; it has a subdirectory named "text_files," a docx file, and a file named README.md](http://sheldon-hess.org/images/learn-cli.png)


What you want to happen is that, when you go back into your terminal and type ```ls ~``` , there is a new directory there called "learn-cli" &mdash; if this isn't what happens, hit me up on Slack, and we'll talk through it. 

Assuming that happened, let's explore the ```learn-cli``` directory!

## Exploring, moving around, and making new things
1. You're still probably hanging out in your home directory. Cool, let's say you want to stay there, but you also want to see what's in ```learn-cli``` &mdash; not a problem!<br />
```> ls learn-cli``` &lt;- that's right, you can ```ls``` a different directory than you're currently working in! <br />
Note: you used a ***relative path*** for that. You could do exactly the same thing with an absolute path: <br />
```> ls ~/learn-cli``` 
1. ```learn-cli``` has another directory inside it, called ```text_files``` &mdash; to look at that, you can just tack the subdirectory onto the previous command. **But don't type the whole command! Hit the up arrow on your keyboard.** That will bring up your previous command, and you can **add ```/text_files``` to the end of it** (the full command, then, will be ```ls learn-cli/text_files``` or, if you tried that absolute path up there, it'll be ```ls ~/learn-cli/text_files``` )<br />
**The up and down arrows let you scroll through your command history.** This saves a lot of typing!
1. While we're talking about saving time and typing, do yourself a favor: type the following **but don't hit enter yet:**<br />
```> cd lear``` **now hit tab**<br />
It should have autocompleted to ```cd learn-cli/``` and you can hit enter now. Your working directory is now ```~/learn-cli``` &mdash; if you try ```ls``` in here, you'll see the same things as you did when you listed the contents of this directory from outside of it.<br />
That trick is called **tab completion,** and it serves two purposes:
	1. It saves typing, of course. Really handy when you're dealing with long filenames.
	1. It also serves as an error check. Type the following:<br />
	```> cd lea``` and then hit "tab" - it honks at you and doesn't auto-complete, right? That's because there is no ```learn-cli``` directory inside the ```learn-cli``` directory! <br />
	Go ahead and delete that command.
1. Now, let's say we want a new file in this directory. Not a problem. We'll use the command ```touch``` to create the file. (There are other ways.)<br />
```> touch birds_rock.txt```<br />
```> ls``` <br />
Notice that there is now a file called "birds_rock.txt" in this directory.
1. If we wanted to create an entire new directory, also not a problem. We'll call it "temp_dir":<br />
```> mkdir temp_dir```<br />
```> ls```<br />
Now we have our new file, "birds_rock.txt" and our new directory, "temp_dir"
1. I just want to remind you, here, that you can navigate up and down directories with relative pathing: <br />
```> cd temp_dir``` &lt;- takes you into that nice new subdirectory <br />
```> cd ..``` &lt;-brings you back up into ```learn-cli```

## Copying and moving things from one place to another
1. What if we want "birds_rock.txt" to be in two places? **We can create a copy of the file in the same directory with a different name:** <br />
```> cp birds_rock.txt birds_rock_copy.txt```<br />
```> ls``` &lt;- just to confirm that we have birds_rock.txt _and_ birds_rock_copy.txt in this directory<br />
1. **We can also create a copy of the file in a different directory (with any name we want):** <br />
```> cp birds_rock.txt temp_dir/birds_rock.txt``` &lt;-creates a copy _with the same name_ inside the temp_dir directory<br />
```> ls temp_dir``` &lt;- just to confirm that happened :) <br />
```> cp birds_rock.txt temp_dir/birds_rock_temp.txt``` &lt;-creates a copy _with a different name_ inside the temp_dir directory<br />
```> ls temp_dir``` &lt;- just to confirm that happened, again :) <br />
1. Maybe unsurprisingly, we don't only have to reach _down_ the directory structure to create new files. We can also move _up_ the hierarchy. To keep your machine clean, though, let's change directory first: <br />
```> cd temp_dir```  &lt;- now we're in ~/learn-cli/temp_dir <br />
```> ls```  &lt;- just remind ourselves what's here <br />
```> cp birds_rock_temp.txt ../``` &lt;- puts a copy of birds_rock_temp.txt into ~/learn-cli <br />
That's right. If you aren't going to change the name of the file, you don't have to retype it when you're making a copy into another directory! (I usually do anyway. It doesn't hurt to be extra explicit with your directions when dealing with a computer.) But go ahead and confirm that it worked: <br />
```> ls ..```
1. All right, so we know how to copy things, which is great when we want the same thing in two different places. Sometimes, though, we just want the same thing, in a different place. In the CLI, **the move command (```mv```)** does what we think of as two different things in a GUI like Windows:
	1. it moves files from one directory to another
	1. it renames files
Let's say we want to rename the file "birds_rock_temp.txt" that we just moved into ```~/learn-cli```:<br />
```> cd ..```  (we could have skipped this; what would the next command look like, if we did?) <br />
```> mv birds_rock_temp.txt birds_really_rock.txt``` <br />
```> ls```<br /> 
There should now be a file named "birds_really_rock.txt" and NO file named "birds_rock_temp.txt" inside of ```~/learn-cli```.
1. Now, let's move "birds_really_rock.txt" into our temporary directory: <br />
```> mv birds_really_rock.txt temp_dir/```<br />
```> ls```  (it's gone from this directory, yes?)<br />
```> ls temp_dir``` (it's in there, yes?)
1. Moving directories works the same way as moving files. We're still working in ```~/learn-cli``` for this:<br />
```> mv text_files great_texts``` <br />
```> ls```  (to confirm the name changed) <br />
```> mv temp_dir great_texts/```  <br />
```> ls``` (is temp_dir gone?)<br />
```> ls great_texts``` (is temp_dir inside great_texts?) <br />
Now, let's actually put it back, shall we?<br />
```> mv great_texts/temp_dir .``` &lt; I mentioned that ```..``` points at the directory above your current working directory, yes? _well,_ ```.``` points at your current working directory; you don't use it often, but here's a case where it makes sense.

Now.

Before we move on to deleting files, I have something important to tell you:

## Nobody who tells you to type ```rm -rf``` has your best interests at heart.<br />
Never type that.

(There are exceptions. I've done it, for legitimate reasons. But I was **extremely careful** and, between you, me, and the 40 million other people who use GitHub, I was also _fairly anxious_ about it each time. ¯\\_(ツ)_/¯) 

## Removing files and directories
1. The command to remove a file is ```rm```. Let's say we want to get rid of one of the files we made a copy of, earlier. There should still be a file called "birds_rock.txt" inside of ```~/cli-files/temp_dir```. Like any of these other commands, we can pass an absolute or a relative path to the file we want to remove. So, assuming we're still working in ```~/learn-cli``` we can do <br />
```> rm temp_dir/birds_rock.txt``` (or, if we're elsewhere, we can fully specify the path: ```rm ~/learn-cli/temp_dir/birds_rock.txt```)
1. The command to remove a directory is **not,** as you might imagine, the same as the command to remove a file. It is its own special command (which you can type, but it won't do anything): <br />
```> rmdir temp_dir``` &lt;- this won't work because there are files in there<br />
We could force it with the -f flag. But that's a little risky. The way I'd do it?<br />
```> ls temp_dir``` &lt;- remind myself what's in here and confirm I don't need any of it<br />
```> rm temp_dir/*``` &lt;- use a **wildcard character** to remove all of the files in the directory<br />
```> rmdir temp_dir``` (and now, it should work, because it's an empty directory!)<br />
And **that is it, it's gone &mdash; there is no Recycle Bin on the command line, no way to undo removing a file or directory.** So we do these things only with great care. (And, in this case, I mean, it was the plan all along; that's part of why I called it "temp_dir" from the start.)

## TODO:
* less
* cat
* head
* tail
* ctrl-c
* nano
* find
* grep
* &gt;
* |