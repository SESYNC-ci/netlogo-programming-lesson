---
---

## Sliders

In case you don't want to start with the same parameter value each time, sliders are an easy and intuitive way to modify parameters.

Let's vary the number of turtles we start with.

- Create a slider named "number-of-turtles": click the Add icon on the toolbar, select Slider next to it, and click on an open spot in the interface. 
- Then inside of setup-turtles, instead of create-turtles 100 you can type: 

~~~
to setup-turtles
  create-turtles number-of-agents
end
~~~
{:.text-document title='Code'}

Go back to the Interface, move the slider to change the number of agents, and click "setup" and "go".

Red sticky notes if this did not work for you.

===

## More Sliders

Adjust the energy the turtles gain and lose as they eat grass and reproduce.

Make a slider called "energy-from-grass". 

Then, inside of `eat-grass`, make this change: 

~~~
to eat-grass
  ask turtles [
    if pcolor = green [
      set pcolor black
      set energy energy + energy-from-grass
    ]
    ifelse show-energy?
      [ set label energy ]
      [ set label "" ]
  ]
end
~~~
{:.text-document title='Code'}

===

Make another slider called "birth-energy". 

Inside of `reproduce`, make this change: 

~~~
to reproduce
  ask turtles [
    if energy > birth-energy [
      set energy energy - birth-energy
      hatch 1 [ set energy birth-energy ]
    ]
  ]
end
~~~
{:.text-document title='Code'}

===

## Challenge

Are there other parameters that could be varied? Write one or more sliders for these parameters.

(Hint: grass regrowth rate, movement of turtles ....)
