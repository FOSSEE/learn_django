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

- Modify the blog/views.py, modify the get_blogs view to display the Blog List of a particular user in a template

      def get_blogs(request, user):
          user_object = User.object.get(username=user)
          blogs = Blog.objects.filter(creator=user_object)
          context = {'blogs': blogs}
          return render(request, 'blog/index.html', context)

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

**Modify the URLs**

- Modify the urls located in the ```myproject``` folder

      # /myproject/urls.py
      from django.conf.urls import include, url
      from django.contrib import admin
      from blog import urls

      urlpatterns = [
          url(r'^admin/', admin.site.urls),
          url(r'^blog/$', blog.urls) # Change this line
      ]

- Modify the urls located in the ```blogs``` folder

      # /blogs/urls.py
      from django.conf.urls import patterns, url
      from blog import urls

      urlpatterns = [
          url(r'^(?P<username>\w+)/list/$', views.get_blogs, name='blogs')
      ]
      
Slide 8
-----------------------

**Test the new view**

- Activate the virtual environment
- Run the Django test server using the command *python manage.py runserver*
- Open the web browser and go to http://127.0.0.1:8000/blog/<username>/list
  - Use the username created in Tutorial 3
  
Demonstration
-----------------------

*Note to Narrator: Demonstrate the new view in the browser to the viewer*

Slide 9
-----------------------

**Add a view to Display Articles**

- Modify the blog/views.py and add a new view to display a list of all the articles of a blog

      def get_blogs(request, user):
          user_object = User.object.get(username=user)
          blogs = Blog.objects.filter(creator=user_object)
          context = {'blogs': blogs}
          return render(request, 'blog/index.html', context)
