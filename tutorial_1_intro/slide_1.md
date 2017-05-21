Tutorial 1: Introduction
=============================
[Demonstration time: 6 mins (0.751 ~ 75%) | Total time: 8 mins 41 s]
-------------

Slide 1 [00:08 | 00:08]
-------------
**Introduction to Django**

Slide 2 [00:09 | 00:17]
--------------

**Learning Objectives**

In this tutorial, we will learn about;
  - What is Django
  - What is virtual environment
  - Django installation

Slide 3 [00:11 | 00:28]
---------------

**System Requirements**
  - Ubuntu 16.10
  - Python 3.5 or higher version
  - python3.4-venv (Install using *apt-get install python3.4-venv*)
	
Slide 4 [00:12 | 00:40]
---------------

**Pre-requisites**

In order to follow this tutorial, you need;
  - Knowledge of Object Oriented Python Programming
  - If not, see the Python tutorials on http://spoken-tutorial.org
	
Slide 5 [00:10 | 00:50]
----------------

**What is Django**
  - Free and open source
  - Web application framework 
  - Written in Python
  - Very popular

[Image of Django logo]


Slide 6 [00:13 | 01:03]
-------------------

**Why Django**
  - easy to start
  - rapid development
  - has a lot of pre-built features
  - supports various database backends
  - supports multilingual websites
  - provides a user interface for administrative activities


Slide 7 [00:06 | 01:09]
--------------

**Where is Django used**

  - Pinterest - A social image and web resource sharing site
    - [Add Screenshot]

Slide 8 [00:03 | 01:12]
--------------

**Where is Django used**

  - Instagram - A social photo sharing site
    - [Add Screenshot]

Slide 9 [00:03 | 01:15]
--------------

**Where is Django used**

  - Disqus - A commenting system that can be integrated on any web page
    - [Add Screenshot]

Slide 10 [00:12 | 01:27]
---------------

**What is virtual environment**
  - Create 'isolated' environment
  - Does not require root access
  - Install Python packages from PyPI
   
Demonstration [02:00 | 03:27]
----------------

**Working with virtual environments**
  - Creating a virtual environment in Python 3
    - *python3 -m venv myapp_env*
  - Activate the environment
    - *source myapp_env/bin/activate*
    - Shell prompt will be *(myapp_env)user1:~$*
  - Deactivate the environment
    - deactivate
    
Demonstration [02:00 | 05:27]
---------------

**Install Django**
  - Check if django is installed using;
    - Command: *python -m django --version*
    - If not installed then we see "No module named django"
  - pip install django
  - Again we check and now we see the django version
  - We can also update the django version in future
    - pip install -U django
  - For more help:
    - pip --help or pip <command> --help

Demonstration [ 02:30 | 07:57]
---------------
- Now we will run few commands to see how django works.
- We will learn about them in later tutorials.
- Type the following command:
  - django-admin.py startproject demo-project
- This creates a project directory with all necessory files.
- cd demo-project
- Now run:
   - python manage.py runserver
- This may give migrations warning at the start, we ignore them for now.
- We see that the server is running now.
- Go to the address shown, mostly will be http://127.0.0.1:8000/
- So in a web browser we see the django index page.
- Go back to the terminal.
- We can quit the server with CONTROL-C
- You can also delete the virtual environment by deleting it's directory
  - *rm -rf myapp_env*
    
Slide 11 [00:12 | 08:09]
---------------   
** Assignment ** 
 - Create a new virtual environment.
 - Activate it.
 - Install other version of django

 ** Followed by standard concluding slides ** [00:30 | 08:39] 
