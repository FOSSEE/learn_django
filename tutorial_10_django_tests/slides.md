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
 - Testing is very complex, as we need to test models, views and forms.
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

We will see test ran successfully as follow:

        Creating test database for alias 'default'...
        System check identified no issues (0 silenced).
        .
        ----------------------------------------------------------------------
        Ran 1 test in 0.002s

        OK
        Destroying test database for alias 'default'...


Demonstration
-------------
**Adding one more testcase**

        def test_was_created_recently(self):
            blog = Blog.objects.get(id=1)
            is_created_recently = True
            self.assertEqual(blog.was_created_recently(), is_created_recently)
 - Run
 - Output will be same as above except for following:

        Ran 2 tests in 0.003s


Demonstration
-------------
**Failing testcase**

 - Edit testcase

        def test_was_created_recently(self):
            blog = Blog.objects.get(id=1)
            is_created_recently = False # Change True to False
            self.assertEqual(blog.was_created_recently(), is_created_recently)

 - Run

 - Show assertion error in the following output:

        Creating test database for alias 'default'...
        System check identified no issues (0 silenced).
        .F
        ======================================================================
        FAIL: test_was_created_recently (blog.tests.BlogTestCase)
        ----------------------------------------------------------------------
        Traceback (most recent call last):
          File "/home/ttt/my-django/myproject/mysite/blog/tests.py", line 19, in test_was_created_recently
            self.assertEqual(blog.was_created_recently(), is_created_recently)
        AssertionError: True != False

        ----------------------------------------------------------------------
        Ran 2 tests in 0.003s

        FAILED (failures=1)
        Destroying test database for alias 'default'...


Demonstration
-------------
** Using assertTrue **

 - Edit testcase

        def test_was_created_recently(self):
            blog = Blog.objects.get(id=1)
            self.assertTrue(blog.was_created_recently())

 - Run
 - Output

        Ran 2 tests in 0.003s

        OK


Demonstration
--------------
 - Run individual test case

    - python manage.py test blog.tests.BlogTestCase.test_was_created_recently

 - Output

        Ran 1 test in 0.002s

        OK


Demonstration
--------------
 - Add testcase for Article model
 - Run
(For script creator: Can add this or give this as an assignment)

**Concluding Slides**
