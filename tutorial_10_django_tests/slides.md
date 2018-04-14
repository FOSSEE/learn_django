Slide 1
--------
Title Slide
** Writing Tests in Django**

Slide 2
--------

**Learning Objectives**

In this tutorial, we will learn to;
  - Write tests in django
  - Run tests in django

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
  - how to use django shell
  - If not, see the relevant django tutorial on http://spoken-tutorial.org

Slide 5
-------

** Testing in Django**
 - Automated testing is very useful
 - We can validate our code during development
 - Testing is very complex,as we need to test models, views and forms.
 - In this tutorial we learn to write tests for models

Demonstration
-------------

 - Write tests in tests.py in blog app

        from django.test import TestCase

        # Create your tests here.

        from blog.models import Blog

        class BlogTestCase(TestCase):
            def setUp(self):
                Blog.objects.create(name='Blog1')

            def test_blog_created(self):
                blog = Blog.objects.get(id=1)
                name = 'Blog1'
                self.assertEqual(blog.name, name)

 - Run test

        python manage.py test blog

We will see test Ran successfully

Demonstration
-------------
**Adding one more testcase**

        def test_was_created_recently(self):
            blog = Blog.objects.get(id=1)
            is_created_recently = True
            self.assertEqual(blog.was_created_recently(), is_created_recently)
 - Run

Demonstration
-------------
**Failing testcase**

 - Edit testcase

        def test_was_created_recently(self):
            blog = Blog.objects.get(id=1)
            is_created_recently = False # Change True to False
            self.assertEqual(blog.was_created_recently(), is_created_recently)

 - Run

 - Show assertion error in the output


Demonstration
-------------
** Using assertTrue **

 - Edit testcase

        def test_was_created_recently(self):
            blog = Blog.objects.get(id=1)
            self.assertTrue(blog.was_created_recently())

 - Run


Demonstration
--------------
 - Run individual test case

        python manage.py shell test blogs.tests.test_was_created_recently

Demonstration
--------------
 - Add testcase for Article model
 - Run
(For script creator: Can add this or give this as an assignment)

**Concluding Slides**
