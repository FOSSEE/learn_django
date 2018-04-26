Slide 1
------------
Title Slide
**Using CSS and JavaScript in Django**

Slide 2
--------------

**Learning Objectives**

In this tutorial, we will learn to;
  - Add CSS and JavaScript files
  - Use them with the App

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
  - how to create templates
  - If not, see the relevant django tutorial on http://spoken-tutorial.org
  
Slide 5:
----------------

**Static Files**

  - CSS, JavaScript or Image files are referred as Static Files
  - Conventionally they are stored in static folder
  - Django will look for static files in the app static folder


Demonstration:
---------------------

**Create a folder static in blogs directory**

        mkdir static

- Create blog folder inside static

        cd static
        mkdir blog

- Create a base CSS file inside blog

        cd blog
        gedit blogs.css &


Demonstration:
---------------------
**Add class to ul tag in blogs.html template**

        <ul class="number">


**Writing CSS in blogs.css**

        ul.number {
            list-style-type:upper-roman;
        }


Demonstration:
-----------------------
  - Visit http://localhost:8000/blogs/get_blogs/
 
  - In output, we will see Roman Letters before a blog


Demonstration:
-----------------------

**Create welcome.js in static/blog/ and add the below code**

        function greet() {
            alert("Welcome to the blog app!");
        }

**Modify blogs.html template as below**

        <script src="{% static 'blog/welcome.js' %}"></script>
        <body onload="greet()">

Demonstration:
---------------------

**Show Output**

  - Visit http://localhost:8000/blogs/get_blogs/
  - Refresh the page

  Output

    - We will see the alert dialog popped up!

For script writer: Can create two folders as css and js to separate out css and js files in a directory.
Also showing an image can be shown here if time permits or else can be give as a slide or an assignment

**Concluding Slides**
