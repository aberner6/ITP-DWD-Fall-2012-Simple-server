## A simple webserver in Python 
Simple example of a web server using Python's Flask web framework. 

------

### Requirements

Tested on Python 2.7.x
You should have [Python](http://www.python.org/download/), Python [Setuptools](http://pypi.python.org/pypi/setuptools#downloads) and PIP installed (run cmd "easy_install pip").


### Setup before initially running server

Before you run the server you must install the Flask module. Flask is the Python framework used in this example web server.

To install Flask run the following command in your Terminal console.

	pip install flask

This will download Flask and all of its requirements (Werkzeug & Jinja2)

For this example you only need to install Flask once. It will then be available for all future Python scripts that import it. 

**HOWEVER, future web servers in the ITP DWD class will be running with Virtualenv, to encapsulate all required modules/libraries.**


------

### Running the basic server

Download the code. To keep your code organized it helps to put example files in their own directory, creating a directory in ~/Documents called 'itp-dwd-examples' is helpful.

Navigate to the directory via Terminal, for example

	cd ~/Documents/itp-dwd-examples

When you are inside the code directiory, run the server with the command

	python web.py

If successful, a simple web server is now running on your computer at [http://localhost:5000](http://localhost:5000)

### Stopping the server

You can stop the server by pressing the CTRL+C keys inside the Terminal.

Two pages are available
* [/](http://localhost:5000) - the main page
* [/page2](http://localhost:5000/page2)- a second example page


------

### Running the second web server example

This server has the same pages as the previous example plus 

* /form - to display a simple web form and a receive form submission.

Run the server with the command

	python web_w_form.py

