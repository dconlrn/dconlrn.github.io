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

I would first like to provide a list of alternaive solutions for deploying a Django application.

*Maybe the best resource available for Django deployment options*

[Django Friendly](https://djangofriendly.com/index.html)

*Another resource that discusses deployment options*

[Deploying Django into production](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Django/Deployment)

*Django official deployment documentation*

[How to deploy Django](https://docs.djangoproject.com/en/4.2/howto/deployment/)





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



------------------------------------

## Pricing and Comparison




| Option | Price | RAM | CPUs | EOS | 
|:-:|:-:|:---:|:------:|:---:|
| Heroku | 3 |  4  |   6    |  
|:-:|:-:|:---:|:------:|:---:|
| Python Anywhere | 7 | 16  |   28   |  
|:-:|:-:|:---:|:------:|:---:|
| Digital Ocean | 5 | 36  |   30   |  
|:-:|:-:|:---:|:------:|:---:|
| AWS |10 | 64  |   80   |  
|:-:|:-:|:---:|:------:|:---:|
| Railway |25 | 120 |   144  |  Σ  |
|:-:|:-:|:---:|:------:|:---:|
| Opalstack |25 | 120 |   144  |  Σ  |
|:-:|:-:|:---:|:------:|:---:|
| Linode |25 | 120 |   144  |  Σ  |
| Google |25 | 120 |   144  |  Σ  |


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
