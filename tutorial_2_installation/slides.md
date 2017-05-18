Tutorial 2: Installation
============================

Slide 1
---------------

**System Requirements:**
  - Python 3
  - python3.4-venv (Install using *apt-get install python3.4-venv*)
  - Ubuntu 16.10

Slide 2
---------------

**What is virtual environment**
  - Install Python packages from PyPI
  - Does not require root access
  - Create 'isolated' environment
  
Slide 3
----------------

**Working with virtual environments**
  - Create a virtual environment
    - python -m venv /path-to-env/directory_name
  - Activate the environment
    - source /path-to-env/bin/activate
  - Deactivate the environment
    - deactivate
  - Delete the environment and related packages
    - Delete the environment directory


Slide 4
---------------

**Create a virtual environment**
  - Creating a virtual environment in Python 3
      - *python3 -m venv /path-to-env/myapp_env*
      
Slide 5
----------------

**Activate the virtual environment**
   - *source /path-to-env/myapp_env*
   - Shell prompt will be *(myapp_env)user1:~$*

Slide 5
---------------

**Install Django**
  - pip install django
  - Check if django is installed using;
    - Command: *python -m django --version*
