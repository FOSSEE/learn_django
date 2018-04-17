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

    from django.http import HttpResponse
    
    def index(request):
        return HttpResponse("Hello, world. You are at the blog index")

Demonstration [02:50 | 05:42]
-----------
**Add URL routing to URLConf**

- Create ```urls.py``` in blog app

      from django.urls import path
      from . import views

      app_name = 'blog'
      urlpatterns = [
          path('', views.index, name='index'),
      ]

Now change the ```/myproject/urls.py``` so that the project knows which urls file to call

    from django.contrib import admin
    from django.urls import path, include

    urlpatterns = [
        path('admin/', admin.site.urls),
        path('blogs/', include('blog.urls', namespace='blogs')),
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


    from .models import Blog

    def get_blogs(request):
        blogs = Blog.objects.all() # This is called a django query
        return HttpResponse(blogs)

- Narrator Notes: Please state that Django queries will be explained later in the series.

- Let us append the url to the urlpatterns in ```blog/urls.py```


        urlpatterns = [
            .
            path('get_blogs/', views.get_blogs, name='get_blogs'),
        ]

  - Go to the url http://localhost:8000/blogs/get_blogs and show the output.
  - Show the blog in the output created in previous tutorial

- Improving the output

      def get_blogs(request):
          blogs = Blog.objects.all() # This is called a query
          response = 'Blogs:'
          for blog in blogs:
              response += '<\ br> {0} '.format(blog)    
          return HttpResponse(response)

    - Narrator Notes: Should explain the above code.
    - Save and again show the browser.
    - Show the blog in the output created in previous tutorial


Demonstration [01:30 | 07:52]
-----------
Let us further edit the view to display articles related to a blog.
In the /blog/views.py edit get_blogs function

        from .models import Blog, Article
    
        def get_blogs(request):
            blogs = Blog.objects.all() # This is called a query
            response = 'Blogs:'
            for blog in blogs:
                articles = Article.objects.filter(blog=blog)
                response += '<br \> {0} '.format(blog)
                response += ', '.join([article.title for article in articles])
            return HttpResponse(response)

    - Narrator Notes: Should explain the above code.
    - Save and again show the browser.
    - We now also see the article created in the tutorial 3.


*** With this we come to the end of the tutorial***
 ----------------------------------------------------
*** Add concluding slides and assignment***[00:42 | 08:34]
 -------------------------------------------
 Narrator Notes: Can give assignment to create a view ***count_blogs*** for displaying the number of blogs.
