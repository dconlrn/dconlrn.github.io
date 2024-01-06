<table rules=none>
 <tr>
<td> <img src="https://i.imgur.com/vQrcNy3.jpeg"></td>
<td> <h2><a href="https://joshjetson.github.io">Django:<br>From Start<br>to Deployment</a></h2><br>A tutorial on how to take a Django application from a test environment to a production environment</td>
</tr>
</table>


<a id="nav"></a>

---------------------------------

## Navigation

- [Resources](#resources)
- [Options](#options)
- [Considerations](#considerations)
- [Building a Django Application](#building)
- [Deploying a Django Application w/Google Cloud](#google)



<a id="resources"></a>

----------------------------------


## Resources

> I would first like to provide a list of alternaive solutions for deploying a Django application.


> [Django Friendly](https://djangofriendly.com/index.html)
> - *Maybe the best resource available for Django deployment options*

> [Deploying Django into production](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Django/Deployment)
> - *Another resource that discusses deployment options*

> [How to deploy Django](https://docs.djangoproject.com/en/4.2/howto/deployment/)
> - *Django official deployment documentation*





<a id="options"></a>

------------------------------

## Options

*From most popular to least but still the most popular out of dozens of choices*


- [Google](#google)
- [Heroku](https://devcenter.heroku.com/articles/deploying-python)
- [Python Anywhere](https://help.pythonanywhere.com/pages/DeployExistingDjangoProject/)
- [Digital Ocean](https://docs.digitalocean.com/developer-center/deploy-a-django-app-on-app-platform/)
- [AWS](https://aws.amazon.com/?nc2=h_lg)
> - [Using Docker and EC2](https://stackabuse.com/deploying-django-applications-to-aws-ec2-with-docker/)
> - [Using Elastic Beanstalk](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/create-deploy-python-django.html)
> > - [Another Elastic Beanstalk Deployment Tutorial](https://realpython.com/deploying-a-django-app-and-postgresql-to-aws-elastic-beanstalk/)
> - [Using App Runner](https://aws.amazon.com/blogs/containers/deploy-and-scale-django-applications-on-aws-app-runner/)
- [Railway](https://dev.to/osahenru/using-railway-app-to-deploy-your-django-project-3ah1)
- [OpalStack](https://docs.opalstack.com/topic-guides/django/)
- [Linode](https://www.linode.com/docs/products/tools/marketplace/guides/django/)


- [Back to navigation](#nav)

<a id="considerations"></a>

---------------------------------

## Considerations

- Domain name purchasing
> - Namecheap
> - Google (Now Squarespace)
- Associating the application with the domain name
> - [Heroku](https://docs.opalstack.com/user-guide/domains/)
- ease of use
- limitations
- performance
- accessibility
- scalability
- resources (Databases, OS tools, programming libraries and tools)


<a id="building"></a>

## Building the application

----------------

*Assumptions:*

- You know a good deal of Python
- You know what Linux is
- You have some knowledge of HTML, CSS and JS
- You are not scared to do work in a terminal

*This example is for Linux/Unix based operating systems*

> If you are on Windows I recommend you install the Windows subsystem for Linux to follow along
> MacOS is Unix based, if you did not know now you do.

*In this example I intend to show:*
> - How an application in Django is built from start to finish

**Overview**

*We will build the application using the following conventions:*

- Git
> for version control
- SSH 
> in conjunction with Git in order to clone our project wherever we want in a secure authenticated fashion

*What you will gain from this tutorial:*

- How to work on a team of developers
- How to be your own team of developers
- How to properly clone a private local or remote repository
- How to manage your own private local or remote repositories
- How to take Django out of test mode and into production mode
- How to take Django out of a test environment and into a production environment
- How to use bootstrap
- A practical understanding of the Django framework
- A brief understanding of Nginx web server side setup and configuration
- How to SSH into a remote server and how to use SSH
- How to use Git

**START**

-------------------------

- OPTIONAL (Good Option though)
> If you do not have a static ip address and do not have dynamic DNS setup
> Consider Using No-IP to:
> - Create a free Domain Name ie. mywebsite.ddns.net
> - Forward requests from your free Domain Name to your home machine using their Free Dynamic DNS
> [No-IP](https://www.noip.com/remote-access?utm_source=google&utm_medium=cpc&utm_term=no-ip%20com&utm_campaign=brand-us&gclid=Cj0KCQiAkeSsBhDUARIsAK3tiedyZUJJGBCd6qm8gC3FeLFjgsbT0WAhT5QxcFCusa8lhxtn14pmKRwaAoF5EALw_wcB)

- **Route A** (Local Private Git):
> This route assumes:
> - Your local machine is accessible via SSH ie. `$ ssh username@mywebsite.ddns.net` or @ your home ip address
> - You will or already have open up access to port 22 on your router

- Make sure you have openssh installed on your machine
> If you don't here are some tutorials:
> - [Arch Linux](https://medium.com/@pythonaugust/enable-ssh-on-arch-linux-8f1ede0d9c88)
> - [Ubuntu Linux](https://www.cyberciti.biz/faq/ubuntu-linux-install-openssh-server/)
> - [Mac](https://osxdaily.com/2022/07/08/turn-on-ssh-mac/)
> - [Windows](https://learn.microsoft.com/en-us/windows-server/administration/openssh/openssh_install_firstuse?tabs=gui)

- In a terminal:
> `$ mkdir ~/A Directory of your choice/yourprojectname.git`
> `$ cd ~/The directory of your choice/yourprojectname.git`
> `/yourprojectname.git/ $ git init --bare`
> You should see this now

```sh

hint: Using 'master' as the name for the initial branch. This default branch name
hint: is subject to change. To configure the initial branch name to use in all
hint: of your new repositories, which will suppress this warning, call:
hint:
hint:   git config --global init.defaultBranch <name>
hint:
hint: Names commonly chosen instead of 'master' are 'main', 'trunk' and
hint: 'development'. The just-created branch can be renamed via this command:
hint:
hint:   git branch -m <name>
Initialized empty Git repository in /home/josh/git/myproject.git/


```

- `/home/josh/git/myproject.git/` = Default Example git




- **Route B** (Remote Public Git)


- [Back to navigation](#nav)

<a id="google"></a>

## Deploying via Google Cloud

---------------------------------

**Using Compute Engine**

*I recommend this method*



- [Back to navigation](#nav)

**Using App Engine**

*Note: I don't recommend using this method for the following reasons*
> It is expensive
> It is less hands on
> It is less likely to deploy without problems
> It does not take advantage of version control
> It is less transparent

- (OPTIONAL)
- Purchase a Domain Name
> There are many cheap places to purchase a domain name from

- Create a Google App Engine account
> - [Google CLoud](https://console.cloud.google.com/)
> Gotta install the google sdk
> - git clone https://aur.archlinux.org/google-cloud-cli.git
> - cd google-cloud-cli
> - makepkg -si
> I also had to source it
> - source /etc/profile.d/google-cloud-cli.sh
>
> Create a new project through console.cloud.google.com
> - Choose your projects code base

> Then CD to your projects main directory
> - gcloud init

> If you need to log into the cloudshell
> - gcloud cloud-shell ssh


**Linking your domain to your app**

> Inside of the [App Engine](console.cloud.google.com)
> - Go to settings
> - Go to custom domains
> - Go to add a custom domain
> - Select the custom domain you purchased through google and finish the setup.
>
> A new mapping will be created.
> The new mapping will have columns and rows
> - Write down or keep note of the data column and the record type of that data

Go back to 
[Google Domains](https://domains.google.com/)
- Find the DNS section. May be in the hamburger menu.
- Find Manage custom records
> Input nothing for the hostname if the record type is and kind of A.
> Enter the Data type to match from the mapping in the app engine
> If the type is a cnam for the host enter just www and the right data


- [Back to navigation](#nav)

*Don't forget to collect your static files*
> python manage.py collecstatic
