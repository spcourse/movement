# Apple

## Goal
Write a program, called `apple.py`, that describes the movement of an apple falling from a height of 100 meters.

## Example
The program should output something like this:

    The apple hits the ground after ?.?? seconds with a speed of ???.?? km/h.
    The apple accelerates to 100 km/h in ?.?? seconds.

Where, of course, you should print actual values in stead of those question marks.

## Background

In physics a lot of research is done on problems that cannot be solved analytically (by hand). Nevertheless, there are a myriad of techniques that, often in a roundabout way, can generate solutions for these problems. In most cases such a technique is very laborious and always involves the aid of computers.

When simulating some physical system you take small steps in time and calculate crudely what happened in between each step. An example of such a system might be the movement of an object. The trick is to make those steps in time as small as possible, which makes the movement increasingly "fluid" as you calculate each step. This task is perfectly suitable for a computer since it involves many (similar) steps. Eventually a simulation describes almost exactly what would actually happen in reality. At least, if the simulation makes use of correct premises and assumptions!

So what do we need to know about the physics of a moving apple?

To calculate the position of the apple $$x$$ at a given time $$t$$, we need to calculate some other properties. We need to figure out the speed $$v$$ of the apple changes over time. And to know the speed changes, we need to know the acceleration $$a$$.

So how do all these four properties ($$x$$, $$v$$, $$a$$ and $$t$$) all depend on each other?

All object falling to earth have an acceleration of around $$9.8 m/s^2$$. This means every second the speed will increase by $$9.8 m/s$$.

> This is only true if there is no air resistance and if gravity pulls uniformly throughout any free fall. Which is not the case, but we're going to assume it is.

This means that the speed of the apple depends on how long it has been falling. To compute the speed of the apple after a specific time interval, $$\Delta t$$ is given by this equation:

$$v_{\rm new} = v_{\rm old} + a \cdot \Delta t$$

So, the new speed $$v_{\rm new}$$ is the old speed $$v_{\rm old}$$ plus the increase of speed $$a \cdot \Delta t$$

If the speed were constant, it would be very easy to also compute the change in height, but the speed isn't constant. What we will do is **assume that for a very small time interval $$\Delta t$$ the speed is constant**. When we do this we get:

$$x_{\rm new} = x_{\rm old} + v \cdot \Delta t$$

So, the new height $$x_{\rm new}$$ is the old height $$x_{\rm old}$$ plus the increase of height $$v \cdot \Delta t$$.

Putting it all together we can use the following algorithm (pseudo code) to **approximate** the fall of the apple:

    dt = 0.01
    t = 0, v = 0, x = 100, a = 9.8,
    repeat:
        x := x - v * dt  # update position (negative because we're going down)
        v := v + a * dt  # update speed
        t := t + dt      # update time

Note that `dt`, the time interval, is set to a small value. If you make this smaller, the simulation will be more precise, but also slower.

## Part 1

First let's see what happens with an apple that falls from a height of a 100 meters. After how many seconds and at what speed does the apple hit the ground?

### Specification

Create a file called `apple.py` and declare in it a function `simulate_apple1(x, dt)` that performs the necessary calculations. The function accepts two parameters:

- `x`: the starting height of the apple.
- `dt`: the time increment of our simulation.

The function should return two values:

- The time elapsed when the apple hits the ground (in seconds).
- The speed at which apple hits the ground (in km/h).

Call the function with the parameters 100 and 0.01, and print the results

### Hints

* Be careful with the *sign* of the powers and speeds. You start with a positive $$x$$ and move towards $$x=0$$.
* In this case you can also calculate the answers yourself using pen and paper.
* First calculate everything in meters per second (m/s) and convert everything to kilometers per hour (km/h) after the simulation is finished.

## Part 1

How quickly does a falling apple accelerate? Is that faster than a Bugatti Veyron?
A Bugatti Veyron accelerates from 0 to 100km/h in [2.46](https://en.wikipedia.org/wiki/Bugatti_Veyron#Specifications_(all_variants)) seconds. Let's see how quickly the apple gets to that speed.

### Specification

Declare a function `simulate_apple2(dt)` that performs the necessary calculations. The function accepts one parameters:

- `dt`: the time increment of our simulation.

It should simulate the fall of the apple until it reaches a speed of 100 km/h. You don't need a height parameter, as you can just assume the apple is dropped from high enough that it won't hit the ground before it reaches this speed.

The function should return one value:

- The time elapsed (in seconds) before reaching a speed of 100km/h.

Is it faster than the Bugatti?

## Testing



<!-- checkpy apple -->
