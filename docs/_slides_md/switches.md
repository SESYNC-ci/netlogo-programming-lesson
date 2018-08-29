---
---

## Switches and Labels

What else is going on that we can track? Turtles are gaining and losing energy as they move around and graze.

Let's create a switch to allow us to toggle energy reporting on and off.

- Click on the "Add" icon on the toolbar (in the Interface tab). 
- Select "Switch" from the menu next to "Add". 
- Click on an open spot in the interface. 

A dialog will appear.

- Into the Global variable field, type `show-energy?`
- Don't forget to include the question mark in the name.

===

## Add Energy Switch procedure

Go back to the `go` procedure in the Code tab.
 
Rewrite the `eat-grass procedure` as follows: 

~~~
to eat-grass
  ask turtles [
    if pcolor = green [
      set pcolor black
      set energy energy + 10
    ]
  ifelse show-energy?
    [ set label energy ]
    [ set label "" ]
  ]
end
~~~
{:.text-document title='Code'}

===

Go back to the Interface, toggle the energy switch to "on", and click the "setup" and "go" buttons.

Green sticky notes when you get this to work.

===

## How Does `ifelse` Work?

The `eat-grass` procedure introduces the `ifelse` command.

Each turtle, when it runs these new commands, checks the value of `show-energy?` (determined by the switch). 

If the switch is on, comparison is true, and the turtle will run the commands inside the first set of brackets. In this case, it assigns the value for the energy to the label of the turtle.

If the comparison is false (the switch is off) then the turtle runs the commands inside the second set of brackets. In this case, it removes the text labels (by setting the label of the turtle to be nothing with an empty text string). 
