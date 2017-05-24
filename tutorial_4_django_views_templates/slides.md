Tutorial: Create Views and Route your URLS
===========================================

Slide 1 [00:08 | 00:08]
------------
Title Slide
**Creating Views and Routing URLs**

Slide 2
--------------

**Learning Objectives**

In this tutorial, we will learn to;
  - Create a django view
  - Create a django template
  - Create a url routing scheme

Slide 3
---------------

**System Requirements**
  - Ubuntu 16.10
  - Python 3.5 or higher version
  - python3.4-venv
  
Slide 4
---------------

**Pre-requisites**

In order to follow this tutorial, you need to know;
  - how to create models in django
  - If not, see the relevant django tutorial on http://spoken-tutorial.org

Slide 5 
------------
**What is a View**
  - A view is code that accepts a request
  - It is responsible for:
    - interaction with the database
    - reads, deletes & updates database entries
    - Provide a response to the request
    - trigger the rendering of templates as a part of response

Demonstration
-----------
**Creating a View**
  - Edit the /blog/views.py

    # /blog/views.py
    from django.http import HttpResponse

    from .models import Blog, Article

    def index(request):
        blog_list = Blog.objects.all() # This is called a query
        for b in blogs:
            article_list = Article.objects.filter(blog=b)
        output = 'Blog: {0}\n\n'.format(b) + '\n'.join([article.title for article in article_list])
        return HttpResponse(output)

    - Narrotr Not: Please state that Django queries will be explained later in the series

Demonstration
-----------
**Add URL routing to URLConf of app**
  - Create a new file: /blog/urls.py
  - This is the URLConf for the app
  `
    # /blog/urls.py
    from django.conf.urls import url
    
    from . import views
    
    app_name = 'blog'
    urlpatterns = [
        url(r'^$', views.index, name='index'),
    ]

  - Now change the /myproject/urls.py so that the project knows which urls file to call
  - This is called the URL Dispatcher
  
  # /myproject/urls.py
  from django.conf.urls import include, url
  from django.contrib import admin

  urlpatterns = [
      url(r'^admin/', admin.site.urls),
      url(r'^blog/', include('blog.urls')), # Add this line
  ]

  - Run the django server using command:
    - python manage.py runserver

  - **Note to Narrator**: Show the web browser to the user


 Slide 6
------------
**What is a Django Template**
  - We have hardcoded the output in the view
  - What if we want the displayed html to change dynamically?
    - Use a 'template' HTML file
  - Template HTML files contain DJango template tags that act like variables
  - Django replaces these tags in the HTML file with dynamic data obtained from views

 Demonstration
----------------
**How to create a template**

  - Create a directory called *templates* in blog directory (/blog/templates)
    - cd blogs
    - mkdir templates
  - Create a directory called *blog* within the *templates* directory
    - cd templates
    - mkdir blog
  - In this directory create an *index.html* file and add the below code
  
    # /blog/templates/blog/index.html
    {% if article_list %}
        <ul>
        {% for article in article_list %}
            <li>{{ article.title }} | Blog: {{ article.blog.name}}</li>
        {% endfor %}
        </ul>
    {% else %}
        <p>No Blog articles are available.</p>
    {% endif %}

Slide 8
-----------
**All about the Django Template**

  - We created a django template using an HTML file
  - The Django templates give the user limited programming logic capabilities like variables, if-else & for loops
  - This is an if-else statement in Django templates
      {% if %}
        ...
      {% else %}
        ...
      {% endif %}
      
  - This is a for loop
      {% for var in my_list %}
        ...
      {% endfor %}
      
  - variables and objects are represented as {{ my_variable }}
  - *Narrator's note* We will discuss more about 

Demonstration
----------------
  - Now let's modify the blog/views.py as follows
    
    from django.http import HttpResponse
    from django.shortcuts import render
    
    
    from .models import Blog, Article

    def index(request):
        article_list = Articles.objects.all()
        
        return render(request, 'blog/index.html', {'article_list': article_list})

  - Run the django server
  - Access the link localhost:8000/blog/
    - You will see the article that you had added in the tutorial 3


Slide 11 [00:12 | 08:09]
---------------   
** Assignment ** 
 - Create a new virtual environment.
 - Activate it.
 - Install other version of django

 ** Followed by standard concluding slides ** [00:30 | 08:39] 
