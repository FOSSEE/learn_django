Tutorial: Creating Your First Django Project & App
=====================================

Slide 1:
------------
  - What is a Django Project?
    - collection of settings for an instance of Django
    - Includes;
      - database configuration
      - Django-specific options
      - Application-specific settings

Slide 2:
------------
  - Activate the virtual environment
  - Create a new directory in your 'home' directory
    - mkdir ~/myproject

Slide 3:
------------
  **Initializing Django Project**
  - Go to the directory
    - cd ~/myproject
  - Run the command
    - *django-admin startproject mysite*
    
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
                  
Slide 5:
---------------
  - Check if you have setup Django project correctly;
    - *python manage.py runserver*
    - Show output screen

Slide 6
------------
**Initializing a Django App**
  - Create a blogging app called blog
  - Run the command;
    - *python manage.py startapp blog*

Slide 7
------------
  - A new directory 'blog' is created.
  - Execute *cd blog/*
  - You will see the file structure
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

Slide 8
------------
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
