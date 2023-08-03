
<table rules=none>
 <tr>
<td> <img src="https://i.imgur.com/GYIQg9q.png"></td>
<td> <h2><a href="https://joshjetson.github.io">Linux Your Welcome</a></h2><br>A Very Simple Linux Guide And Reference</td>
</tr>
</table>

**Demystifying Linux**

This is a repository dedicated to all things Linux and aims to act as a reference for popular and useful commands as well as crucial Linux concepts from A - Z. The material in this repo is delivered in a way that is friendly for the Linux confused, unaware, beginners - advanced users. If you read through the bulk of this repository you will know Linux.

## Deconstructed Learning System

- *Note: The Index in this document lists all sections.*

**Learning in steps based on the basics**
*Notice: How to install Linux is further down in steps. This is by design.*


1. [ ] [What is Linux ?](#what-is-linux-?)
2. [ ] [Learning The Linux file structure](#linux-file-structure)
3. [ ] [How do you navigate around a Linux system](#linux-navigation)
4. [ ] [What is a command ?](#what-is-linux-?)
5. [ ] [How do people install programs in Linux ?](#installing-applications-in-linux)
6. [ ] [How do you update Linux and programs installed in it ?](#what-is-linux-?)
7. [ ] [What are some differences between Linux, Windows and MacOS ?](#what-is-linux-?)
8. [ ] [Why do people use Linux ?](#what-is-linux-?)


## The Index

(click on the thing to jump to the thing)

<a href=""></a>

- [Assumptions](#assumptions)

## Who is this repository for ?

- Someone new to Linux
- Someone not new to Linux 
- Someone that just wants a reference to a bunch of useful Linux stuff and commands.
- Someone confused about Linux
- Which means this repository is for anyone interested in either learning about Linux/Linux commands or simply anyone wanting a kind of cliff notes or (reference/one stop shop) for a bunch of different Linux commands, principals and concepts.

*There are many explanations in this repository to either introduce you to concepts or clarify them in a calm simple way. 
- Your Welcome.* 



## Assumptions

These are things this repository assumes or assumes you could just google really quick.

- You know how to read
- You know what google is
- You know what a computer is
- You know what a hard drive is
- You know what computer memory is
- You know what computer hardware refers to

## Terminology Definitions

- **Source Code:** The entire programming code used to build a software technology. In the case of Linux most of it is coded in the C programming language.

- **Protocols:** A set of agreed upon rules and procedures specific to how computers interface and communicate with eachother. 
> **Some examples:** *HTTP, FTP, DHCP, IP, DNS, Telnet, SSH. You can google what these things are but suffice it to say Linux and other operating systems makes use of them.*

- **Services:** Programs running in the background that take care of different things like communicating with resources, controlling protocols, keeping track of the date and time, managing all the running programs or processes in the system, creating or managing daemons.

- **A Process:** A running instance of a program but also the smaller parts of a program that are running which the larger collective program needs in order to either keep running or run in a healthy state.
> **In Linux processes come from three main places.**
> - The user (*The bulk of the systems processes come from the user cause the user be running mad programs and what not.*)
> - A daemon
> - The Linux Kernel

- **The Linux Kernel:** The code and brains of the operating system that makes a Linux system a Linux system. It contains all of the instructions and logic for the operating system to work the way it does. If you consider all of the terms in this section and what everything is, the kernel has the instructions on how to work with them and manage them and bring them to life so someone could use them all. 

- **Daemon:** Is really a subset of a service which needs a service to run or needs to be told to run by a service at which point then runs in memory and waits to do stuff once it gets instructions. These instructions are called "Requests"

- **A Server:** A computer which hosts services, an entire operating system and or resources and then allows them to be accessible by utilizing some kind of protocl either locally or remotely. Meaning you could either access the computer and the stuff on it through your local home network or through the internet depending on how you set it up. 

- **Resources:** Hardrive space, installed memory, the CPU, the wireless card, the ethernet adapter, things plugged into the computer keyboards, thumb drives etc.. 

- Policies:

- Schedulers

## What this repositories goal is

#### There is a huge barrier to getting started using Linux or just finding out what the the heck it is and what its used for.

**Examples of barriers to entry**

- Linux/Linux command documentation assumes you already know how to read , understand and apply its contents.
- Linux command documentation often does not provide real working examples of how to use each command flag.
- When command examples are given they often look very different when you use them yourself in comparrison to the examples. 
- There is no one stop shop that answers almost everything needed to get started with Linux worded in a simple every day kind of speech broken down step by step.

This repo can help clarify some of the following questions and concerns as well as the above barriers to entry.

- You dont know where to start
- What is Linux in the first place ?
- Why does anyone use Linux ?
- <a href="#what-is-a-shell-?">What is a shell ?</a>
- What is a distribution of Linux ?
- Which distribution should you choose ?
- Which shell should you choose ?
- What is a command flag ?
- What is a man page ?
- Is everything in Linux command based ?
- How do you install Linux and what are some options available.



## Where to start

- Watching videos about Linux and what it is and what its used for to get a general overview of things.
> - Watching videos is not the best way to go in my opinion because learning Linux is very much about being able to read and understand what your reading.
> - If you dont have patience to read. You will for sure have a very difficult time learning Linux and your likely going to quit fast. 

*In other words just start here by reading on. I keep things as simple as possible while still getting into a descent amount of detail.* 

**Here is my recommended structure of how you should learn Linux:**

<span style="color:red">Start with the steps in my  Deconstructed Learning System <-- (click)</span>
Once you make it through the basics move on to things below that you have not learned about yet or just learn the below right from the jump if you don't like to approach things in steps.

> (*Keep in mind all of these things are answered here and you could just click on the thing to jump to a breakdown of it.*)

**Learn :**

- What is Linux
- The Linux file heirarchy structure first and what different directories are used for.
- What is a boot loader.
- What is a partition.
- How to access a terminal and start a shell session.
- About different user priveleges.
- What sudo is used for.
- What a sudoer is.
- What root means and who the root user is.

> ###### In a shell by using commands:
> > - What a command flag is and how to use them.
> > - What a man page is and how to access one and effectively read them.
> > - How to change directories, create a file and directory, remove a file or directory.
> > - How to view the contents of a file.
> > - How to edit the contents of a file.
> > - How to rename a file or folder.
> > - How to know which working directory you are in and what is a working directory ?
> > - How to move a file or folder to a different place.
> > - How to copy, cut and paste a file or folder.
> > - How to view the history of all the commands you have ever used.
> > - How to update your system.
> > - How to set your default applications.
> > - How to create, give a password and home directory to a new system user.
> > - How to change file and folder permissions.
> > - How to make something executable.
> > - The export command.
>

- What is systemd and systemctl as well as the service command.
- The different types of Linux file systems.
- About hidden files and folders in Linux and what their purposes are.
- About the Linux kernel.
- How to update/upgrade your kernel.
- What is the mkinitcpio command used for and what is the initrd and the initramfs.
- About package management and different package managers.
- How do you install a program in Linux ?
- What is PATH?
- What are Linux repository mirrorlists ?
- About different shell types.
- About different editors.
- About different user, system, and application configuration files as well as where they are located.

<a id="what-is-linux-?"></a>




## What is Linux ?

Linux is an open source operating system based on an older proprietary operating system called Unix.
> Some dood came along one day and thought wait.. this Unix OS thing should be free, im gonna work on that!
> And thus Linux was born. The doods name is Linus so he combined his name with Unix and presto we got Linux.

**Operating system:**

- A compilement of software tools, protocols, services, resources, policies, schedulers, advanced features, file/folder structures etc.. 
- Used to control and make use of all of the features your computers hardware has available to it.

**Open source:** 

- Anyone can view the entire source code used to create a Linux operating system and effectively create their own flavor of Linux. 
- It is free to do whatever you want.

## Why do people use Linux ?


There is not one answer to rule them all but here are five reasons along with a couple of examples.

#### 1. Free and open source stuff


Linux is free and most applications or pieces of software that run on Linux are open source and free as well.
Linux provides simple ways to find a similar, many times better, open source version of popular paid software using some kind of package management tool or git.
The vast majority of the time these open source programs can read and output files in popular formats such as .psd, .docx, .xls, .ppt etc..
What this means is that you are not limited to being confined by a paid program like photoshop simply because it outputs files in .psd format and your coworkers need that file format for a specific project.
Open source also means that people are constantly going to be working on this thing and making it better.


A few examples:

- Adobe Photoshop vs The Gimp Image Manipulation Program
- Microsoft Office vs Libre Office
- Microsoft Outlook vs Thunderbird
- AutoCAD vs LibreCAD
- Autodesk Maya vs Blender

#### 2. Programming / Developing

You can be a developer and use just about any modern operating system. Linux just makes it a little bit easier for specific languages like C, verilog,  java, python, javascript, nodejs and many others.
What I mean is that out the box many flavors of Linux either already come with enviornments set up to get started programming quick or have the ability to set up the enviornments quickly and seemlessly.

#### 3. Security

Linux enviornments are really easy to make secure and out the box are much more secure than a windows enviornments.
Linux systems out the box are also a lot more secure from a user accidentally messing something up or damaging crucial system files.

#### 4. Hosting Services

You want to have the following for free:

- A web server / website
- A database
- Your own cloud network
- Your own email server
- Your own version of netflix
- Your own music streaming service
- Your own file server
- Your own version control system keeping track of who edited whatever work file simultaneously backing them up
- Your own whatever service you already pay for..

You can do all of that and so much more in a Linux system with a little bit of reading, a little bit of patience, a little bit of elbow grease and a little bit of trial and error.

#### 5. Customization

You dont like the way something looks or the way someting is behaving.
You can easily change it in Linux.
The entire graphical user interface or command line interface can be completely customized to how you want it to look. You can make simple changes or crazy drastic changes you never knew were possible. 


#### One personal reason for using Linux framed the way I think. (Keep in mind im a python developer)

> - I have a bunch of older laptops that I dont want to throw away and I want to continue to get use out of. 
> - If I install windows on them they become unusable because everything takes a very very long time to run.
>
> ###### So what are my options ?
>
> ##### Linux is lightweight
>
> - Meaning it doesnt take up a whole bunch of space on a hard drive if you install it. Even a hard drive thats only 20 gb large could work for a Linux install. 
> - Linux manages a computers working memory really well so it doesnt stay stuck loading something for a long time.
> - The applications that run on Linux are also small in size so you can install many of them without needing a big hard drive. 
> - Linux applications are not resource heavy so Linux has an easier time running them.
>
> ##### Alright so I install Linux and now all these machines are usable and some how magically run really fast.
>
> - Cool so now I have all of these revitalized machines. 
>
> ##### What am I going to do with them ? I have three. They are all laptops.
> ##### Well.. I have always wanted my own website. 
>
> - I dont want to pay for a website and I dont want to host my files on some server somewhere that is just running Linux anyways.
> - Ill use one of the three machines, the most powerful one, as a webserver, cloud server and media server. 
> - The second most powerful machine I will use to code on. Im a python developer so that will be useful.
>
> ##### Ok from all of this coding sitting down for too long hurts my back so ill create some kind of a way where I could either sit or stand at my desk.
>
> - Sitting and standing is cool but sometimes I wish I could lay down and get work done also. 
> - If I could switch between the three work modes, sitting, standing and laying, I bet I could be ultra productive.
> > Idea !
>
> - Ill use the third remaining machine to set up some kind of bed programming situation where I have the machine rigged in such a way that I could code while laying down in my bed. 
> - I will also make sure that this laptop is easily detachable so I could use it as my mobile work station also.
> 
> ##### Cool all that worked ! Now im ultra productive.
>
> > ##### Its getting a little annoying sending files that im working on back and forth from each machine. 
> 
> > Ah I know ! Ill use my main server also as a git server hosting all of my work files securely. 
>
> - When I make changes to something its all managed and sent to one place. 
> - Git is cool too because if I mess something up I can just roll back the changes to a previous time. 
> - If I want I could also invite others to work on a project and just create a seperate user accounts for them on my server.



## What is a shell ?
A shell is a Linux command line interpreter. What the hell does that mean ?
It means that Linux has a bunch of specific words called commands that are used to make the operating system do stuff and a shell is a program that understands those words or commands and can make use of them.
Shells also have built in programming languages which let you write "scripts" you can run to do more stuff or automate things. 

## What is a terminal ?

A terminal is an application or piece of software that allows a user to interact with a shell.
There are a lot of different kinds of terminals that either specialize in a specific thing or allow you to customize the way you interact with a shell. 
You could do all of the regular stuff your used to doing on a computer inside of a terminal.
Terminals along with command line shells are an explicit way of interacting with your computers operating system.
Clicking around using your mouse or trackpad is an implicit way of interacting with your computers operating system. 
When you click around and create a file or edit a file or open a program your computer is actually running all these commands in the background.
This means if you wanted to you could just type the commands into a terminal directly.

**How do you find or access a terminal in Linux ?**

One of these will do it.

- Hold the CTRL+ALT+t keys

- Click the start menu and type term in the search bar and then choose "Terminal Emulator" or "Xfce" or "Alacritty" or anything that has a desription of terminal emulator or has term in the name should work.
<img src="https://imgur.com/qHu1vIt.png"></img>

**Which terminal should you use ?**

It doesn't really matter. Once you get more into Linux you play with different terminals and start to like certain ones for specific reasons such as:

- Its easily customizable
- The configuration file is not annoying
- It starts up fast and exits fast
- It has things like tabs for multiple sessions. (A sesssion is just an instance of a shell)

Honestly, its not too tricky to customize any terminal. Any will do.

## What is a man page ?

<img src="https://imgur.com/9YITDn0.png"></img>

## What is a command ?

A command is a word/term that is a reference to an application, a serrvice, a protocol, a feature installed or accessible in your operating system which invokes/creates some kind of action.


*Please see the following related material*

- What are commands flags ?
- What is a shell ?
- What is a Terminal ?

**Where do you type commands ?**

[ ] You type commands in a terminal.
[ ] A terminal will give you access to a shell which will be the thing that knows how to understand the commands you type in the terminal.

## What is a command flag ?

A command flag is a thing you type after a command that makes the command behave differently.
We are going to use the ls command as an example.

The ls command: ls is short for the word "list". 
The ls command shows you a list of files and folders in whatever working directory you are in.

If I type the command "ls" in a terminal like this and then press enter.

```sh
> ls

```

This is the output of that command.

<img src="https://imgur.com/mzwLRkK.png"></img>


*You see! In the terminal I now have a list of files and folders relative to the directory im in, which in this case is my home directory.*


Alright cool. Now lets try using a command flag with the ls command.

``` sh
> ls -a

```

<img src="https://imgur.com/ayHMyGc.png"></img>

*You see! For the ls command the -a tells the command to list all files and folders even the hidden ones. This is an example of a command flag and it changing the behavior of a command.*

Commands usually have a ton of different command flags.

Ok so how do you find command flags for a specific command though ? 
You could usually type the command name in a terminal followed by a space and either --help or -h, alternatively you could also type "man ls" or "man 'Command_name_here'" without ANY of the quotes.
Unfortunately documentation is really annoying for a beginner and you dont learn till later that you werent suppose to type the command with the brackets or the quotes or something else.
There is also a lack of real world examples in documentation and they just kind of assume that you could figure it out. You could always ask google something like " real examples of the ls command ".
I also am doing the best I can to de-mystify things in the realm of this idea here in this repo so hopefully you could just find your answer here.

## What is a Linux distribution ?

It's just a unique version/flavor of Linux that people made.
Like ice cream anyone can source the ingredients of Linux and make their own flavor.
Most distributions of Linux are not too different from each other and if you learn how to navigate around one you can without too much difficulty figure out another.

Here is a small list of what different distributions might be tailored towards:

- Ease of use
- Security
- Customization
- Development
- Web Server
- Lightweight (small in size)
- Community
- Package Management (Software management)
- Business
- Running on mobile devices

Here is a small list of some actual distributions:

- Arch Linux
- Manjaro Linux
- Debian Linux
- Ubuntu Linux
- CentOS Linux
- RedHat Linux
- Suse Linux
- Gentoo Linux
- Fedora Linux

Some distributions of Linux are built off of other distributions.

Ex.
Ubuntu is built off of Debian
Manjaro is built off of Arch
Fedora is built off of RedHat

Here are a few examples of what certain distributions are geared towards and why.

- Arch Linux is geared towards people who want more control and customization options in a lightweight form factor.
This means that out the box Arch does not come with a whole bunch of stuff and is more bare bones.
It installs with less packages than a distribution like Ubuntu and you have to manually configure more things out the box then you would with a distro like Ubuntu.

- Manjaro Linux is geared towards developers. So a group of people liked the lightweight nature of Arch and thought, 
hmm thats cool lets use that as a base for a new distro with a bunch of tools added
for programmers.

- RedHat Enterprise Linux is geared towards individuals or businesses that want to pay for support.
It has a lot of tools out the box to set up different kinds of server enviornments.
RedHat is used by a lot of larger companies that provide some kind of web service.
Which makes sense because if something goes wrong they can just call someone for help and get support
for different features of the operating system whenever they want. 

- Fedora is basically RedHat but its community supported instead. So it has all of the features
of RedHat minus the on demand support. This means that if you need help you have to fish around in 
a forum somewhere reading posts from people who have sorted out similar issues or it means
your going to have to ask people in a forum somewhere for help.

- Ubuntu has many sub Ubuntu flavors and is generally geared towards ease of use in all matters from how a user installs Ubuntu, to how a user sets up different server enviornments. 
Ubuntu out the box comes with a bunch of software packages and in that sense
is more robust in terms of what it has installed right out the gate. 
This also means that Ubuntu has more services running straight away when compared to an Arch based system 
and it may require more resources because of all of its services and software packages.
This also means that out the box there may be a bunch of things you either dont need or dont want.

## Which distribution should you choose ?

Answer these questions first.

- Why are you at all intersted in Linux ?
- Do you have an extra computer you dont use ?
- Do you not want to use another machine to install Linux ?
- Do you know how a virtual machine works ?
- Have you heard of windows subsystem for Linux and does that idea appeal to you ?
- Do you want to learn in detail how Linux works or do you just want it to more or less work after you install it ?

**My Linux Journey for context**
I started using Linux in 1997 for no good reason other then I was and am still obsessed with computers.
The first distribution I used was called Slackware which is currently the oldest distribution still maintained.
It was very hard for me. I had to read a ridiculous amount just to do simple things that I could do on windows willy nilly.
The community was not nice. I would go on to forums and ask questions and everyone would say the same thing RTFM!
Which means Read The F'ing Manual. 
The pros are I did end up reading the f'ing manual and as a result I learned a lot.
The cons are I wasted so much time going down the wrong path on many occasions but when your 14 you have time.

So look. If your new most people recommend Ubuntu or a Debian based distro.
Im a Arch guy now, well Manjaro to be more specific. Im a programmer and I have old computers I want to still use for stuff.
With Manjaro, sure I need to already know a fair amount about Linux but since I do its not a problem for me.

I dont know your situation or your personality I also dont know what you have to work with.
If you have some old pos laptop or desktop your not using and are new to Linux maybe try Lubuntu.
If you want to immerse yourself in pain and frustration but then come out the other end with a better understanding of Linux than your standard Ubuntu user maybe try Arch.
If you run windows and maybe just want to play around with command line stuff you should install the Windows subsystem for Linux in your Windows enviornment.

## Which shell should you use.
If your new to Linux or havent been using it for too long. 
I recommend [Zsh](https://github.com/ohmyzsh/ohmyzsh/wiki/Installing-ZSH).
Then I recommend installing [Oh-My-Zsh](https://github.com/ohmyzsh/ohmyzsh/wiki/Installing-ZSH)
Then I recommend installing [Powerlevel10k](https://github.com/romkatv/powerlevel10k) and configuring it the way you like it.


## Configration files

## Defaults


## Logs
.bashrc
.zshrc

## Sources
exporting stuff

## User related

## Git related

Show if your local repository is up to date ahead or behind a remote repo.

```sh

git remote update

```

then

```sh

git status -uno

```

## Linux Server Security Related

Fail2ban



## Text Editor Related

**Nano**

**Vim**

If you want to learn Vim through a playing a little game.
[Here you go.](https://vim-adventures.com/)


Copy to clipboard

Enter visual mode
Highlight the text

```
\ + y
```

to copy
to paste 

ctrl + shift + v
or
ctrl + alt + v

**Nvim (*Neovim*)**

*Same as vim just looks cooler with a few more features*

**Spacevim**

*Vim/Neovim on crack!*


## Scheduling related
crontab


## Remote Related (Computer to Computer, Local and Non-Local)

### Rsync

### SSH Related

#### Generate an ssh 4096 bit encrypted rsa key

> What ?
> - A special key used for secure communication between local and remote machines.
> Why ?
> - To make communication more seemless while still protecting the process.

> Ex.

```
ssh-keygen -b 4096
```


#### Copy ssh key to a remote machine

> What ?
> - Authorizes a remote machine allowing it to login without entering a password
> - Adds a trusted key into the authorized users file in /home/username/.ssh/authorized_keys
> Why ?
> - So you do not have to keep typing in your password when your sshing into a remote machine.

> Ex.

```
ssh-copy-id -i ~/.ssh/id_rsa.pub username@192.168.5.38
```


## Docker Related


## Hardware Related

## Network Related


## File and Folder Related

> File and folder permissions.
- What the hell are they and what are they used for ?

**Ranger**

#### Compressing and decompressing files

#### Searching for or in files

#### Searching for or in folders


#### System related

#### Web Server Related

**Apache**

**Nginx**

#### Cool useful commands

Neofetch
ttyd
asciinema
xfce4-screenshooter
