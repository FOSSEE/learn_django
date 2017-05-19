Tutorial: Create Django Models
===============================

Slide 1 [00:08 | 00:08]
-------------
Title Slide: ** Creating Django Models **

Slide 2 [00:13 | 00:21]
--------------

**Learning Objectives**

In this tutorial, we will learn to;
  - Create a django model
  - Perform Database migration
  - Use Admin app

Slide 3 [00:13 | 00:34]
---------------

**System Requirements**
  - Ubuntu 16.10
  - Python 3.5 or higher version
  - python3.4-venv
  
Slide 4 [00:15 | 00:49]
---------------

**Pre-requisites**

In order to follow this tutorial, you need to know;
  - how to create a django project
  - If not, see the relevant django tutorial on http://spoken-tutorial.org


Slide 4: What is a Django Model [00:30 | 01:19]
--------------------------------------

  - Every Django app has one or more models
  - A Django model is a pythonic representation of a Database Table
    - A Model Class represents a database table
    - A Model attribute represents a column
    - Each model instance is table row
  - All django models are stored in a models.py
    - models.py represents a Database

Slide 5: Creating Django Models for Blog app [00:35 | 01:54]
-----------------------------------------------

  - We will create two tables 'blog' and 'article'
  - The blog model will have 3 fields:
    - name
    - creator
    - create_date
  - the 'article' model will have 5 fields:
    - blog
    - title
    - create_date
    - author
    - body

Demonstration [03:00 | 04:54]
----------------

  - open */blog/models.py* in editor
  - Type the following code

        from django.db import models

        class Blog(models.Model):
            name = models.CharField(max_length=120)
            created_on = models.DateTimeField('date created')


        class Article(models.Model):
            blog = models.ForeignKey(Blog, on_delete=models.CASCADE)
            created_on = models.DateTimeField('date created')
            title = models.CharField(max_length=120)
            body = models.TextField()
            draft = models.BooleanField(default=False)

   - **(Not for narration) Note:  For this demonstration there should explanation about each field **

Demonstration [01:00| 06:39]
--------------------
- Run python manage.py --help
  - Show the help text for *makemigrations* command
  - Show the help text for *migrate* command

- Go to the directory containing *manage.py* file
  - Make sure that the environment is active
  - Run the command to create database migration files
    - *python manage.py makemigrations*
  - Run the command to apply these migrations
    - *python manage.py migrate*
  - Output:
    - *Show command line output for makemigrations and migrate*
    - Observe that a *db.sqlite3* has been created.
    - Check the /blog/migrations/ directory and you will observe that a new file has been created.
  - We will be revisiting *migrations* in more detail later

Slide 5: What is Django Admin App [00:13| 06:52]
-------------------------------------------

  - What is the Django Admin App
    - The django admin app is a feature that provides an interface to Create, Read, Update and Delete model instances

Demonstration: Create a superuser [00:55| 07:47]
----------------------------------------------
  - Create a superuser to login to the admin interface
    - Run *python manage.py createsuperuser*
      - Provide a username
      - Provide an email address
      - Provide a password and confirm it by entering again
  - Output: *Superuser created successfully.*


Demonstration: Show the Admin interface [00:45| 08:32]
---------------------------------
  - Run the django server with
    - *python manage.py runserver*
  - Open the web browser and go to http://127.0.0.1:8000/admin/
  - You will see the login screen
      - [Add Screenshot]
  - Enter the superuser credentials as created previously
  - You can see the interface
    - [Add Screenshot]
    
Demonstration: Make the Blog App modifiable through Admin [00:45| 08:32]
-------------------------------------------
  - In order to display the Blog app and it's components in the admin interface, change the */blog/admin.py* file;

    # /blog/admin.py
    from django.contrib import admin

    from .models import Blog, Article

    admin.site.register(Blog)
    admin.site.register(Article)
  - Save
  - Login to the Admin interface

Demonstration: Add a Blog database entry [00:40| 09:12]
-----------------------
  - Click on 'Blog'
  - Click on 'Add Blog'
  - Fill the form for new blog
    - name
    - creator
    - create_date
  - Click on Save
  
  - You will see your new blog in the list
    - You can click on the blog name to view it's details
  - Click on Home (in breadcrumb section)
  
Demonstration: Add an Article database entry [00:45| 09:57]
--------------------------------
  - Click on 'Article'
  - Click on 'Add Article'
  - Fill the form for the new Article
    - blog: Select 'My New Blog' from list
    - title
    - create_date
    - author: Select super-username form the list
    - body: Add Article text
  - Click on Save
  - You will see your new article in the list
    - You can click on the article name to view it's details
 
 
 *** With this we come to the end of the tutorial***
 ----------------------------------------------------
 *** Add concluding slides and assignment***
 -------------------------------------------
