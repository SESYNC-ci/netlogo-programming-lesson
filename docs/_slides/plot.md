---
---

## Plotting

Wouldn't it be nice if we had a easier way to track the changes in the model behavior over time? 

Fortunately, NetLogo allows us to plot data as we go along.

To make plotting work, we'll need to create a plot in the Interface tab and put some commands inside it. 

===

## Create a plot

The commands we put in the plots will run automatically when our setup procedure calls reset-ticks and when our go procedure calls tick.

- Create a plot by clicking the "Add" icon on the toolbar, selecting "Plot" next to it, and clicking on an open spot in the Interface. 
- Set its Name to "Totals"
- Set the X axis label to "time" 
- Set the Y axis label to "totals" 
- Change the name of the "default" pen to "turtles". 
- Enter plot count turtles under "Pen Update Commands". 
- Press the "Add Pen" button.
- Change the name of the new pen to "grass". 
- Enter `plot count patches with [pcolor = green]` under "Pen Update Commands".
- Press OK in the Plot dialog to finish editing. 

Go back to the Interface and click the "setup" and "go" buttons.

Green sticky notes when you get this to work.

===

## Plotting notes

1. There are not labels for the lines in the plot. Mouse over the Interface and you'll notice that your cursor turns to cross-hairs. Click and hold while dragging over some part of the plot until it is highlighted. Now the plot is selected. Notice that the Edit and Delete buttons are no longer greyed-out. Click Edit to open the plot dialog, and then click the "Show Legend?" box.

1. When you create the plot you can also set the minimum and maximum values on the X and Y axes. You'll want to leave the "Auto Scale" checkbox checked, so that if anything you plot exceeds the minimum and maximum values for the axes, the axes will automatically grow so you can see all the data. 

1. The term "pen" is a little weird, right? But here's the raionale ... we used the plot command to add the next point to a plot. This command moves the current plot pen to the point that has an X coordinate equal to 1 greater than the previously plotted X coordinate and a Y coordinate equal to the value given in the plot command (in the first case, the number of turtles, and in the second case, the number of green patches). As the pens move they each draw a line. 

===

## Tick counter

To make comparisons between plots from one model run and another, it is often useful to do the comparison for the same length of model run. This can be done by stopping or starting an action at a specific time by stopping the model at the same point each model run. 

Keeping track of how many times the `go` procedure is run is a useful way to cue these actions. That's what the tick counter does. You're already using the tick counter in your model, with the `reset-ticks` and `tick` commands, which also trigger plotting. 

You can also use the tick counter for other things, such as to set a limit on the total length of a run. 

===

## Set the limit of a model run

Change the go procedure: 

~~~
to go
  if ticks >= 300 [ stop ]
  move-turtles
  eat-grass
  check-death
  reproduce
  regrow-grass
  tick
end
~~~
{:.text-document title='Code'}

Now setup and run the model. 

Green sticky notes if your model runs and then stops on tick 300.
