---
---

## Let's Create a New Model!

To start a new model, select `New` from the `File` menu. Begin by creating a setup button with the following steps:

1. Click the "Add" icon in the toolbar at the top of the Interface tab. 
1. On the menu next to Add, select Button (if it isn't already selected). 
1. Click wherever you want the button to appear in the empty white area of the Interface tab. 
1. A dialog box for editing the button opens. Type setup in the box labeled "Commands". 
1. Press the OK button when you're done; the dialog box closes.

Red sticky notes if this didn't work for you.

===

Now you have a setup button. 

Pressing the button runs a procedure called "setup". A procedure is a sequence of NetLogo commands that we assign a new name. We'll define that procedure soon. 

The button refers to a procedure that doesn't exist, so the button turns red. 

If you want to see the actual error message, click the button.

===

## Create the Setup Procedure

Swtich to the code tab and type:

~~~
to setup
  clear-all
  create-turtles 100 [ setxy random-xcor random-ycor ]
  reset-ticks
end
~~~
{:.text-document title='Code'}

Note: Every procedure begins with `to` and ends with `end`.

===

## Understanding the Setup Procedure

What do these lines of code do?

- `to setup` begins defining a procedure named "setup". 
- `clear-all` resets the world to an initial, empty state. All the patches turn black and any turtles you might have created disappear. Basically, it wipes the slate clean for a new model run. 
- `create-turtles 100` creates 100 turtles. They start out standing at the origin, that is, the center of patch 0,0. 
- After `create-turtles` we can put commands for the new turtles to run, enclosed by square brackets. 

===

- `setxy random-xcor random-ycor` is a command using "reporters". A reporter, as opposed to a command, reports a result. First each turtle runs the reporter random-xcor which will report a random number from the allowable range of turtle coordinates along the X axis. Then each turtle runs the reporter random-ycor, same for the Y axis. Finally each turtle runs the `setxy` command with those two numbers as inputs. That makes the turtle move to the point with those coordinates. 
- `reset-ticks` starts the tick counter, now that setup is otherwise complete. 
- `end completes` the definition of the "setup" procedure. 

Switch to the Interface tab and press the setup button you made before. Repeat to see the effects of the random initialization.

===

## Control the View

Now that we're using the tick counter (automatically created with `reset-ticks`), we should tell NetLogo that it only needs to update the view once per tick, instead of continuously updating it. 

- Find the view updates menu. It's above the view and by default says "continuous". 
- Choose "on ticks" instead. 

===

## Make the Go Button

Now make a button called "go". Follow the same steps you used to make the setup button, except: 

- For Commands enter `go` instead of `setup`. 
- Check the "Forever" checkbox in the edit dialog. 
- Check the "Disable until ticks start" checkbox too. 

The "Forever" checkbox makes the button stay down once pressed, so its commands run over and over again, not just once. 

The "Disable until ticks start" prevents you from pressing go before setup. 

===

## Add the Go Procedure

~~~
to go
  move-turtles
  tick
end
~~~
{:.text-document title='Code'}

`tick` is a primitive (i.e., built-in to NetLogo) that advances the tick counter by one tick. 

`move-turtles` is not, and we need to add another procedure. Note that it is common that one procedure might have (many) others nested within (i.e., dependencies).

===

## Add the Move Procedure

Add the `move-turtles` procedure after the `go` procedure: 

~~~
to move-turtles
  ask turtles [
    right random 360
    forward 1
  ]
end
~~~
{:.text-document title='Code'}

Note there are no spaces around the hyphen in `move-turtles`. Earlier, we used `red - 2`, with spaces, in order to subtract two numbers, but here we want `move-turtles`, without spaces. The "-" combines "move" and "turtles" into a single name.

===

Once finished adding the code, go back to the Interface, click `setup` to initialize and `go` to make your agents move.

Green sticky notes when you've gotten this to work.

===

## Coding Best Practices

Why couldn't we have just written all of these commands in `go` instead of in a separate procedure?

We could have, but during the course of building your model, it's likely that you'll add many other parts. We'd like to keep `go` as simple as possible, so that it is easy to understand. 

Eventually, it will include many other things you want to have happen as the model runs, such as calculating something or plotting the results. 

Each of these things to do will have its own procedure and each procedure will have its own unique name. 
