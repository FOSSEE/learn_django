Slide 1
------------
Title Slide
**Django Authentication**

Slide 2
--------------

**Learning Objectives**

In this tutorial, we will learn to;
  - Create login functionality
  - Using django built-in login and logout functions

Slide 3
---------------

**System Requirements**
  - Ubuntu 16.10
  - Python 3.5 or higher version
  - python3.4-venv

Slide 4:
----------------

**Introduction**

- Let us use our knowledge of forms and templates to create a login system for our blog application
- We will use Django's built-in authentication system for this.

Demonstration
------------------

**Add a new form**

- We will now add a login form to the ```forms.py``` file located in ```blog``` folder
- Add the following code to the file;

      from django.contrib.auth.forms import AuthenticationForm 
      from django import forms

      class LoginForm(AuthenticationForm):
          username = forms.CharField(label="Username", max_length=30, 
                        widget=forms.TextInput(attrs={'name': 'username'}))
          password = forms.CharField(label="Password", max_length=30, 
                        widget=forms.PasswordInput(attrs={'name': 'password'}))

**explain this in short, any complex concept then cna mention will be covered in the upcoming tutorials**

Demonstration
------------------

**Create a new template**

- Create a template ```login.html``` at ```/blog/templates/blog/login.html``` to look like below

        <html>
        <body>
          <form method="post">
              {% csrf_token %}
              {{ form.as_p }}
              <input type="submit" value="login" />
          </form>
        </body>
        </html>

**explain this in short, any complex concept then cna mention will be covered in the upcoming tutorials**

Demonstration
----------------

**Modify the urls.py**

- Modify the urls.py file located in the ```myproject``` folder


      from django.contrib import admin
      from django.urls import path, include
      from django.contrib.auth import views as auth_views # Add this import

      urlpatterns = [
          path('admin/', admin.site.urls),
          path('blogs/', include('blog.urls', namespace='blog')),
          path('login/', auth_views.login, {'template_name': 'blog/login.html',                'authentication_form': LoginForm}, name='login'), # Add this line
      ]

**explain this**

Demonstration
--------------------

**Modify settings.py**

- Add the following:

        LOGIN_REDIRECT_URL = '/blogs/get_blogs/'

**explain this**

Demonstration
--------------------

**Modifying the views**

- You will have to add this line ```@login_required(login_url="/login/")``` above all the function in the ```views.py```
- This is called a decorator.
- It is a special function and a built-in feature in django that allows you to verify if the current session of the User is authenticated.
- In case the user is not logged in / authenticated, the user is redirected to the link specified in the variable ```login_url```

Example:

      # blog/views.py

      @login_required(login_url="/login/")
      def get_blogs(request):
          ...


At this point, run the server and show login demo using the super user credentials
You can visit page ```http://localhost:8000/blogs/get_blogs/``` and show the demo


Demonstration
---------------------

**Add logout url**

- Modify the ```urls.py``` located in 

      # myproject/urls.py

      from django.conf.urls import include, url
      from django.contrib import admin
      from blog import views
      from django.contrib.auth import views as auth_views
      from blog.forms import LoginForm

      urlpatterns = [
          url(r'^admin/', admin.site.urls),
          url(r'^blogs/$', include('blogs.urls')),
          url(r'^login/$', auth_views.login, {'template_name': 'login.html', 'authentication_form': LoginForm}, name='logout'),
          url(r'^logout/$', auth_views.logout, {'next_page': '/login'}, name='logout'), # Add this line
      ]
      
Demonstration
---------------------

- Add a link to the ```/logout``` url to the template blogs.html as following:

    <p><a href="{% url 'logout' %}">Logout</a></p>

At this point, run the server and show logout demo, as well as login and logout demo again in different ways.
For example:
1. We can show http://localhost:8000/blogs/get_blogs/ and it reditrects to login page if user is not authenticated, else we see the blogs
2. We can show http://localhost:8000/login/ and demonstrate login and redirects!

**Concluding and Assignment Slides**

