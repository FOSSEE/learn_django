Slide 1
------------
Title Slide
**Creating Forms in Django**

Slide 2
--------------

**Learning Objectives**

In this tutorial, we will learn to;
  - Create a Django form
  - Create a views to handle form submission

Slide 3
---------------

**System Requirements**
  - Ubuntu 16.10
  - Python 3.5 or higher version
  - python3.4-venv

Slide 4:
----------------

**What is a Form?**

- In HTML, a form is a collection of elements inside <form>...</form>
- Allow user to do things like;
    - enter text
    - select options
    - manipulate objects or controls, and so on,
- Send data to the server

Slide 5
----------------

**Django Forms**

- Django provides inbuilt libraries to help you build forms easily


Demonstration
----------------
** Creating form using html to add blog**

 - templates/add_blog.html

        <form action="" method="POST">
            {% csrf_token %}
            <label for="name">Blog name: </label>
            <input id="name" type="text" name="name">
            <input type="submit" value="Add Blog">
        </form>

 -  views.py to add blog

        def add_blog(request):
            if request.method == 'POST':
                name = request.POST.get('name')
                Blog.objects.create(name=name)
                return HttpResponse("Blog created")
            return render(request, 'add_blog.html')

 - blog/urls.py

        path('blog/add/', views.add_blog, name='add_blog'),

Demonstration
----------------

**Creating a Django Form**

 - Create a file forms.py in the ```blog``` and add the code

        from django import forms

        class BlogForm(forms.Form):
            name = forms.CharField(label='name', max_length=100)

 - views.py

        from blog.forms import BlogForm

        def add_blog(request):
            if request.method == 'POST':
                form = BlogForm(request.POST)
                if form.is_valid():
                    name = form.cleaned_data.get('name')
                    Blog.objects.create(name=name)
                    return HttpResponse("Blog created")
            context = {'form': BlogForm()}
            return render(request, 'add_blog.html', context)

 - templates/add_blog.html

        <form action="" method="POST">
            {% csrf_token %}
            {{ form }}
            <input type="submit" value="Add Blog">
        </form>

Demonstration
----------------

**Creating a Django Form from models **

- Create a file forms.py in the ```blog``` and add the code

      from blog.models import Blog, Article

      class BlogForm(forms.ModelForm):
          class Meta:
              model = Blog
              fields = ['name']
        
      class ArticleForm(forms.ModelForm):
          class Meta:
              model = Article
              fields = ['title', 'body', 'draft']

(For script creator: given article form and view as well, as an additional content, can be used if required.)

 - views.py

        from blog.forms import BlogForm

        def add_blog(request):
            if request.method == 'POST':
                form = BlogForm(request.POST)
                if form.is_valid():
                    form.save() 
                    return HttpResponse("Blog created")
            context = {'form': BlogForm()}
            return render(request, 'add_blog.html', context)

Demonstration
----------------

**Edit view **

- Let's edit an existing blog
- To do this add the following code to the ```views.py``` in the ```blog```directory

      from django.http import HttpResponse, HttpResponseNotFound
      from .forms import BlogForm, ArticleForm

      def add_blog(request, blog_id=None):
      """
      This view adds a new or edits an existing blog
      """
          if blog_id:
              blog = Blog.objects.get(id=blog_id)
          else:
              blog = Blog()
          if request.method == 'POST':
              form = BlogForm(request.POST, instance=blog)
              if form.is_valid():
                  form.save()
                  return HttpResponse("Blog created")
          blog_form = BlogForm(instance=blog)
          context = {'form': blog_form, 'blog': blog}
          return render(request, 'add_blog.html', context)
                  

**Template for the view**

- In ```add_blog.html``` add following

        <html>
        <body>
        {% if form %}
            <form action="/blogs/add_blog/{{ blog.id }}" method="post">
                {% csrf_token %}
                    {{ form }}
                <input type="submit" value="Submit" />
            </form>
        {% endif %}
        </body>
        </html>

Modify the urls located in the blogs folder

    # /blogs/urls.py
        path('blog/add/<int:blog_id>/', views.add_blog, name='add_blog'),

Slide 10:
-----------------

**Edit Templates to add new URL redirect**

- Edit the ```/blog/templates/blog/blogs.html``` as follows;


      <html>
      <body>
      <h2><a href='/blog/add_blogs/'>Add New Blog</a></h2>
      {% if blogs %}
         .
         .
        <ul>
        {% for blog in blogs %}
            <li>{{ blog.name}} <a href='/blog/add_blogs/{{ blog.id }}'>[Edit]</a></li>
        {% endfor %}
         .
         .
        </ul>
      {% else %}
          <p>No Blogs are available.</p>
      {% endif %}
      </body>
      </html>

 *** With this we come to the end of the tutorial***
 ----------------------------------------------------
 *** Add concluding slides and assignment***


(For script creator)
-------------------
**After every edit in the code the demonstration can be shown by visting the url**

For demonstration:

- Activate the virtual environment
- Run the Django test server using the command python manage.py runserver
- Open the web browser and go to http://127.0.0.1:8000/blogs/add_blog/
- For edit http://127.0.0.1:8000/blogs/add_blog/1/

- Submit form
- In django admin interface we can show the new object created
