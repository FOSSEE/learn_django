Tutorial: Creating Your First Django Project
=====================================
[Demonstration time: 7 mins 30 secs (0.812 ~ 81%) | Total time: 9 mins 11 s]
-------------

Slide 1 [00:08 | 00:08]
-------------
Title Slide: ** Creating a Django Project **

Slide 2 [00:12 | 00:20]
--------------

**Learning Objectives**

In this tutorial, we will learn to;
  - Create a django project
  - Initialize a django app

Slide 3 [00:11 | 00:31]
---------------

**System Requirements**
  - Ubuntu 16.10
  - Python 3.5 or higher version
  - python3.4-venv
  
Slide 4 [00:15 | 00:46]
---------------

**Pre-requisites**

In order to follow this tutorial, you need to know;
  - how to use a virtual environment
  - how to install django
  - If not, see the relevant django tutorial on http://spoken-tutorial.org
	
Demonstration: [01:30 | 2:16]
------------
- Revisit the virtual environment created in previous tutorial.
 - Activate the virtual environment
  - Create a new directory
    - mkdir myproject
  - Go to the directory
    - cd myproject
  - Run the command
    - *django-admin startproject mysite*
  - This will create a django project 'mysite'
    
Demonstration: [02:00 | 4:16]
-------------
  - So django project is
    - collection of settings for an instance of Django
    - Includes;
      - database configuration(will be seen after we run the server for the first time)
      - Django-specific options
      - Application-specific settings
      
    **(Not for narration) Note:  For this demonstration we can navigate through project files and explain them **
  
Slide 5: [00:05 | 04:21]
-------------
  - You will see such a File structure
 
        myproject/
             |-> manage.py
             `-> mysite/
                  |-> __init__.py
                  |-> settings.py
                  |-> urls.py
                  `-> wsgi.py
                  
Demonstration [01:30 | 05:51]
---------------
  - Now let us run the django server and check;
    - *python manage.py runserver*
  - You will see that the server is running at the address shown.
  - Go to the address via web browser
  - We see the django's index page- "It works"
  - Here we can see the command to create an app in django.

Slide [00:10 | 06:01]
-----------
**Initializing a Django App**
  - A Django project typically contains one or more apps
  - A Django app performs a particular task
  - Let us create a blogging app called 'blog'

Demonstration [01:30 | 07:31]
--------------
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

Demonstration [01:00 | 08:31]
------------
** Adding the app to the settings file**
  - For the project to detect an app, we need to add the app name to settings.py
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
   - So now our app will be recognized by our project.
   
Slide 13 [00:10 | 08:41]
---------------   
** Assignment ** 
 - Create a new project and app

 ** Followed by standard concluding slides ** [00:30 | 09:11] 
