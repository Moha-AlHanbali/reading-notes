[Home](README.md)

<br>

# Django Custom User

<br>

## Readings from [Django Best Practices: Custom User Model](https://learndjango.com/tutorials/django-custom-user-model)

<br>

### Overview

<br>

> Django ships with a built-in User model for authentication and if you'd like a basic tutorial on how to implement log in, log out, sign up and so on see the Django Login and Logout tutorial for more.

> Using a custom user model provides far more flexibility down the line so, as a general rule, always use a custom user model for all new Django projects.

<br>

### Setup

<br>

- To start, create a new Django project from the command line. We need to do several things:
  - create and navigate into a dedicated directory
  - install Django
  - make a new Django project called config
  - make a new app accounts
  - start the local web server

<br>

> We did not run migrate to configure our database.

> It's important to wait until after we've created our new custom user model before doing so.

<br>

### AbstractUser vs AbstractBaseUser

<br>

- There are two modern ways to create a custom user model in Django:
  - AbstractUser
  - AbstractBaseUser

> In both cases we can subclass them to extend existing functionality however AbstractBaseUser requires much, much more work.

<br>

### Custom User Model

<br>

- Creating our initial custom user model requires four steps:
  - update `config/settings.py`
  - create a new `CustomUser` model
  - create new `UserCreation` and `UserChangeForm`
  - update the admin

<br>

### Superuser

<br>

> It's helpful to create a superuser that we can use to log in to the admin and test out log in/log out

<br>

### Templates/Views/URLs

<br>

> Our goal is a homepage with links to log in, log out, and sign up. Start by updating `settings.py` to use a project-level templates directory.

> Create a new project-level templates folder and within it a registration folder as that's where Django will look for the log in template.

> We will also put our signup.html template in there.

<br>

## Readings from [DjangoX](https://github.com/wsvincent/djangox)

<br>

### Installation

<br>

> DjangoX can be installed via Pip, Pipenv, or Docker depending upon your setup.

> To start, clone the repo to your local computer and change into the proper directory.

```

$ git clone https://github.com/wsvincent/djangox.git
$ cd djangox


$ docker build .
$ docker-compose up -d
$ docker-compose exec web python manage.py migrate
$ docker-compose exec web python manage.py createsuperuser
# Load the site at http://127.0.0.1:8000

```

<br>

> For Docker, the INTERNAL_IPS configuration in config/settings.py must be updated to the following:

```

# config/settings.py
# django-debug-toolbar
import socket
hostname, _, ips = socket.gethostbyname_ex(socket.gethostname())
INTERNAL_IPS = [ip[:-1] + "1" for ip in ips]

```
<br>

### Setup

<br>

```

# Run Migrations
(djangox) $ python manage.py migrate

# Create a Superuser
(djangox) $ python manage.py createsuperuser

# Confirm everything is working:
(djangox) $ python manage.py runserver

# Load the site at http://127.0.0.1:8000

```