Slide 1 [00:08 | 00:08]
------------
Title Slide
**Creating Views and Routing URLs**

Slide 2 [00:12 | 00:20]
--------------

**Learning Objectives**

In this tutorial, we will learn to;
  - Create a new view with custom queries
  - Create an interface to view all blogs and articles

Slide 3 [00:11 | 00:31]
---------------

**System Requirements**
  - Ubuntu 16.10
  - Python 3.5 or higher version
  - python3.4-venv
  
Slide 4 [00:11 | 00:42]
---------------

**Pre-requisites**

In order to follow this tutorial, you need to know;
  - how to create models in django
  - how to write django queries
  - how to create templates
  - how to write views
  - If not, see the relevant django tutorial on http://spoken-tutorial.org
  
Slide 5:
----------------

**Create a new View**

- Modify the blog/views.py and add a new view to display the Blog List of a particular user

    def user_blogs(request, user):
    
        
