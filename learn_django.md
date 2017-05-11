Django Tutorial Outline
===================

1. Introduction
	- How a server application works
		- Using requests, server-side code and database to store data
	- What is a Web Framework.
	- Why Django should be used.
	- Where Django is used. 

2. Installing Django
	- System Requirements
	- Installing pip
	- Installing Django using pip
		- Test successful installation using *python -m django --version*

3. Overview of Django
	- What is MVC architecture
	- Block Diagram explanation of MVC
		- Show fig. explaining relationship between urls, views, models and forms

3.  Create your first Django Project
	-  *django-admin startproject <name>*
	-  Show file structure

4. Create your first Django app
	*Create a micro-blogging application*
	- Use management command *python manage.py startapp <name>*
	- Show the file structure 
	- Describe and Modify the *settings.py* file
		- Show database settings
		- Add app_name to INSTALLED_APPS variable
		-  Show other relevant variables

5.  Django Models
	- What is a Django model
	- Create table
		- *Tweet*
			- post
			- author
			- created_date

6. Django Admin
	- Create a superuser
	- Modify *admin.py* file, add *Tweet* model
	- Demonstrate usage of admin interface
		- Open the interface
		- Save a tweet
		- View the tweet

7. Django Urls
	- Modify *urls.py* file of the app and project and add a custom url

8. Django views
	- Add a simple view to display all tweets

9. Django Templates
	- Show file structure & create */templates/* directory
	- Create a HTML template
		- Describe template tags

10. Django Querysets
	- Add a simple filter and explain Querysets
	- Point to docs

11. Django Forms
	- Create a custom form to add tweets
	- Add a new view for submitting new tweets

12. Adding more functionality
	- Add User registration 
	- Add Login
