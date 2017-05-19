Tutorial: Create Django Models
===============================

Slide 1: What is a Django Model
--------------------------------------

  - Every Django app has one or more models
  - A Django model is a pythonic representation of a Database Table
    - A Model Class represents a database table
    - A Model attribute represents a column
    - Each model instance is table row
  - All django models are stored in a models.py
    - models.py represents a Database

Slide 2: Creating Django Models for Blog app
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

Demonstration
----------------

  - Add the following code to */blog/models.py*

    # /blog/models.py
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

Slide 3: What is a database migration
---------------------------------------
  - A database migration is a technique that allows you to update your database, including
    - Adding & Removing columns
    - Altering columns (& the type of data that they can hold)
    - Adding & Removing tables
  - Migrations makes such changes easy since;
    - No need to rebuild the database for every change
    - Avoids loss of data
  - Django handles migrations by creating a migration *.py* file
  - **Demonstrate**
      - Run python manage.py --help
      - Show the help text for *makemigrations* command
      - Show the help text for *migrate* command

Demonstration
--------------------

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

Slide 5: What is Django Admin
-------------------------------------------

  - What is the Django Admin
    - The django admin is a feature that provides an interface for users to Create, Read, Update and Delete database entries

Demonstration: Create a superuser
----------------------------------------------
  - Create a superuser to login to the admin interface
    - Run *python manage.py createsuperuser*
      - Provide a username
      - Provide an email address
      - Provide a password and confirm it by entering again
  - Output: *Superuser created successfully.*


Demonstration: Show the Admin interface
---------------------------------
  - Run the django server with
    - *python manage.py runserver*
  - Open the web browser and go to http://127.0.0.1:8000/admin/
  - You will see the login screen
      - [Add Screenshot]
  - Enter the superuser credentials as created previously
  - You can see the interface
    - [Add Screenshot]
    
Demonstration: Make the Blog App modifiable through Admin
-------------------------------------------
  - In order to display the Blog app and it's components in the admin interface, change the */blog/admin.py* file;

    # /blog/admin.py
    from django.contrib import admin

    from .models import Blog, Article

    admin.site.register(Blog)
    admin.site.register(Article)

  - Save and exit
  - Return to the directory with *manage.py* file
  - Run the django server
    - *python manage.py runserver*
  - Open the web browser and go to http://127.0.0.1:8000/admin/
  - Login to the Admin interface

Demonstration: Add a Blog database entry
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
  
Demonstration: Add an Article database entry
--------------------------------
  - Click on 'Article'
  - Click on 'Add Article'
  - Fill the form for the new Article
    - blog: Select 'My New Blog' from list
    - title
    - create_date
    - author: Select super-username form the list
    - body: Add Article text
  - You will see your new article in the list
    - You can click on the article name to view it's details
  - Click on Save
 
