Slide 1 [00:08 | 00:08]
------------
Title Slide
**Creating Views and Routing URLs**

Slide 2 [00:12 | 00:20]
--------------

**Learning Objectives**

In this tutorial, we will learn to;
  - Use the django shell
  - Create a django query

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
  
Slide 5
------------

**What is the Django Shell**

The Django shell is a tool to help developers to
  - Manipulate Django objects in a python command line environment
  - Fetch and view objects in a python command line environment

Demonstration
------------

**Start the Django Shell**

In your command line environment, run the command

*python manage.py shell*

Demonstration
-------------

**Using the Django Shell**

Run the following Django Query

  >>> from blog.models import Blog, Article
  >>> Blog.objects.all()
  
  >>> <QuerySet [<Blog: Blog object>]> # Output
  
Explanation: This django query displays all the instances of the Question model as a list.

Now let's add a new blog using the Django shell

  >>> from django.utils import timezone
  >>> b = Blog(name="My Second Blog", created_on=timezone.now())
  >>> b.save()

Explanation:
- We create an instance of Blog and add values to it's fields (name and creation date)
- We then save the object, which means Django writes this information to the SQL table 'Blog'

Demonstration
--------------

**Filtering Entries with Django Queries**

Close and restart the django shell using the command
*python manage.py shell*

  >>> from blog.models import Blog, Article
  >>> b2 = Blog.objects.filter(id=2)
  >>> b2
  >>> <QuerySet [<Blog: Blog object>]> # Output
  >>> get_b2 = Blog.objects.get(id=2)
  >>> get_b2
  >>> <QuerySet [<Blog: Blog object>]> # Output
  
Explanation: This query will give all the Blog instances with id 1, since the id is unique we get only one result. You can make sure that the id is 2 by running

  >>> b2.id
  >>> 2 # Output
  
Try sorting the Blog objects based on created_on year

  >>> from django.utils import timezone
  >>> current_year = timezone.now().year
  >>> Question.objects.filter(created_on__year=current_year)

Explanation: This query will give all the blog instances with created_on year

Demonstration
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


  

  



