Tutorial 1: Introduction
=============================

Slide 1 [00:08 | 00:08]
-------------
**Introduction to Django**

Slide 2 [00:20 | 00:28]
--------------

**Learning Objectives**

In this tutorial, we will learn about;
  - What is a web application
  - What is a web framework
  - Why use Django
  - What is virtual environment
  - Django installation

Slide 3 [00:15 | 00:53]
---------------

**System Requirements**
  - Ubuntu 16.10
  - Python 3.5 or higher version
  - python3.4-venv (Install using *apt-get install python3.4-venv*)
	
Slide 4 [00:12 | 01:05]
---------------

**Pre-requisites**

In order to follow this tutorial, you need;
  - Knowledge of Object Oriented Python Programming
  - If not, see the Python tutorials on http://spoken-tutorial.org
	
Slide 5 [00:10 | 01:15]
----------------

**What is Django**
  - Free and open source
  - Web application framework 
  - Written in Python
  - Very popular

[Image of Django logo]

Slide 6 [00:35 | 01:50]
----------------

**What is a web application**

![Block diagram of Web application](https://raw.githubusercontent.com/FOSSEE/learn_django/master/tutorial_1_intro/webapp_diag.png 'Web Application Block diagram')
** Narration for this slide **	
  - An application stored on a remote computer i.e. server
  - A server can be accessed by a user through a web browser
  - The browser communicates with the server by sending a 'request'
  - The web application carries out actions as per the request
  - It has a 'database' to store and manipulate data
  - It sends a 'response' to the user
  - The user's browser then displays this response suitably formatted.

Slide 7 [00:16 | 02:06]
------------------

**What is a web Framework**
  - Easy to develop web apps
  - Provides
    - Interface to Database
    - Authentication (Login system)
    - Templating engine (HTML rendering)
    - Forms
		
Slide 8 [00:18 | 02:24]
-------------------

**Why Django**
  - easy to start
  - rapid development
  - has a lot of pre-built features
  - supports various database backends
  - supports multilingual websites
  - provides a user interface for administrative activities


Slide 9 [00:07 | 02:31]
--------------

**Where is Django used**

  - Pinterest - A social image and web resource sharing site
    - [Add Screenshot]

Slide 11 [00:05 | 02:36]
--------------

**Where is Django used**

  - Instagram - A social photo sharing site
    - [Add Screenshot]

Slide 12 [00:05 | 02:41]
--------------

**Where is Django used**

  - Disqus - A commenting system that can be integrated on any web page
    - [Add Screenshot]

Slide 13 [00:13 | 02:54]
---------------

**What is virtual environment**
  - Create 'isolated' environment
  - Does not require root access
  - Install Python packages from PyPI
   
Demonstration [01:20 | 04:14]
----------------

**Working with virtual environments**
  - Creating a virtual environment in Python 3
    - *python3 -m venv myapp_env*
  - Activate the environment
    - *source myapp_env/bin/activate*
    - Shell prompt will be *(myapp_env)user1:~$*
  
Demonstration [01:26 | 05:40]
---------------

**Install Django**
  - Check if django is installed using;
    - Command: *python -m django --version*
    - If not installed then we see "No module named django"
  - pip install django
  - Again we check and now we see the django version
  - Deactivate the environment
    - deactivate
  - You can also delete the virtual environment by deleting it's directory
    - *rm -rf myapp_env*
    
Slide 13 [00:15 | 05:55]
---------------   
** Assignment ** 
 - Create a new virtual environment.
 - Activate it.
 - Install other version of django

 ** Followed by standard concluding slides ** [02:15 | 08:10] 
