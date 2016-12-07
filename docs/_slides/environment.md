---
---

## Creating an Environment

Now we've got 100 turtles aimlessly moving around, completely unaware of anything else around them. Let's create a structured environemnt through which they will move.

Go back to the `setup` procedure. We can rewrite it as follows: 

~~~
to setup
  clear-all
  setup-patches
  setup-turtles
  reset-ticks
end
~~~
{:.text-document title='Code'}

The new definition of `setup` refers to two new procedures we need to define.

===

To define `setup-patches`, add this: 

~~~
to setup-patches
  ask patches [ set pcolor green ]
end
~~~
{:.text-document title='Code'}

The `setup-patches` procedure sets the color of every patch to green to start with.

===

The only part remaining in our new `setup` that is still undefined is setup-turtles. Add this procedure too:

~~~
to setup-turtles
  create-turtles 100
  ask turtles [ setxy random-xcor random-ycor ]
end
~~~
{:.text-document title='Code'}

Go back to the interface, click "setup" and "go".

Green sticky notes when you've gotten this to work.

===

## Adding Turtle Attributes and Behavior

Thus far, our turtles are just running around. Let's add some interaction between the turtles and the patches. 

We'll make the turtles eat "grass" (the green patches), reproduce, and die. The grass will change color and gradually grow back after it is eaten.

We'll need a way of controlling when a turtle reproduces and dies. We'll determine that by keeping track of how much "energy" each turtle has. To do that we need to add a new turtle variable. 

===

You've already seen built-in turtle variables like `color`. To make a new turtle variable, we add a `turtles-own` declaration at the top of the Code tab, before all the procedures. 

Call it energy: 

~~~
turtles-own [energy]
~~~
{:.text-document title='Code'}

===

## Rewrite the Go procedure

Let's use this newly defined variable (energy) to allow the turtles to eat. Go down to the `go` procedure and rewrite as:

~~~
to go
  move-turtles
  eat-grass
  tick
end
~~~
{:.text-document title='Code'}

===

## The `if` statement

A turtle has direct access to the variables of the patch it is standing on. We want each turtle to determine whether the value of the patch color it is on (pcolor) is "green", and if so, to gain energy by eating grass.

Add a new `eat-grass` procedure below the `move-turtle` procedure: 

~~~
to eat-grass
  ask turtles [
    ...
    ]
  ]
end
~~~
{:.text-document title='Code'}

===

An "if statement" allows the program to exectue one procedure if and only if the patch color is green. Only then will the turtle run commands given inside brackets and following the test:

~~~
to eat-grass
  ask turtles [
    if pcolor = green [
      set pcolor black
      set energy energy + 10
    ]
  ]
end
~~~
{:.text-document title='Code'}

The commands make the turtle change the patch color to black and increase its own energy by 10. The patch turns black to signify that the grass at that spot has been eaten.

===

## Movement Costs Energy

Next, let's make the movement of turtles use up some of the turtle's energy. 

Rewrite `move-turtles` as follows: 

~~~
to move-turtles
  ask turtles [
    right random 360
    forward 1
    set energy energy - 1
  ]
end
~~~
{:.text-document title='Code'}

Switch back to the Interface, click "setup" and "go", and watch your turtles graze!

Green sticky notes when you get this to work.
