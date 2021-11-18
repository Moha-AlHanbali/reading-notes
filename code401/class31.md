[Home](README.md)

<br>

# Django REST Framework & Docker

<br>

## Readings from [A Beginner's Guide to Docker](https://wsvincent.com/beginners-guide-to-docker/)

<br>

### Linux Containers

<br>

> Docker is really just Linux containers which are a type of virtualization.

> Virtualization has its roots at the beginning of computer science when large, expensive mainframe computers were the norm.

> Virtualization and specifically virtual machines which are complete copies of a computer system from the operating system on up.

> The downside to a virtual machine? Size and speed. A typical guest operating system can easily take up 700MB of size.

> So if one physical server supports three virtual machines, that’s at least 2.1GB of disk space taken up along with separate needs for CPU and memory resources.

<br>

### Containers vs Virtual Environments

<br>

> Virtual environments are used to isolate Python software packages locally.

> We can create an isolated box for individual projects so one can use Python 2.7 and Django 1.5 while another can use Python 3.5 and Django 2.1 on the same computer.

> They still rely on a global, system-level installation of Python albeit they can refer to the proper version.

> So when we use Python 2.7 in a project, we’re pointing to an installation of Python 2.7 on the computer itself, not actually within the virtual environment.

<br>

### Install Docker

<br>

> Once Docker is done installing we can confirm the correct version is running.

> `$ docker --version`.

> Docker Compose is an additional tool that is automatically included with Mac and Windows downloads of Docker.

> However if you are on Linux, you will need to add it manually.

> You can do this by running the command `sudo pip install docker-compose` after your Docker installation is complete.

> To confirm Docker installed correctly we can run our first command `docker run hello-world`.

> A good command to inspect Docker is `docker info` which we can run now.

> It will contain a lot of output but focus on the top lines which show we now have 1 container which is stopped and 1 image.

<br>

### Images and Containers

<br>

> Images and containers are the two fundamental concepts to grasp when you start with Docker.

> An image is a snapshot in time of what a project contains.

> A container is a running instance of the image.

<br>

- A baking analogy we can use here is as follows:
  - A Dockerfile is the recipe for a cake
  - An image is a snapshot of the recipe at a given time
  - A docker-compose.yml says how to make the cake
  - And the container is the actual, baked cake

<br>

### Images

<br>

> First create a local directory on your computer for our code.

> I’ve chosen to make a code folder on my Desktop and then a python3.7 folder within that.

> Now we need to define the image with a `Dockerfile`.

> This is similar to a Pipenv or a `requirements.txt` file; it is a list of all the requirements needed to build our image.

> It is simpler to have them all in one place rather than install each manually line-by-line.

> With your text editor add the following single line of code to the Dockerfile.

> `FROM python:3.7-alpine`.

> Dockerfiles are read from top-to-bottom. The first instruction must be the FROM command which lets us import a base image to use for our image.

> This base image could be another Docker image or one we create entirely from scratch.

> In this case we’ll be using the official Docker image for Python 3.7, specifically the alpine version which includes only the bare minimum needed to run Python.

> The alpine version takes up 78MB of space versus full Python’s 923MB so it is a good option to start with!

<br>

### Image Builds

<br>

> With our instructions complete it’s time to `build` or create the image for the first time.

> Don’t forget that period `.` at the end of the command!

<br>

### Image Layers

<br>

> Every image is made up of one or more image layers.

> The base layer is often a flavor of Linux, like alpine.

> When we built the image for python:3.7-alpine this image had the id b2c276538711.

> But that image depended on five other images which were visible while building it.

- This is called image layering and it exists for two main reasons.
  - First, each image layer is immutable–unchanged–like a git commit. This helps ensure consistency when two developers build the same image.
  - The second reason is performance.

<br>

### Containers

<br>

> Now that we have our Python image how do we run it?

> Well just as a Dockerfile is a list of image instructions there is also a `docker-compose.yml` file that is a list of container instructions.

> On the command line, go up a directory to our code folder and create a new one called djangoapp.

> Then we’ll use Pipenv to install Django and enter the virtual environment shell.

```python

$ cd ..
$ mkdir djangoapp && cd djangoapp
$ pipenv install django==3.0
$ pipenv shell

```

<br>

> This creates both a Pipfile and a `Pipfile.lock`.

>  Now create an example_project that we’ll put in our current directory.

> Don’t forget the period `.` at the end of the command here!

<br>

### Dockerized Django

<br>

> We’ll now create a Dockerfile for our image which will completely replace our local dev environment, so this will have Python 3 and Django.

> Then we’ll add a `docker-compose.yml` for the container instructions.

> Make each file via the command line.

> `$ touch Dockerfile`.

> `$ touch docker-compose.yml`.

<br>

<br>

## Readings from [Chapter 2: Library Website and API](https://djangoforapis.com/library-website-and-api/)

<br>

### Overview

<br>

> Django REST Framework works alongside the Django web framework to create web APIs.

> We cannot build a web API with only Django Rest Framework; it always must be added to a project after Django itself has been installed and configured.

<br>

### Traditional Django

<br>

> First we need a dedicated directory on our computer to store the code.

> he location really does not matter; it just needs to be easily accessible.

```py
$ cd ~/Desktop
$ mkdir code && cd code
```

> Now we are within the code folder which will be the location for all the code in this book.

> The next step is to create a dedicated directory for our library site, install Django via Pipenv, and then enter the virtual environment using the shell command.

> You should always use a dedicated virtual environment for every new Python project.

```py
$ mkdir library && cd library
$ pipenv install django~=3.1.0
$ pipenv shell
(library) $
```

> Pipenv creates a `Pipfile` and a `Pipfile.lock` within our current directory.

> The `(library)` in parentheses before the command line shows that our virtual environment is active.

> A traditional Django website consists of a single project and one (or more) apps representing discrete functionality.

> `(library) $ django-admin startproject config .`.

> Django automatically generates a new project for us which we can see with the tree command.

> Run `migrate` to sync the database with Django’s default settings and start up the local Django web server.

<br>

### First app

<br>

> `(library) $ python manage.py startapp app_name`.

> Typically developers will also create an `urls.py` file within each app too for routing.

> Open the text editor of your choice to the `config/settings.py` file.

> The first step is to add the new app to our `INSTALLED_APPS` `configuration`.

> Then run `migrate` to sync our database with the changes.

<br>

### Models

<br>

> This is a basic Django model where we import models from Django on the top line and then create a class that extends it.

> We also include a `__str__` method so that the reference to the class will display in the admin later on.

> Since we created a new database model we need to create a `migration` file to go along with it, then update our database.

<br>

### Admin

<br>

> We can start entering data into our new model via the built-in Django app.

> But we must do two things first: create a superuser account and update `admin.py` so the app is displayed.

> `(library) $ python manage.py createsuperuser`.

<br>

### Views

<br>

> The `views.py` file controls how the database model content is displayed.

> Since we want to list all items we can use the built-in generic class `ListView`.

> On the top lines we’ve imported `ListView` and our Book model.

> Then we create a `ItemListView` class that specifies the model to use and the template (not created yet).

<br>

### URLs

<br>

> We need to set up both the project-level `urls.py` file and then one within the books app.

> When a user visits our site they will first interact with the `config/urls.py` file so let’s configure that first.

> Add the include import on the second line and then a new path for our app.

> Now we can configure our `app/urls.py` file.

> Django for some reason does not include a `urls.py` file by default in apps so we need to create it ourself.

> If you are on a Mac you can use the touch command; Windows users must create the file within the text editor.

> he way Django works, now when a user goes to the homepage of our website they will first hit the `config/urls.py` file, then be redirected to `items/urls.py` which specifies using the `ItemistView`.

> The final step is to create our template file that controls the layout on the actual web page.

> We have already specified its name as `item_list.html` in our view. 

<br>

### Django REST Framework

<br>

> Django REST Framework is added just like any other third-party app.

> `(library) $ pipenv install djangorestframework~=3.11.0`.

> Add it to the `INSTALLED_APPS` config in our `settings.py` file.

> Ultimately, our API will expose a single endpoint that lists out all books in JSON.

> So we will need a new URL route, a new view, and a new serializer file (more on this shortly).

> There are multiple ways we can organize these files however my preferred approach is to create a dedicated api app. 

> `(library) $ python manage.py startapp api`.

> Then add it to `INSTALLED_APPS`.

> The api app will not have its own database models so there is no need to create a `migration` file and run migrate to update the database.

<br>

### URLs

<br>

> Let’s start with our URL configs.

> Adding an API endpoint is just like configuring a traditional Django app’s routes.

> First at the project-level we need to include the api app and configure its URL route, which will be `api/`.

> Then create a `urls.py` file within the api app.

<br>

### Views

<br>

> Next up is our `views.py` file which relies on Django REST Framework’s built-in generic class views.

> These deliberately mimic traditional Django’s generic class-based views in format, but they are not the same thing.

> To avoid confusion, some developers will call an API views file `apiviews`.py or `api.py`.

> Personally, when working within a dedicated api app I do not find it confusing to just call a Django REST Framework views file `views.py` but opinion varies on this point.

> On the top lines we import Django REST Framework’s generics class of views, the models from our item app, and serializers from our api app (we will make the serializers next).

> Then we create a `ItemAPIView` that uses `ListAPIView` to create a read-only endpoint for all book instances.

> There are many generic views available and we will explore them further in later chapters.

> The only two steps required in our view are to specify the queryset which is all available items, and then the `serializer_class` which will be `ItemSerializer`.

<br>

### Serializers

<br>

> A serializer translates data into a format that is easy to consume over the internet, typically JSON, and is displayed at an API endpoint. 

> Make a `serializers.py` file within our api app.

> `(library) $ touch api/serializers.py`.

> On the top lines we import Django REST Framework’s serializers class and the Book model from our items app.

> We extend Django REST Framework’s ModelSerializer into a ItemSerializer class that specifies our database model Item and the database fields we wish to expose: title, subtitle, and author.

<br>

### cURL

<br>

> We can use the popular cURL program to execute HTTP requests via the command line.

> All we need for a basic GET request it to specify curl and the URL we want to call.

> The data is all there, in JSON format, but it is poorly formatted and hard to make sense of.

> Fortunately Django REST Framework has a further surprise for us: a powerful visual mode for our API endpoints.

<br>

### Browsable API

<br>

> With the local server still running in the first command line console, navigate to our API endpoint in the web browser at `http://127.0.0.1:8000/api/`.

> Wow look at that! Django REST Framework provides this visualization by default.

> And there is a lot of functionality built into this page that we will explore throughout the book.

> For now I want you to compare this page with the raw JSON endpoint.

> Click on the “`GET`” button and select “`json`” from the dropdown menu.
