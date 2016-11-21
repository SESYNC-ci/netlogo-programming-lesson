---
---

## More Dynamics and Behavior

Now our turtles are eating. Let's make them reproduce and die, and have the grass grow back.

We'll add all three of these behaviors now, by making three separate procedures, one for each behavior.

Rewrite the `go` procedure as follows to add more procedures:

~~~
to go
  move-turtles
  eat-grass
  reproduce
  check-death
  regrow-grass
  tick
end
~~~
{:.text-document title='{{ site.worksheet }}'}

===

## Procedure for reproduction

Add the procedures for `reproduce`, `check-death`, and `regrow-grass`, starting with `reproduce`  as shown below: 

~~~
to reproduce
  ask turtles [
    if energy > 50 [
      set energy energy - 50
      hatch 1 [ set energy 50 ]
    ]
  ]
end
~~~
{:.text-document title='{{ site.worksheet }}'}

===

## Interpreting the `reproduce` procedure

When each turtle runs `reproduce`, it checks the value of the turtle's energy variable. 

If it is greater than 50, then the turtle runs the commands inside the first set of brackets. 

In this case, it decreases the turtle's energy by 50, then "hatches" a new turtle with an energy of 50. 

The hatch command is a NetLogo primitive which looks like this: hatch number [ commands ]. This turtle creates number new turtles, each identical to its parent, and asks the new turtle(s) that have been hatched to run commands. You can use the commands to give the new turtles different colors, headings, or whatever. In our case we run one command. We set the energy for the newly hatched turtle to be 50.

===

## Procedure for death

Add the following code for `check-death`:

~~~
to check-death
  ask turtles [
    if energy <= 0 [ die ]
  ]
end
~~~
{:.text-document title='{{ site.worksheet }}'}

===

## Interpreting the `check-death` procedure

Each turtle, when it runs check-death it will check to see if its energy is less or equal to 0. 

If this is true, then the turtle is told to die (die is a NetLogo primitive).

===

## Procedure for regrowing the grass

Add the procedures for `regrow-grass` as shown below:

~~~
to regrow-grass
  ask patches [
    if random 100 < 3 [ set pcolor green ]
  ]
end
~~~
{:.text-document title='{{ site.worksheet }}'}

===

## Interpreting the `regrow-grass` procedure

When each patch runs `regrow-grass` it will check to see if a random integer from 0 to 99 is less than 3. 

If so, the patch color is set to green. This will happen 3% of the time (on average) for each patch, since there are three numbers (0, 1, and 2) out of 100 possible that are less than 3. 

===

## Run it!

Go back to the Interface, toggle the energy switch to "off", and click the "setup" and "go" buttons.

Green sticky notes when you get this to work.

What do you notice about the dynamics? How is this communicated through the Monitors?
