# Project 5: Linux Server Configuration
### by Stephen Harris
Linux Server Configuration project, part of the Udacity [Full Stack Web Developer
Nanodegree](https://www.udacity.com/course/full-stack-web-developer-nanodegree--nd004).

## What it is and does
Implements a secure WEB/APP server on the Amazon cloud using the LightSail platform to
standup a Ubuntu Linux server instance.  The following objects were met:
* Install Unbuntu and updated to latest
* Installed [SQLAlchemy](http://www.sqlalchemy.org/) 0.8.4 or higher (a Python SQL toolkit)
* Installed [Flask](http://flask.pocoo.org/) 0.10.1 or higher (a web development microframework)
* Installed the following Python packages:
    * oauth2client
    * requests
    * httplib2
* Installed Apache2 WWW server & WSGI libraries
* Installed GIT

This instance runs a web App named Software Development Languages Reference that is a reference to
software development languages that are categorized by language type.  A logged in user
based on their Facebook credentials can perform CRUD to maintain the reference data.  However
the Facebook integration requries that this server leverage HTTPS connection, however this would
require addiotional expense to setup Amazon Lightsail with HTTPS (load Balancer), certificates
and domain services.  So login capabilites will not be supported for this project.

## Required Libraries and Dependencies
The project code requires the following software:

* Python 2.7.x
* [SQLAlchemy](http://www.sqlalchemy.org/) 0.8.4 or higher (a Python SQL toolkit)
* [Flask](http://flask.pocoo.org/) 0.10.1 or higher (a web development microframework)
* The following Python packages:
    * oauth2client
    * requests
    * httplib2
* Apache2 & WSGI

## Project contents
This project consists of the following files in the `catalog` directory located in /var/www/catalog:

* `catalog.wsgi` - The main entry point for the solution.
* `fbClientSecrets.json` - Client secrets for Facebook OAuth login.
* `/catalog` - Directory containing the `catalog` package.
    * `/static` - Directory containing CSS and Javascript for the website.
        Includes a copy of the [Material Design Lite](http://www.getmdl.io/)
        web framework by Google and
        [JavaScript Cookie](https://github.com/js-cookie/js-cookie/), a JavaScript
        API for handling cookies.
    * `/templates` - Directory containing the HTML templates for the website, using
        the [Jinja 2](http://jinja.pocoo.org/docs/dev/) templating language for Python.
		* `home.html` - Home page, displays the latest 6 languages details.
		* `login.html` -  Enables a user to login using their Facebook credentials.	
		* `item.html` - Displays a individual language and it's details.
		* `items.html` - Displays all languages associated with a language category.
		* `myItems.html` - Displays all languages that were added by a user.
		* `itemAdd.html` - Allows a logged in user to add a new language.
		* `itemDelete.html` - Allows a logged in user to delete a language.
		* `itemEdit.html` - Allows a logged in user to edit a language.
		* `layout.html` - Provides a common layout for all other HTML pages.
    * `__init__.py` - Initialises the Flask libraries and exposes routes.
    * `authenicate.py` - Handles the login and logout of users using OAuth.
    * `dbConnect.py` - Function for connecting to the database.
    * `model.py` - Defines the database classes and creates an empty database.
    * `apis.py` - JSON response restful.
    * `createSampleDB.py` - creates a default database with 12 categories/6 languages.
    * `views.py` - Provides the views of the data and forms for creating, editing and 
	deleting languages.

## How to Run the Project
The catalog solution is a responsive design app.  
To access the main UI app @ http://udacity.homemations.com/

### Several JSON Endpoints to retrieve data based on RestFul APIs
* http://udacity.homemations.com/catalog/categorys.json/ - returns all categories.
* http://udacity.homemations.com/catalog/category/3.json/ - returns a single category based on ID.
* http://udacity.homemations.com/catalog/categoryname/Interpreted%20languages.json/ - returns a single category by name.
* http://udacity.homemations.com/catalog/items.json/ - returns all languages with details on each.
* http://udacity.homemations.com/catalog/item/1.json/ - returns a single item and details based on ID.
* http://udacity.homemations.com/catalog/itemname/Ada.json/ - returns a single item and details based on name.

## To access the instance
use the following command

```bash
ssh grader@udacity.homemations.com -p 2200 -i homemations
```

The homemations private key was provided in the project submission.  you will need
place this the contents of the submission in a file called homemations and place
in the directory where you run the above command.

The IP address of the server instance is 18.130.226.71 and SSH setup on port 2200

## The following configuration changes were completed:
* Changed SSH port from 20 to 2200
* Setup the Universal Fire wall (UFW) to only allow traffic on http, https, ssh (2200), ntp
* Add user 'grader' with rights to run sudo
* Setup WSGI and changed catalog.py to catalog.wsgi with changes to this file to support integration
* Added catalog.conf for the Apache configuration with /etc/apache2/available-sites

## List of 3rd party resources used:
* [SQLAlchemy](http://www.sqlalchemy.org/) 0.8.4 or higher (a Python SQL toolkit)
* [Flask](http://flask.pocoo.org/) 0.10.1 or higher (a web development microframework)
* [Apache] (https://httpd.apache.org/) 2.4.37 or higher (WEB/APP Server)
* [WSGI] (apt-get install libapache2-mod-wsgi) Supports Apache web integration with Python scripts
