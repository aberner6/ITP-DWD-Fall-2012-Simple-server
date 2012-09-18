## A simple webserver in Python 
Simple example of a web server using Python's [Flask web framework](http://flask.pocoo.org/). 

------

### Reference Links

* Flask - micro web framework [http://flask.pocoo.org/](http://flask.pocoo.org/)
* Heroku registration - [https://api.heroku.com/signup](https://api.heroku.com/signup)
* Heroku Toolbelt (download) - [https://toolbelt.heroku.com/](https://toolbelt.heroku.com/)

### Requirements

* Tested on Python 2.7.x
* You should have [Python](http://www.python.org/download/), Python [Setuptools](http://pypi.python.org/pypi/setuptools#downloads) and PIP installed (run cmd "easy_install pip").


### Setup before initially running server

Before you run the simple server example below you must install the Flask module. Flask is the Python framework used in this example web server.

To install Flask run the following command in your Terminal console.

	pip install flask

This will download Flask and all of its requirements (Werkzeug & Jinja2)

For this example you only need to install Flask once. It will then be available for all future Python scripts that import it. 

**NOTE: future web servers in the ITP DWD class will be running with Virtualenv, to encapsulate all required modules/libraries. The ITP DWD class will be installing with PIP with an alternative command. **


------

### Running the basic server

#### Download [code for web.py](https://github.com/johnschimmel/ITP-DWD-Fall-2012-Simple-server/blob/master/web.py)

Download the code. To keep your code organized it helps to put example files in their own directory, creating a directory in ~/Documents called 'itp-dwd-examples' is helpful.

Navigate to the directory via Terminal, for example

	cd ~/Documents/itp-dwd-examples

When you are inside the code directiory, run the server with the command

	python web.py

If successful, a simple web server is now running on your computer. Open your browser and visit [http://localhost:5000](http://localhost:5000)

Two pages are available
* [/](http://localhost:5000) - the main page
* [/page2](http://localhost:5000/page2)- a second example page

### Inside the code

There are four things happening in this code

1. Importing modules. The **import** and **from** keyword commands tell the script to include certain code libraries ([understanding imports](http://learnpythonthehardway.org/book/ex40.html) see an example from Learn Python the Hard Way). 


		import os	# import the operating system module
		from flask import Flask 	# Retrieve Flask, our framework


2. Create the Flask app

		
		app = Flask(__name__)	
		# __name__ is a Python variable that holds the name of the module, currently it is '__main__'

3. Routes. Routes provide a resource path for your clients to access. In Flask, routes are configured with the use of Python decorators (read more about decorators). The decorate is prefixed with **@** symbol and it will "wrap" the Python function directly below itself.

		# Main Page Route
		@app.route("/")
		def index():
    		return "Hello World!<br/><br/><a href='/page2'>Visit page #2</a>"

    	# Second Page Route
		@app.route("/page2")
		def page2():
			return """<html><body>
			<h2>Welcome to page 2</h2>
			<p>This is just amazing!</p>
			</body></html>"""

4. Start the server. If the __name__ of the module is '__main__', this script is not being imported by another, turn on debug mode and turn on the server.
	
		if __name__ == "__main__":
			app.debug = True	# enables auto restarting of server when code changes
			app.run()	# turns server on, ready for requests


Running the script will turn on the server and allow it to accept requests.

------


### Stopping the server

You can stop the server by pressing the CTRL+C keys inside the Terminal.

------

### Running the second web server example

#### Download [code for web_w_form.py](https://github.com/johnschimmel/ITP-DWD-Fall-2012-Simple-server/blob/master/web_w_form.py)

The second web server example has a third page that demonstrates a simple web form. When the server receives a 'GET' request to '/form' it responds with a form. If the user fills in the form and submits the server receives a 'POST' request with the form data. The server responds with a custom made HTML string using the user form data.

* /form - to display a simple web form and a receive form submission.

Run the server with the command

	python web_w_form.py

If successful, a simple web server is now running on your computer. Open your browser and visit [http://localhost:5000](http://localhost:5000)


### Inside the '/form' route

1. Route has 2nd argument to define acceptable HTTP request methods. By default Flask only provides 'GET'. We have the option to use 'GET','POST','PUT','DELETE'. We will usually be using only 'GET' and 'POST'

		@app.route("/form", methods=["GET","POST"])


2. 'GET' or 'POST'

		def simpleform():

			# Did the client make a POST request?
			if request.method == "POST":

				# get the form data submitted and store it in a variable
				user_name = request.form.get('user_name', 'Tim Berners-Lee')

				# return custom HTML using the user submitted data
				return "<html><body><h2>HELLO %s! What an interesting name.</h2><br><a href='/form'>back to form</a></body><html>" % user_name

			else:

				# client made a GET request for '/form'
				# return a simple HTML form that POSTs to itself
				return """<html><body>
				<form action="/form" method="POST">
					What's your name? <input type="text" name="user_name" id="user_name"/>
					<input type="submit" value="submit it"/>
				</form>
				</body></html>"""


