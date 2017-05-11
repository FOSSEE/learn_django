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
		- Use Python 3
	- Use venv
	- Installing Django using pip
		- Test successful installation using *python -m django --version*

3.  Create your first Django Project
	-  *django-admin startproject <name>*
	-  Show file structure
	-  Describe the *settings.py* file
	-  Run the Test Page using *python manage.py runserver*

4. Create your first Django app
	*Create a micro-blogging application*
	- Use management command *python manage.py startapp <name>*
	- Show the file structure 
	- Modify the *settings.py* file
		- Show database settings
		- Add app_name to INSTALLED_APPS variable
		- Show other relevant variables

5.  Django Models
	- What is a Django model
	- Create table
		- *Tweet*
			- post
			- author
			- created_date
	- Explain that Django is based on MVC architecture
	- Explain M - Models in MVC

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
	- Explain V - Views in MVC

9. Django Templates
	- Show file structure & create */templates/* directory
	- Create a HTML template
		- Describe template tags

10. Summary of Topics covered so Far
	- Block Diagram explanation of MVC and Django
		- Show fig. explaining relationship between urls, views, models and forms

11. Django Forms
	- Create a custom form to add tweets
	- Add a new view for submitting new tweets

12. Django Querysets
	- Add a simple search filter
	- Add a form and a view for search
	- Explain Querysets
	- Point to docs
	
11. Styling and better Templates
	- Adding CSS styles, Javascript and other Static assets
		- Making changes to settings
		- Adding static directory

12. Adding more functionality
	- Add User registration 
	- Add Login

Advanced Topics
----------------

13. More about Django Admin
	- User management
	- Group and Permission management

14. What are Migrations

15. Testing Django Views & Models
