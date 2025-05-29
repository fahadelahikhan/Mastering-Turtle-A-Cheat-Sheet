# Turtle Cheat Sheet

# Complete Python Turtle Graphics Cheat Sheet

## Quick Start Setup

```python
import turtle

# Method 1: Object-oriented (recommended)
t = turtle.Turtle()
screen = turtle.Screen()

# Method 2: Functional (quick start)
from turtle import *

```

## Essential Screen Setup

```python
screen = turtle.Screen()
screen.setup(width, height)              # Set window size
screen.bgcolor("color")                  # Background color
screen.title("Your Title")               # Window title
screen.colormode(255)                    # Enable RGB 0-255 values
screen.setworldcoordinates(llx, lly, urx, ury)  # Custom coordinate system

```

## Movement Commands

### Basic Movement

```python
# Forward/Backward
t.forward(distance)    # t.fd(distance) - Move forward
t.backward(distance)   # t.bk(distance), t.back(distance) - Move backward

# Turning
t.right(angle)         # t.rt(angle) - Turn right by degrees
t.left(angle)          # t.lt(angle) - Turn left by degrees

# Direct positioning
t.goto(x, y)           # Move to specific coordinates
t.setx(x)              # Set x-coordinate only
t.sety(y)              # Set y-coordinate only
t.setheading(angle)    # t.seth(angle) - Set absolute heading
t.home()               # Return to (0,0) facing east (0°)

```

## Pen Control

### Pen State

```python
t.penup()              # t.up(), t.pu() - Lift pen (no drawing)
t.pendown()            # t.down(), t.pd() - Lower pen (draw)
t.isdown()             # Check if pen is down (returns True/False)

```

### Pen Appearance

```python
t.pensize(width)       # t.width(width) - Set line thickness
t.pencolor("color")    # Set pen color
t.fillcolor("color")   # Set fill color for shapes
t.color("pen_color", "fill_color")  # Set both colors
t.color("color")       # Set both pen and fill to same color

```

## Drawing Shapes & Patterns

### Basic Shapes

```python
t.circle(radius)                    # Draw complete circle
t.circle(radius, extent)            # Draw arc (extent in degrees)
t.circle(radius, extent, steps)     # Draw polygon approximation
t.dot(size)                         # Draw filled circle dot
t.dot(size, "color")                # Colored dot

```

### Filling Shapes

```python
t.begin_fill()         # Start filling mode
# Draw your shape here
t.end_fill()           # End filling and fill the enclosed area

```

### Writing Text

```python
t.write("text")        # Write at current position
t.write("text", align="center", font=("Arial", 16, "bold"))
# align options: "left", "center", "right"
# font styles: "normal", "bold", "italic"

```

## Turtle Appearance & Behavior

### Speed Control

```python
t.speed(speed)         # Set animation speed
# Values: 1-10 (1=slowest, 10=fastest), 0=no animation
# Strings: "slowest", "slow", "normal", "fast", "fastest"

```

### Turtle Visibility & Shape

```python
t.showturtle()         # Make turtle visible
t.hideturtle()         # Hide turtle cursor
t.shape("shape_name")  # Change turtle shape
# Shapes: "arrow", "turtle", "circle", "square", "triangle", "classic"

```

### Stamps & Cloning

```python
stamp_id = t.stamp()   # Leave turtle shape impression
t.clearstamp(stamp_id) # Remove specific stamp
t.clearstamps()        # Remove all stamps

```

## Information & State Queries

### Position & Orientation

```python
t.position()           # t.pos() - Get (x, y) coordinates
t.xcor()               # Get x-coordinate
t.ycor()               # Get y-coordinate
t.heading()            # Get current heading angle (0-360°)

```

### Distance & Direction

```python
t.distance(x, y)       # Distance to point (x, y)
t.towards(x, y)        # Angle toward point (x, y)

```

## Colors & Styling

### Color Formats

```python
# Named colors
t.color("red")

# Hex colors
t.color("#FF0000")

# RGB tuples (0.0-1.0 by default)
t.color((1.0, 0.0, 0.0))

# RGB values (0-255 with colormode(255))
screen.colormode(255)
t.color((255, 0, 0))

```

### Common Color Names

```
"red", "blue", "green", "yellow", "orange", "purple", "pink",
"brown", "black", "white", "gray", "grey", "cyan", "magenta",
"lime", "navy", "olive", "maroon", "silver", "gold"

```

## Animation & Performance Control

### Screen Updates

```python
screen.tracer(0)       # Turn off animation (faster drawing)
screen.update()        # Manually update screen
screen.tracer(1)       # Turn animation back on
screen.tracer(n)       # Update every n-th regular screen update

```

## Event Handling

### Mouse Events

```python
def click_handler(x, y):
    t.goto(x, y)

screen.onclick(click_handler)        # Handle mouse clicks
screen.onscreenclick(click_handler)  # Same as onclick

```

### Keyboard Events

```python
def move_up():
    t.setheading(90)
    t.forward(20)

screen.onkey(move_up, "Up")     # Handle key press
screen.onkeypress(move_up, "Up") # Handle key press (alternative)
screen.listen()                  # Start listening for events

```

## Program Control & Termination

### Keeping Window Open

```python
screen.exitonclick()   # Close when screen is clicked
screen.mainloop()      # Keep window open indefinitely
turtle.done()          # Alternative to mainloop()

```

## Coordinate System & Angles

### Understanding the Grid

- **Origin (0,0)**: Center of screen
- **X-axis**: Increases rightward, decreases leftward
- **Y-axis**: Increases upward, decreases downward

### Angle System

- **0°**: East (right)
- **90°**: North (up)
- **180°**: West (left)
- **270°**: South (down)

## Essential Patterns & Examples

### Basic Shapes

```python
# Square
for i in range(4):
    t.forward(100)
    t.right(90)

# Triangle
for i in range(3):
    t.forward(100)
    t.right(120)

# Star
for i in range(5):
    t.forward(100)
    t.right(144)

# Hexagon
for i in range(6):
    t.forward(100)
    t.right(60)

```

### Filled Circle

```python
t.fillcolor("yellow")
t.begin_fill()
t.circle(50)
t.end_fill()

```

### Spirals

```python
# Square spiral
for i in range(100):
    t.forward(i)
    t.right(90)

# Circular spiral
for i in range(100):
    t.forward(i)
    t.right(91)

```

### Random Walk

```python
import random
for i in range(100):
    t.forward(20)
    t.right(random.randint(0, 360))

```

## Advanced Techniques

### Multiple Turtles

```python
t1 = turtle.Turtle()
t2 = turtle.Turtle()
t1.color("red")
t2.color("blue")
# Control each turtle independently

```

### Custom Shapes

```python
# Register custom shape
shape = ((0, 0), (10, 10), (20, 0), (10, -10))
screen.register_shape("diamond", shape)
t.shape("diamond")

```

### Coordinate Transformations

```python
# Save current state
pos = t.position()
heading = t.heading()

# Do some drawing...

# Restore state
t.goto(pos)
t.setheading(heading)

```

## Performance Tips

1. **Use `screen.tracer(0)`** for complex drawings
2. **Set `speed(0)`** for fastest drawing
3. **Hide turtle** with `hideturtle()` during drawing
4. **Update manually** with `screen.update()`

## Common Debugging Tips

1. **Add `screen.exitonclick()`** to prevent window from closing
2. **Use `print(t.position())`** to debug positioning
3. **Add delays** with `time.sleep(1)` if drawing too fast
4. **Check pen state** with `t.isdown()`

## Complete Template

```python
import turtle
import random  # if using random functions

# Setup
screen = turtle.Screen()
screen.setup(800, 600)
screen.bgcolor("white")
screen.title("My Turtle Art")
screen.colormode(255)  # if using RGB values

# Create turtle
artist = turtle.Turtle()
artist.speed(0)  # Fastest
artist.shape("turtle")
artist.color("blue")

# Optional: Turn off animation for complex drawings
screen.tracer(0)

# Your drawing code here
for i in range(4):
    artist.forward(100)
    artist.right(90)

# Update screen if tracer was turned off
screen.update()

# Keep window open
screen.exitonclick()

```

## Quick Reference Summary

| Category | Key Functions |
| --- | --- |
| **Movement** | `forward()`, `backward()`, `right()`, `left()`, `goto()` |
| **Pen** | `penup()`, `pendown()`, `pencolor()`, `fillcolor()` |
| **Shapes** | `circle()`, `dot()`, `begin_fill()`, `end_fill()` |
| **Info** | `position()`, `heading()`, `distance()`, `towards()` |
| **Control** | `speed()`, `tracer()`, `update()`, `exitonclick()` |

This comprehensive cheat sheet covers everything from basic turtle movement to advanced event handling and performance optimization, making it your complete reference for Python turtle graphics!
