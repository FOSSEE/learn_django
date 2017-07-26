Slide 1 [00:08 | 00:08]
------------
Title Slide
**Django Authentication**

Slide 2 [00:12 | 00:20]
--------------

**Learning Objectives**

In this tutorial, we will learn to;
  - Create login functionality
  - Using django built-in login and logout functions

Slide 3 [00:11 | 00:31]
---------------

**System Requirements**
  - Ubuntu 16.10
  - Python 3.5 or higher version
  - python3.4-venv

Slide 4:
----------------

**Introduction**

- Let us use our knowledge of forms and templates to create a login system for our blog application
- We will use Django's inbuilt authentication system for this.

Slide 5:
----------------

**Modify the urls.py**

- Modify the urls.py file located in the ```myproject``` folder


      from django.conf.urls import include, url
      from django.contrib import admin
      from blog import views
      from django.contrib.auth import views as auth_views # Add this import


      urlpatterns = [
          url(r'^admin/', admin.site.urls),
          url(r'^blogs/$', include('blogs.urls')),
          url(r'^login/$', auth_views.login, {'template_name': 'login.html'}), # Add this line
      ]

Slide 6:
------------------

**Create a new template*

- Create a template ```login.html``` at ```/blog/templates/blog/login.html``` to look like below

        <html>
        <body>
            <form method="post" action="{% url 'django.contrib.auth.views.login' %}">
                {% csrf_token %}
                <p class="bs-component">
                    <table>
                        <tr>
                            <td>{{ form.username.label_tag }}</td>
                            <td>{{ form.username }}</td>
                        </tr>
                        <tr>
                            <td>{{ form.password.label_tag }}</td>
                            <td>{{ form.password }}</td>
                        </tr>
                    </table>
                </p>
                <p class="bs-component">
                    <center>
                        <input class="btn btn-success btn-sm" type="submit" value="login" />
                    </center>
                </p>
                <input type="hidden" name="next" value="{{ next }}" />
            </form>
        </body>
        </html>

Slide 7:
------------------

**Add a new form**

- We will now add a login form to the ```forms.py``` file located in ```blog``` folder
- Add the following code to the file;

      from django.contrib.auth.forms import AuthenticationForm 
      from django import forms

      # If you don't do this you cannot use Bootstrap CSS
      class LoginForm(AuthenticationForm):
          username = forms.CharField(label="Username", max_length=30, 
                                   widget=forms.TextInput(attrs={'name': 'username'}))
          password = forms.CharField(label="Password", max_length=30, 
                                   widget=forms.TextInput(attrs={'name': 'password'}))


Slide 8:
--------------------

**Add the form to the URL configuration**

- We will now add the form that we just created to the URL configuration of ```/login``` URL

      # myproject/urls.py

      from django.conf.urls import include, url
      from django.contrib import admin
      from blog import views
      from django.contrib.auth import views as auth_views
      from blog.forms import LoginForm

      urlpatterns = [
          url(r'^admin/', admin.site.urls),
          url(r'^blogs/$', include('blogs.urls')),
          url(r'^login/$', auth_views.login, {'template_name': 'login.html', 'authentication_form': LoginForm}}), # Add this variable 'authentication_form'
      ]

Slide 8:
--------------------

**Modifying the views**

- You will have to add this line ```@login_required(login_url="login/")``` above all the function in the ```views.py```
- This is called a decorator.
- It is a special function and a built-in feature in django that allows you to verify if the current session of the User is authenticated.
- In case the user is not logged in / authenticated, the user is redirected to the link specified in the variable ```login_url```

Example:

      # blog/views.py

      @login_required(login_url="login/")
      def get_blogs(request, username):
          ...

      @login_required(login_url="login/")
      def edit_blogs(request, blog_id):
          ...

      @login_required(login_url="login/")
      def edit_articles(request, article_id):
        ` ...

Slide 9:
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
          url(r'^login/$', auth_views.login, {'template_name': 'login.html', 'authentication_form': LoginForm}}),
          url(r'^logout/$', auth_views.logout, {'next_page': '/login'}), # Add this line
      ]
      
Slide 10:
---------------------

- Add a link to the ```/logout``` url to the templates

