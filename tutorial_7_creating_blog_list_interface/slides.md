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

      def get_blogs(request, user):
          user_object = User.object.get(username=user)
          blogs = Blog.objects.filter(creator=user_object)
          context = {'blogs': blogs}
          return render(request, 'myapp/index.html', context)

Slide 6:
---------------------

**Modify the blogs template**

- Modify the template created previously, located at ```/blog/templates/blog/blogs.html``` to look like below

    # /blog/templates/blog/blogs.html
    {% if blogs %}
        <ul>
        {% for blog in blogs %}
            <li>{{ blog.name}}</li>
                <ul>
                {% for article in blog.article_set %}
                    <li>{{ article.title }}</li>
                {% endfor %}
                </ul>
        {% endfor %}
        </ul>
    {% else %}
        <p>No Blogs are available.</p>
    {% endif %}

Slide 7:
---------------------

** Modify the URLs **

- Modify the urls located in the ```myproject``` folder

      # /myproject/urls.py
      from django.conf.urls import include, url
      from django.contrib import admin
      from blog import urls

      urlpatterns = [
          url(r'^admin/', admin.site.urls),
          url(r'^blog/$', blog.urls) # Add this line
      ]

- Modify the urls located in the ```blogs``` folder

      # /blogs/urls.py
      from django.conf.urls import patterns, url
      from blog import urls

      urlpatterns = [
          url(r'^(?P<username>\w+)/list/$', views.get_blogs, name='blogs') # Add this line
      ]

