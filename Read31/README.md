# Class 31 

## Guide to Docker

Docker is really just Linux containers which are a type of virtualization.

Virtualization has its roots at the beginning of computer science when large, expensive mainframe computers were the norm. How could multiple programmers use the same single machine? The answer was virtualization and specifically virtual machines which are complete copies of a computer system from the operating system on up.

### Container vs Virtual 

If you are a Python programmer (like me) a common question at this point is, what about virtual environments? How do they differ from containers?

Virtual environments are used to isolate Python software packages locally. We can create an isolated box for individual projects so one can use Python 2.7 and Django 1.5 while another can use Python 3.5 and Django 2.1 on the same computer. Virtual environments are great.

Also we can’t run a production database or other services within virtual environments so compared to Docker containers they are far more limited.

### Install Docker 

To install Docker we need to [Download Desktop App ](https://www.docker.com/get-started/)

Once Docker is done installing we can confirm the correct version is running.

```code
$ docker --version
Docker version 19.03.5, build 633a0ea
```

Docker Compose is an additional tool that is automatically included with Mac and Windows downloads of Docker. However if you are on Linux, you will need to add it manually. You can do this by running the command sudo pip install docker-compose after your Docker installation is complete.

Now run the command below to confirm you have a working version of it, too. The version should be at least 1.24.x.

```code
$ docker-compose --version
docker-compose version 1.24.1, build 4667896b
```

### Hello, World

To confirm Docker installed correctly we can run our first command docker run hello-world. This will download an official image and then run the container. We’ll discuss both images and containers shortly.

```code
$ docker run hello-world
Unable to find image 'hello-world:latest' locally
latest: Pulling from library/hello-world
1b930d010525: Pull complete
Digest: sha256:9572f7cdcee8591948c2963463447a53466950b3fc15a247fcad1917ca215a2f
Status: Downloaded newer image for hello-world:latest

Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://hub.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/get-started/
 ```

 A good command to inspect Docker is docker info which we can run now. It will contain a lot of output but focus on the top lines which show we now have 1 container which is stopped and 1 image.
```code
$ docker info
Containers: 1
 Running: 0
 Paused: 0
 Stopped: 1
Images: 1
```

Want to inspect just the current image?
```code
$ docker image ls
REPOSITORY          TAG        IMAGE ID            CREATED             SIZE
hello-world         latest     fce289e99eb9        12 months ago       1.84kB
```
I have shortened the actual about for CREATED and STATUS to fit but we can see the container for hello-world. The NAMES here, musing_raman, is randomly created by Docker unless we specifically set it so your name will likely be different.

Also, why do we need ls -la here instead of ls? The answer is because the container is stopped! Only running containers will appear with docker container ls.

### Images and Containers

Images and containers are the two fundamental concepts to grasp when you start with Docker. An image is a snapshot in time of what a project contains. A container is a running instance of the image.

When we ran hello-world we used an official Docker image. We did not have to create the image ourself. But typically we will create custom images and we do so using a Dockerfile. We also will use docker-compose.yml files to run the containers.

## Django fir APIs

Django REST frameworks alongside the Django web framework to create web APIs. We cannot build a web API with only Django Rest Framework. It always must be added to a project after Django itself has been installed and configured.

### Traditional Django 

Navigate to the existing code directory on the Desktop and make sure you are not in a current virtual environment. You should not see (.venv) before the shell prompt. If you do, use the command deactivate to leave it. Make a new directory called library, create a new virtual environment, activate it, and install Django.

```code
# Windows
> cd onedrive\desktop\code
> mkdir library
> cd library
> python -m venv .venv
> .venv\Scripts\Activate.ps1
(.venv) > python -m pip install django~=4.0.0

# macOS
% cd desktop/desktop/code
% mkdir library
% cd library
% python3 -m venv .venv
% source .venv/bin/activate
(.venv) % python3 -m pip install django~=4.0.0
```
A traditional Django website consists of a single project with multiple apps representing discrete functionality. Let’s create a new project with the startproject command called django_project. Don’t forget to include the period . at the end which installs the code in our current directory. If you do not include the period, Django will create an additional directory by default.

```code
(.venv) > django-admin startproject django_project .

```

Pause for a moment to examine the default project structure Django has provided for us. You examine this visually if you like by opening the new directory with your mouse on the Desktop. The .venv directory may not be initially visible because it is “hidden” but nonetheless still there.


```tree
├── django_project
│   ├── __init__.py
|   ├── asgi.py
│   ├── settings.py
│   ├── urls.py
│   └── wsgi.py
├── manage.py
└── .venv/
```

The .venv directory was created with our virtual environment but Django has added a django_project directory and a manage.py file. Within django_project are five new files:

- `__init__.py`  indicates that the files in the folder are part of a Python package. Without this file, we cannot import files from another directory which we will be doing a lot of in Django!
- `asgi.py`  allows for an optional Asynchronous Server Gateway Interface to be run
- `settings.py` controls our Django project’s overall settings
- `urls.py` tells Django which pages to build in response to a browser or URL request
- `wsgi.py` stands for Web Server Gateway Interface which helps Django serve our eventual web pages.

The `manage.py` file is not part of django_project but is used to execute various Django commands such as running the local web server or creating a new app. Let’s use it now with migrate to sync the database with Django’s default settings and start up the local Django web server with runserver.

```code
(.venv) > python manage.py migrate
(.venv) > python manage.py runserver

```

Open a web browser to http://127.0.0.1:8000/ to confirm our project is successfully installed and running.

['web browser '](https://djangoforapis.com/assets/images/00_welcome40.png)

### First app

The next step is to add our first app which we’ll call books. Stop the local server by typing Control+c and then run the startapp command plus our app name to create it.

```code
(.venv) > python manage.py startapp books

```
Now let’s explore the app files Django has automatically created for us.

```tree
├── books
│   ├── __init__.py
│   ├── admin.py
│   ├── apps.py
│   ├── migrations
│   │   └── __init__.py
│   ├── models.py
│   ├── tests.py
│   └── views.py
```

Each app has a __init__.py file identifying it as a Python package and there are 6 new files created:

`admin.py` is a configuration file for the built-in Django Admin app
`apps.py` is a configuration file for the app itself
`migrations/` is a directory that stores migrations files for database changes
`models.py` is where we define our database models
`tests.py` is for our app-specific tests
`views.py` is where we handle the request/response logic for our web app
Typically, developers will also create an `urls.py` file within each app for routing. We’ll do that shortly.

Before moving on we must add our new app to the INSTALLED_APPS configuration in the `django_project/settings.py`. Do so now with your text editor.

```code
# django_project/settings.py
INSTALLED_APPS = [
    "django.contrib.admin",
    "django.contrib.auth",
    "django.contrib.contenttypes",
    "django.contrib.sessions",
    "django.contrib.messages",
    "django.contrib.staticfiles",
    # Local
    "books.apps.BooksConfig",  # new
]
```

Each web page in traditional Django requires several files: views.py, urls.py, template, and models.py. Let’s start with the database model to structure our Library data.

### Models

In your text editor, open up the file books/models.py and update it as follows:

```code
# books/models.py
from django.db import models


class Book(models.Model):
    title = models.CharField(max_length=250)
    subtitle = models.CharField(max_length=250)
    author = models.CharField(max_length=100)
    isbn = models.CharField(max_length=13)

    def __str__(self):
        return self.title

```

This is a basic Django model where models is imported from Django on the top line and a new class, called Book, extends it. There are four fields: title, subtitle, author, and isbn. We also include a __str__ method so that the title of a book will display in readable format in the admin later on. Note that an ISBN is a unique, 13-character identifier assigned to every published book.

Since we created a new database model we need to create a migration file to go along with it. Specifying the app name is optional but recommended. We could just type python manage.py makemigrations but if there were multiple apps with database changes, both would be added to the migrations file which makes debugging in the future more of a challenge. Keep your migrations files as specific as possible.

```code
(.venv) > python manage.py makemigrations books
Migrations for 'books':
  books/migrations/0001_initial.py
    - Create model Book
```

Then second step after creating a migrations file is to migrate it so it is applied to the existing database.


### Admin

We can start entering data into our new model via the built-in Django app. To use it we need to create a superuser account and update the `books/admin.py` file so the books app is displayed.

Start with the superuser account. On the command line run the following command:

```code
(.venv) > python manage.py createsuperuser

```
Follow the prompts to enter a username, email, and password. Note that for security reasons, text will not appear on the screen while entering your password.

Now update our books app’s `admin.py` file.

```code
# books/admin.py
from django.contrib import admin

from .models import Book

admin.site.register(Book)
```

That’s all we need! Start up the local server again.

```code
(.venv) > python manage.py runserver

```
Navigate to ``http://127.0.0.1:8000/admin`` and log in. This brings up the admin homepage.

![' ' ](https://djangoforapis.com/assets/images/03_admin_homepage.png)

Click on the “+ Add” link next to Books.

![' '](https://djangoforapis.com/assets/images/03_admin_add_book.png)



Resources:

- [DjangoForAPIs](https://djangoforapis.com/library-website-and-api/)
- [Docker](https://www.docker.com/get-started/)
- [beginners-guide-to-docker](https://wsvincent.com/beginners-guide-to-docker/)