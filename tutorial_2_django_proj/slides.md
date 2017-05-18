Tutorial: Creating Your First Django Project
=====================================

Slide 1 [00:10 | 00:10]
-------------
** Creating Your First Django Project **

Slide 2 [00:15 | 00:25]
--------------

**Learning Objectives**

In this tutorial, we will learn to;
  - create django project
  - create django app

Slide 3 [00:15 | 00:40]
---------------

**System Requirements**
  - Ubuntu 16.10
  - Python 3.5 or higher version
  - python3.4-venv
  
Slide 4 [00:15 | 00:55]
---------------

**Pre-requisites**

In order to follow this tutorial, you need to know;
  - django installation and virtual environment
  - If not, see the relevant django tutorial on http://spoken-tutorial.org
	
Demonstration:
------------
- Revist the virtual environment created in previous tutorial.
 - Activate the virtual environment
  - Create a new directory
    - mkdir myproject
  - Go to the directory
    - cd myproject
  - Run the command
    - *django-admin startproject mysite*
    This will create a django project 'mysite'
    
Demonstrations:
-------------
  - So django project is
    - collection of settings for an instance of Django
    - Includes;
      - database configuration
      - Django-specific options
      - Application-specific settings
      
    **(Not for narration) Note:  For this demonstration we can navigate through project files **
  
Slide 4:
-------------
  - You will see such a File structure
 
        myproject/
             |-> manage.py
             `-> mysite/
                  |-> __init__.py
                  |-> settings.py
                  |-> urls.py
                  `-> wsgi.py
                  
Demonstration
---------------
  - Check if you have setup Django project correctly;
    - *python manage.py runserver*
    You will see that the server is running at the address shown.
    Go to the address via web browser
    We see the django's index page- "It works"

Demonstration
--------------
**Initializing a Django App**
  - Create a blogging app called blog
  - Run the command;
    - *python manage.py startapp blog*
    This creates an app 'blog'
  - A new directory 'blog' is created.
  - Execute *cd blog/*
  
  - You will see the file structure(This can be in slide or terminal)
        blog/
           |-> __init__.py
           |-> admin.py
           |-> apps.py
           |-> migrations/
                `-> __init__.py
           |-> models.py
           |-> tests.py
           `-> views.py
  - Return to the parent directory
    - *cd ..*

Demonstration
------------
** Adding the app to the settings file**
  - Open the *settings.py* file
  - Go to *INSTALLED_APPS* and add *'blog.apps.BlogConfig',* to the list so it should now look like this;

    INSTALLED_APPS = [
        'blog.apps.BlogConfig',
        'django.contrib.admin',
        'django.contrib.auth',
        'django.contrib.contenttypes',
        'django.contrib.sessions',
        'django.contrib.messages',
        'django.contrib.staticfiles',
    ]

Slide 13 [00:15 | 05:55]
---------------   
** Assignment ** 
 - Create a new project and app

 ** Followed by standard concluding slides ** [02:15 | 08:10] 
