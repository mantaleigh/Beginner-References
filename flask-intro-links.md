# Relevant links (and starter code) for my Flask Intro presentation

* Virtual environments: http://docs.python-guide.org/en/latest/dev/virtualenvs/
* First of a series of Flask lectures from CS304: http://cs.wellesley.edu/~cs304/lectures/flask/flask.html

## Starter code (slide 6) 

```python
from flask import Flask
app = Flask(__name__)

@app.route('/')
def index(): 
  return '<h1>Hello world!</h1>'
  
@app.route('/about')
def about():
  return 'About Page'
```

## Variable Rules

```python
from flask import Flask
app = Flask(__name__)

@app.route('/')
def index():
    return 'Index Page'

@app.route('/about')
def about():
    return 'About Page'

@app.route('/hello/<name>')
def hello(name):
	# give the user a personalized greeting
    return '<h1>Hello, %s!</h1>' % name
```
