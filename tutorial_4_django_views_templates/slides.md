Tutorial: Create Views and Route your URLS
===========================================
[Demonstration time: 10 mins 50 s (0.85 ~ 85%) | Total time: 12 mins 42 s]

Slide 1 [00:08 | 00:08]
------------
Title Slide
**Creating Views and Routing URLs**

Slide 2 [00:12 | 00:20]
--------------

**Learning Objectives**

In this tutorial, we will learn to;
  - Create a django view
  - Create a django template
  - Create a url routing scheme

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
  - If not, see the relevant django tutorial on http://spoken-tutorial.org

Slide 5 [00:10 | 00:52]
------------
**What is a View**
  - A view is code that accepts a request
  - It processes the request and sends back a response
    
Demonstration [03:00 | 03:52]
-----------
**Creating a View**

Edit the /blog/views.py

    # /blog/views.py
    from django.http import HttpResponse
    
    from .models import Blog, Article
    
    def get_blogs(request):
        blogs = Blog.objects.all() # This is called a query
        for blog in blogs:
            articles = Article.objects.filter(blog=blog)
        response = 'Blog: {0}\n\n'.format(b) + '\n'.join([article.title for article in articles])
        return HttpResponse(response)

    - Narrator Notes: Please state that Django queries will be explained later in the series,
    and should explain the above code.

Demonstration [03:50 | 07:42]
-----------
**Add URL routing to URLConf**

Now change the /myproject/urls.py so that the project knows which urls file to call

This is called the URL Dispatcher

    # /myproject/urls.py
    from django.conf.urls import include, url
    from django.contrib import admin

    urlpatterns = [
        url(r'^admin/', admin.site.urls),
        url(r'^$', views.index, name='index') # Add this line
    ]

  - Run the django server using command:
      - python manage.py runserver

  - **Narrator Note**: Show the web browser to the user
  - Go to the url http://localhost:8000/blogs/ and show the output.
  - You will see the article that you had added in the tutorial 3

 Slide 6 [00:18 | 08:00]
------------
**What is a Django Template**
  - We have hardcoded the output in the view
  - What if we want the displayed html to change dynamically?
    - Use a 'template' HTML file
  - Template HTML files contain Django template tags that act like variables
  - Django replaces these tags in the HTML file with dynamic data obtained from views

 Demonstration [03:00 | 11:00]
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
    {% if articles %}
        <ul>
        {% for article in articles %}
            <li>{{ article.title }} | Blog: {{ article.blog.name}}</li>
        {% endfor %}
        </ul>
    {% else %}
        <p>No Blog articles are available.</p>
    {% endif %}

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

Demonstration [01:00 | 12:00]
----------------
Now let's modify the blog/views.py as follows
    
    from django.http import HttpResponse
    from django.shortcuts import render
    
    
    from .models import Blog, Article

    def index(request):
        article_list = Articles.objects.all()
        context = {'article_list': article_list}
        return render(request, 'blog/index.html', context)

  - Run the django server
  - Access the link localhost:8000/blogs/


*** With this we come to the end of the tutorial***
 ----------------------------------------------------
 *** Add concluding slides and assignment***[00:42 | 12:42  ]
 -------------------------------------------

