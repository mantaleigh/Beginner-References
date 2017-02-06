# Relevant links (and starter code) for my Flask Intro presentation

* Virtual environments: http://docs.python-guide.org/en/latest/dev/virtualenvs/
* First of a series of Flask lectures from CS304: http://cs.wellesley.edu/~cs304/lectures/flask/flask.html

## Starter code (slide 6) 

```python
from flask import flask
app = Flask(__name__)

@app.route('/')
def index(): 
  return '<h1>Hello world!</h1>'
  
if __name__ == '__main__': 
  app.run(debug = True)
  
```
