Tutorial: Create Views and Route your URLs
===========================================
[Demonstration time: 7 mins 00 s (0.817 ~ 82%) | Total time: 8 mins 34 s]

Slide 1 [00:08 | 00:08]
------------
Title Slide
**Creating Views and Resolving URLs**

Slide 2 [00:12 | 00:20]
--------------

**Learning Objectives**

In this tutorial, we will learn to:
  - Create a django view
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

In order to follow this tutorial, you need to know:
  - how to create models in django
  - If not, see the relevant django tutorial on http://spoken-tutorial.org

Slide 5 [00:10 | 00:52]
------------
**What is a View**
  - A view is code that accepts a request
  - It processes the request and sends back a response
    
Demonstration [02:00 | 02:52]
-----------
**Creating a View**

Edit the /blog/views.py

    # /blog/views.py
    from django.http import HttpResponse
    
    from .models import Blog
    
    def get_blogs(request):
        blogs = Blog.objects.all() # This is called a query
        return HttpResponse(blogs)

    - Narrator Notes: Please state that Django queries will be explained later in the series,
    and should explain the above code.

Demonstration [02:50 | 05:42]
-----------
**Add URL routing to URLConf**

Now change the /myproject/urls.py so that the project knows which urls file to call

This is called the URL Dispatcher

    # /myproject/urls.py
    from django.conf.urls import include, url
    from django.contrib import admin
    from blog import views

    urlpatterns = [
        url(r'^admin/', admin.site.urls),
        url(r'^blogs/$', views.get_blogs, name='blogs') # Add this line
    ]

  - Run the django server using command:
      - python manage.py runserver

  - **Narrator Note**: Show the web browser to the user
  - Go to the url http://localhost:8000/blogs/ and show the output.
  - You will see the blog object Query set.
  - So we have created a simple client-server model.(At this point we can show
    the image, we showed in the previous tutorial.)
  - Let us now improve our view.


Demonstration [01:30 | 06:22]
-----------
In the /blog/views.py edit get_blogs function

    
    def get_blogs(request):
        blogs = Blog.objects.all() # This is called a query
        response = 'Blogs:\n\n'
        for blog in blogs:
            response += '{0}\n'.format(blog)    
        return HttpResponse(response)

    - Narrator Notes: Should explain the above code.
    - Save and again show the browser.
    - We now see the individual blog object created in tutorial 3.


Demonstration [01:30 | 07:52]
-----------
Let us further edit the view to display articles related to a blog.
In the /blog/views.py edit get_blogs function

    
    def get_blogs(request):
        blogs = Blog.objects.all() # This is called a query
        response = 'Blogs:\n\n'
        for blog in blogs:
            articles = Articles.objects.filter(blog=blog)
            response += '{0}\n'.format(blog)
            response += '\n'.join([article.title for article in articles])
        return HttpResponse(response)

    - Narrator Notes: Should explain the above code.
    - Save and again show the browser.
    - We now also see the article created in the tutorial 3.


*** With this we come to the end of the tutorial***
 ----------------------------------------------------
*** Add concluding slides and assignment***[00:42 | 08:34]
 -------------------------------------------
 Narrator Notes: Can give assignment to create a view ***count_blogs*** for displaying the number of blogs.
