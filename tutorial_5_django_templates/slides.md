Tutorial: Create html template in django
===========================================
[Demonstration time: 7 mins (0.805 ~ 81%) | Total time: 8 mins 42 s]

Slide 1 [00:08 | 00:08]
------------
Title Slide
**Creating html template in django**

Slide 2 [00:12 | 00:20]
--------------

**Learning Objectives**

In this tutorial, we will learn to;
  - Create a django html template

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
  - how to create views in django
  - If not, see the relevant django tutorial on http://spoken-tutorial.org

Slide 5 [00:18 | 01:00]
------------
**What is a Django Template**
  - We have hardcoded the output in the view
  - What if we want the displayed html to change dynamically?
    - Use a 'template' HTML file
  - Template HTML files contain Django template tags that act like variables
  - Django replaces these tags in the HTML file with dynamic data obtained from views

 Demonstration [04:00 | 05:00]
----------------
**How to create a template**

  - Create a directory called *templates* in blog directory (/blog/templates)
    - cd blogs
    - mkdir templates
  - Create a directory called *blog* within the *templates* directory
    - cd templates
    - mkdir blog
    
In this directory create an *blogs.html* file and add the below code
  
    # /blog/templates/blog/blogs.html

        <html>
        <body>
        {% if blogs %}
            <ul>
            {% for blog in blogs %}
                <li>{{ blog.name}} </li>
            {% endfor %}
            </ul>
        {% else %}
            <p>No Blogs are available.</p>
        {% endif %}
        </body>
        </html>

  - We created a django template using an HTML file
  - The Django templates give the user limited programming logic capabilities like variables, if-else & for loops

This is an if-else statement in Django templates
      
      {% if %}
        ...
      {% else %}
        ...
      {% endif %}
      
This is a for loop
      
      {% for var in my_list %}
        ...
      {% endfor %}
      
  - variables and objects are represented as {{ my_variable }}
  - *Narrator's note* We will discuss more about Django templating later in the series 

Demonstration [03:00 | 08:00]
----------------
Now let's modify the blog/views.py as follows
    
    from django.http import HttpResponse
    from django.shortcuts import render
    
    
    from .models import Blog, Article

    def get_blogs(request):
        blogs = Blog.objects.all()
        context = {'blogs': blogs}
        return render(request, 'blog/blogs.html', context)

  - Run the django server
  - Access the link localhost:8000/blogs/


*** With this we come to the end of the tutorial***
 ----------------------------------------------------
 *** Add concluding slides and assignment***[00:42 | 08:42]
 -------------------------------------------
