Tutorial: Django Shell and Django Database Query
=====================================
[Demonstration time: 7 mins 00 secs (0.8333 ~ 83%) | Total time: 8 mins 24 s]
------------

Slide 1 [00:00 | 00:08]
------------
Title Slide
**Django Shell and Creating Django Database Query**

Slide 2 [00:08 | 00:16]
--------------

**Learning Objectives**

In this tutorial, we will learn to;
  - Use the django shell
  - Create a django query

Slide 3 [00:08 | 00:24]
---------------

**System Requirements**
  - Ubuntu 16.10
  - Python 3.5 or higher version
  - python3.4-venv
  
Slide 4 [00:08 | 00:32]
---------------

**Pre-requisites**

In order to follow this tutorial, you need to know;
  - how to create models in django
  - If not, see the relevant django tutorial on http://spoken-tutorial.org
  
Slide 5 [00:12 | 00:44]
------------

**What is the Django Shell**

 - The Django shell is a Python shell configured for our Django Project.
 - We can execute our project code in this shell.
 - We can manipulate our app models in this shell

Demonstration [03:00 | 3:44]
------------

**Start the Django Shell**

In the terminal, run the command

*python manage.py shell*

(For script creator: Here there will be certain flow, i.e activating virtual env and cd to the project directory etc..
 Also, flow will be better if before starting any activity we have an initial statement like: Let us now create/see/run....etc..)

(For script creator: small description why this command and not python.)

Run the following Django Query

  >>> from blog.models import Blog, Article
  >>> Blog.objects.all()
  
  >>> <QuerySet [<Blog: Blog object>]> # Output
  
Explanation: This django query returns all the instances of the Blog model.

Now let's add a new blog

  >>> from django.utils import timezone
  >>> b = Blog(name='My Second Blog', created_on=timezone.now())
  >>> b.save()

Explanation:
- We create an instance of Blog and add values to it's fields (name and creation date)
- We then save the object, which means Django writes this information to the SQL table 'Blog'

Now we access model field values via Python attributes.

  >>> b.id
  >>> b.name
  >>> b.created_on

Change values

  >>> b.name = 'This is a blog from shell!'
  >>> b.save()
  >>> b.name

  >>> Blog.objects.all()

In output we see, <QuerySet [<Blog: Blog object>....]>
  -  Blog object in the output is not a good representation for the object.

Let us fix this in the models.py
 - Add __str__() method to the models

 class Blog(models.model):
   .
   .
   def __str__(self):
       return self.name

 class Article(models.model):
   .
   .
   def __str__(self):
       return self.title


Lets add a custom method to the blog model

 class Blog(models.model):
   .
   .
   def was_created_recently(self):
        return self.created_on >= timezone.now() - datetime.timedelta(days=1)

In shell:
  >>> b2.was_created_recently()

Demonstration [01:30 | 05:14]
--------------

**Filtering Entries with Django Queries**

  >>> from blog.models import Blog, Article
  >>> b2 = Blog.objects.filter(id=2)
  >>> b2
  
Explanation: This query will give all the Blog instances with id 1, since the id is unique we get only one result. You can make sure that the id is 2 by running

  >>> b2[0].id
  >>> 2 # Output
  
Try sorting the Blog objects based on created_on year

  >>> current_year = timezone.now().year
  >>> Blog.objects.filter(created_on__year=current_year)

Explanation: This query will give all the blog instances with created_on year


Demonstration [01:00 | 06:14]
-------------
** methods for queryset returned**

  >>> blogs =  Blog.objects.all()
  >>> blogs.count()
  >>> blogs. <press TAB here to show > available methods

Demonstration [01:30 | 07:44]
-----------------

**Queries for related Objects**

  >>> b1 = Blog.objects.get(id=1)
  >>> b1.articles_set.all()
  
  Show output
  
Explanation: Since every article is related to a Blog (because of the ForeignKey relationship), we can always get all Articles related to a particular blog by using the "_set" suffix

  >>> a1 = Article.objects.get(id=1)
  >>> b = a1.blog
  >>> b.id

Explanation: You can always access the information of the Blog object through it's related Article object as shown above

You can also delete objects from shell

  >>> b2.delete()

Remaining conluding slides with the Assignment [00:40 | 8:24]
----------------------------------------------
