---
---

## Creating an Environment

Now we've got 100 turtles aimlessly moving around, completely unaware of anything else around them. Let's create a structured environemnt through which they will move.

Go back to the `setup` procedure. We can rewrite it as follows: 

to setup
  clear-all
  setup-patches
  setup-turtles
  reset-ticks
end

The new definition of `setup` refers to two new procedures we need to define.

===

To define `setup-patche`s, add this: 

~~~
to setup-patches
  ask patches [ set pcolor green ]
end
~~~
{: .input}

The `setup-patches` procedure sets the color of every patch to green to start with.

===

The only part remaining in our new `setup` that is still undefined is setup-turtles. Add this procedure too:

~~~
to setup-turtles
  create-turtles 100
  ask turtles [ setxy random-xcor random-ycor ]
end
~~~
{: .input}

Go back to the interface, click "setup" and "go".

Green sticky notes when you've gotten this to work.

===

### Adding `turtle` Attributes and Behavior

Thus far, our turtles are just running around. Let's add some interaction between the turtles and the patches. 

We'll make the turtles eat "grass" (the green patches), reproduce, and die. The grass will change color and gradually grow back after it is eaten. 

We'll need a way of controlling when a turtle reproduces and dies. We'll determine that by keeping track of how much "energy" each turtle has. To do that we need to add a new turtle variable. 

===

You've already seen built-in turtle variables like `color`. To make a new turtle variable, we add a `turtles-own` declaration at the top of the Code tab, before all the procedures. 

Call it energy: 

~~~
turtles-own [energy]
~~~
{: .input}

===

Rewrite the Go procedure

Let's use this newly defined variable (energy) to allow the turtles to eat. Go down to the `go` procedure and rewrite as:

~~~
to go
  move-turtles
  eat-grass
  tick
end
~~~
{: .input}

Add a new `eat-grass` procedure below the `move-turtle` procedure: 

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
{: .input}

===

### How does the `if` statement work?

Each turtle, when it runs these commands, compares the value of the patch color it is on (pcolor) to the value for green. (A turtle has direct access to the variables of the patch it is standing on.) 

If the patch color is green, the comparison reports true, and only then will the turtle run the commands inside the brackets (otherwise it skips them). 

The commands make the turtle change the patch color to black and increase its own energy by 10. The patch turns black to signify that the grass at that spot has been eaten.

===

### Movement costs energy

Next, let`s make the movement of turtles use up some of the turtle`s energy. 

Rewrite move-turtles as follows: 

~~~
to move-turtles
  ask turtles [
    right random 360
    forward 1
    set energy energy - 1
  ]
end
~~~
{: .input}

Switch back to the Interface, click "setup" and "go", and watch your turtles graze!

Green sticky notes when you get this to work.
