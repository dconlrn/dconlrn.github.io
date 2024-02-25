<p align="center">

<img src="https://imgur.com/VWqWfMh.png">

</p>


<h2 align="center"> A Quicker guide to Grails </h2>

<div id="top" align="center">
<p align="center">This guide initially follows the Grails documentation almost identically but then derails into a path intended to help you, not only build a more robust application in Grails quicker but also give you a rapid understanding of the structure of a Grails application from a birds eye view.</p>

</div>

<div align="center">
<b>Disclaimer</b>
<i>This guide is command line focused. <br>Meaning most of the time you will be doing things in the command line</i>

</div>

------------------------------------------------------

## Navigation

--------------------------------------------------------

- [Prerequisites](#prereqs)

- [Installation](#installation)

- [Creating a Grails Application](#app)



-------------------------------------------------

## Prerequisites

<div id="prereqs"></div>

*$ <- This dollar sign denotes a bash shell, meaning anything that follows it is supposed to be executed in a terminal aka command prompt, If you didn't know.*



- Java Installed
- JavaJDK installed, BUT! MUST BE JDK 11 or earlier latest JDK wont work for Grails.
> *So all routes to either install Java or make sure its installed and then the JDK 11*
> *All routes to making sure JDK 11 is your systems default*
> *Note: Most Unix/Linux based systems have Java and likely the JDK installed out the gate*

- On an Arch Linux setup I needed to *Remember this is for an Arch Linux system*:
> - Install an older version of the JDK, JDK 11
> `$ sudo pacman -Sy jdk11-openjdk --noconfirm`
>
> - Change the default JDK version used by the system
> `$ sudo archlinux-java set java-11-openjdk`

<div id="installation"></div>

----------------------------------------

## Installation



- Installation: (As per the Grails documentation)
- Use the SDKMAN, method it is the easiest
> Otherwise follow some other method through the documentation [Here](https://docs.grails.org/6.1.1/guide/single.html)

- Install SDKMAN

> `$ curl -s "https://get.sdkman.io" | bash`

- Source the sdkman init.sh

> `$ source "$HOME/.sdkman/bin/sdkman-init.sh"`

- Install grails

> `$ sdk install grails`

<div id="app"></div>

-------------------------------------------------------

## Creating a Grails Application

- Create a new folder/directory and name it as you like
> `$ mkdir myapp`

- Go into the new directory you just created
> `$ cd myapp`

- Create a new Grails app
> `$ grails create-app myapp --servlet=tomcat`
>
> The "myapp" part can be renamed to whatever you want your app to be, actually called.
> The `--servlet=tomcat` command flag part : (*Lets break this down*)
>
> - Tomcat is a web server that puts things into a container called a servlet.
> > This creates a smaller packaged environment which contains
> > all of the things needed for the application to run without 
> > pulling bulky resources from several different places.
> >
> > This concept drastically decreases the amount of time you
> > can get an application up and running while it is being developed.




**The Grails Interactive Console**

*Just in case you ever need to access it for whatever reason*
*Note:When you run this command make sure your in either a grails app directory or a place you want to make a new grails app<br>if you plan on doing anything useful that is.*

- Just type:
> `$ grails`

*From inside of the interactive console:*

- Get some help and a list of commands (Just type help)
> `$ help`

- Exit (Just type exit)
> `$ exit`

**Run a Grails app**


*In the same folder the gradlew file is located (Should be the root app folder)*

- Type the following:
> `$ ./gradlew bootRun`

- Run on a different port *(If needed for whatever reason)*

> `$ ./gradlew bootRun --D grails.server.port=9090`

**If all went well!**

> If all goes well you should be able to open a web browser
> and navigate to http://localhost:8080 or whatever port
> you used in place of 8080


**At a glance**

<p align="center">
<br><b>After you create a Grails app these files and folders get created</b><br>

<img src="https://imgur.com/fcwUGyQ.png">
<br>

</p>

**The bulk of your development in Grails**

> - Your work will largely be focused in the grails-app folder.


<p align="center">
<br><b>These are the folders inside the grails-app folder</b><br>
<img src="https://imgur.com/Da60kNo.png">
<br>

</p>

> > **To start simple**
> > **We will start by focusing on the:**
> > - **Assets Folder**
> > - **Controllers Folder**
> > - **Views Folder**

<p align="center">
<br><b>The assets folder</b><br>
<img src="https://imgur.com/gGPBkCd.png">
<br>

</p>

> **Contains what are commonly referred to as static files**
- **This is where you are going to put your CSS, JavaScript and Images associated with your application**
- **Grails is going to know to look here when you reference this stuff in your HTML/(.gsp) files**

<p align="center">
<br><b>This is how you reference your CSS in your HTML/(.gsp) files</b><br>
<img src="https://imgur.com/7hTmTbA.png">
<br>

</p>

<p align="center">
<br><b>This is how you reference your JavaScript in your HTML/(.gsp) files</b><br>
<img src="https://imgur.com/J2s4nRf.png">
<br>

</p>

<p align="center">
<br><b>The controllers folder</b><br>
<img src="https://imgur.com/886Bnju.png">
<br>

</p>

> **Controllers deal with**
- **Requests**
> - **This is where you can create logic responsible for handling data to and from the browser**
> - **Controllers render data that can be used in .gsp files through a language that is called "view tags" which we will get into later**

To create a new controller enter the Grails interactive console

```sh
$ grails


```

Then from inside the interactive console:

```sh

$ create-controller greeting

```
<p align="center">
<br><b>The views folder</b><br>
<img src="https://imgur.com/8lL43YB.png">
<br>

</p>

> **Views contains**
- All of your applications HTML inside of individual .gsp files
- To create a new .gsp file
- Go into the views folder and create a new file with the .gsp extension.
- Then add some html in it

**Layouts**

> The layouts folder inside of the views folder:
> - This is where you keep .gsp/HTML files which contain reusable code you want to be able to access in other .gsp/HTML files
> - The concept of the layouts folder is similar to the idea of HTML partials.


**Database Interaction**

(Still fuzzy on this need to work on this section later)

> Grails Domain Class:
- A way of creating data models which interact with a database.

- From inside of an interactive console

```sh
$ grails


```

- Run this to create a new Domain Class

```sh

$ create-domain-class yourmodelname

```

------------------------

<p align="center">

<br>
<img src="https://imgur.com/T1NTbyT.png">

<br>
</p>


> In terms of Grails once it recieves a request:
> - The application looks here in this file:

<p align="center">

<img src="https://imgur.com/enqQjYg.png">

</p>

> Which will look something like this:

<p align="center">

<img src="https://imgur.com/utbOHkK.png">

</p>



> If the URL doesnt contain a /
- Ex.
- coolsite.com and not coolsite.com/about


<p align="center">

Grails looks in the UrlMappings.groovy file for an entry that matches the URL in the request.
<br> In this case if the url does not contain anything extra after .com <br>
Grails associates that as single forward slash <b>/</b><br>
So it looks for an entry with a single forward slash
<br>
<img src="https://imgur.com/XwS4931.png">


</p>


> Then once Grails finds a match:
- Grails looks at the thing next to the match
- In this case the thing next to the forward slash


<p align="center">


<img src="https://imgur.com/ACDujoz.png">

<br> Then Grails understands it needs to look inside of the views folder for a .gsp file named index

</p>

> Once Grails finds the .gsp file it renders it to the browser.

<p align="center">

Most web frameworks use HTML out the box for web pages.<br>Grails uses .gsp files which are located in the views folder
<br>
<img src="https://imgur.com/fBUOgf4.png">

<br>
.gsp files are almost equivalent to HTML files<br>They contain regular HTML but also have the ability to interpret other syntax which we will get into later.<br> If you wanted to stick with regular HTML inside a .gsp file you could though, without an issue.
<br>

</p>

**Make more pages**

- **Navigate to grails-app/views**
- **Make a new file with the extension .gsp**
> **EX.**
> - **views/test.gsp**

**Navigate to controllers/myapp/**
- **Open the UrlMappings.groovy file in an editor**
- **Add line 14 from the following image:**


<p align="center">
<img src="https://imgur.com/Ql3smqW.png">
<br>
</p>

**You just successfully registered a new view**
- **What this means is that after running the app you can now navigate to coolsite.com/test**


**Consider the following** 

- Your website name is: mycoolsite.come

> When you create a new controller in grails
> - You give the controller a name: ie. ContactList
> - However you create the controller, it should be located:
> - appname/grails-app/controllers/contactlist/ContactList.groovy


```groovy

package contactlist

    def index() {
    }

```

> The controller should have a couple things inside of it
- A package which should be the same name of the directory that the file is sitting in
- A default index method

*def index*

> The index method is saying whenever someone navigates to mycoolsite
