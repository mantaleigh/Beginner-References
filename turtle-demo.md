## Notes

All of the following are for use with the Python turtle module, assuming the turtle is named `t`:

    import turtle
    t = turtle.Turtle()
    
Check out the documentation here: https://docs.python.org/2/library/turtle.html
to see what other types of things you can do with your turtle that aren't listed here. 

---------------------------
## Demos

### Change Direction

**The number in the parens is the angle to turn.**

    t.left(90)
    t.right(45)

### Move

**The number in the parens is the numbet of pixels to move.**

    t.forward(100)
    t.backward(50)

### Change Color

    t.color("blue")
    t.color("red")
    t.color("#ffff00")

### Pen Up & Down

    t.penup()
    t.pendown()

### What if we want to repeat instructions? 

  **The number in `range()` is the number of times the instructions in the loop are executed**

    for x in range(4):
        t.forward(100)
        t.left(90)
        
  _What does this make?_

_Actually, these loops aren't part of turtles specifically, they're part of Python! (and most other programming languages)_



## CHALLENGES: 

### Challenge 1: 

Can you figure out a way to draw a circle using 1 line of code? Hint: look at the documentation link above.

### Challenge 2: 

Write your name using the turtle! 

**Make it harder**: Make each letter of your name a different color.

### Challenge 3:

Create some flowers like the one I did before! Mine isn't very good, though. Try to make it look more realistic!

![Red "flower"](http://i.imgur.com/eWwdPH3.png "Red 'flower'")

Extra challenge: create the above flower using only 4 lines of code!
