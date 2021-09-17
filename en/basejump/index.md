# Free fall during a base jump

Write a program in which the fall of a base jumper is plotted. The base jumper is jumping from a height of 1000m, and at 200 meters he will open his parachute. Assume this base jumper weighs 72 kilograms.

## Background

In the previous assignment the air friction was neglected, which made it possible to verify the answer using relatively simple physics equations. Now we're going to add back a layer of realism: air friction.

Although air resistance is dependent on the surface and mass of the object and the density of the air, we'll only be examining the effect of speed in this assignment. Because of the friction, there exists a speed in which gravity and air friction keep each other in balance. The maximum speed a parachutist can achieve is about 196 km/h and is called [terminal velocity](https://en.wikipedia.org/wiki/Terminal_velocity).

![](../../assets/Freefall.png)

As always there are people trying to find the [limits](https://en.wikipedia.org/wiki/Speed_skydiving). Because he started his jump in an area where air pressure was incredibly low, Felix Baumgartner reached a record speed of 1357.64 km/hour, that will be very difficult to overcome.

## The math

In the previous assignment, because there was no air friction, we could assume that the acceleration $$a$$ was constant. This is not the case anymore. The acceleration depends on the forces $$F$$ that work on the base jumper. The force of gravity $$F_{\rm gravity}$$ is constant:

$$F_{\rm gravity} = m \cdot 9.8$$

Where $$m$$ is the mass of the base jumper, which is $$m = 75$$

The force created by the air friction depends on the speed of the base jumper:

$$F_{\rm drag} = \xi v^2$$

Where $$\xi$$ is a constant coefficient. For the base jumper this has the value $$\xi = 0.24$$.

The net force working on the base jumper is the combination of those two forces:

$$F = F_{\rm drag} - F_{\rm gravity}$$

Once you know the net force you can compute the acceleration:

$$a = F/m$$

So now you can extend the algorithm from the previous assignment to include the air friction:

    dt = 0.01
    t = 0, v = 0, x = 1000
    repeat as long x > 200:
        F := ??
        a := F/m
        x := x + v * dt  # update position
        v := v + a * dt  # update speed
        t := t + dt      # update time

## Specification

Create a file `basejump.py` and declare a function `simulate_free_fall(x_start, x_end, m, xi, dt)` in it. The function has 5 paramaters:

- `x_start`: the starting height
- `x_end`: the height at which the simulation stops (the base jumper hopefully opens his parachute there)
- `m`: the mass of the basejumper
- `xi`: the drag constant $$\xi$$, which for this case is $$0.24$$
- `dt`: the time increment for the simulation

The function should return two values:

- A list of heights: the `x` position at every step of the simulation
- A list of times: the time value at every step of the simulation.

Use these lists to plot the height of the base jumper as a function of the time. Plot two lines:

- A green line for a simulation considering air friction ($$\xi = 0.24$$)
- A blue line for a simulation ignoring air friction ($$\xi = 0$$)

## Testing

<!-- checkpy basejump -->
