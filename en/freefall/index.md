# Assignment: the ultimate free fall

The apple from the previous assignment reached the surface after a little over 4 seconds. Imagine that exactly at the location where the apple was dropped, a tunnel was dug straight through the planet. The problem with a free fall through the earth is that the gravitational pull of earth can not be considered constant anymore. At the surface of the earth you feel much more gravity than near the center.

The following video explains the basic math behind this situation:

![embed](https://www.youtube.com/embed/urQCmMiHKQk)

In summery, if we consider the density of the earth to be uniform, the equation that governs the gravitational force in the free fall is (see 2:00 in the video):

$$F_{\rm gravity} = -G\cdot \sigma \cdot \frac{4}{3} \cdot \pi \cdot m \cdot r$$

Where

- $$G$$ is the gravitational constant with the value of $$G = 6.67408e-11 m^3 / kg / s^2$$
- $$\sigma$$ is the density of the earth, which is $$\sigma = 5520 g/m^3$$
- $$m$$ is the mass of the object that's falling in kilograms
- $$r$$ is the distance of the object to the center of the earth in meters

Or, as they elegantly put it in the video, $$F_{\rm gravity}$$ is just some constant stuff times $$r$$. The only thing that changes over time is $$r$$.

If we only consider the force of gravity (and no air drag or any other force), we can write the acceleration of the object:

$$
a = \frac{F}{m} = \frac{F_{\rm gravity}}{m} = \frac{-G\cdot \sigma \cdot \frac{4}{3} \cdot \pi \cdot m \cdot r}{m} \\
= -G\cdot \sigma \cdot \frac{4}{3} \cdot \pi \cdot r
$$

In other words, we loose the $$m$$. We don't need to know the mass of the object. Peter, from the video, jumping through the hole and our apple will accelerate at the exact same rate.

Using this equation for the acceleration, we can simulate the fall through the earth.

## Specification
Create a file `tunnel.py` and declare a function `simulate_ultimate_free_fall(r_start, dt)` in it. The function has 2 paramaters:

- `r_start`: the distance of the apple to the center of the earth. If the apple starts at the surface of the earth, this is `6.38e6` meters.
- `dt`: the time increment for the simulation

The function should run the simulation until the apple has completed a full cycle and is back to it's highest point. (How are you going to detect this? You have to be a bit clever here.)

The function should return three lists:

- A list of distances: the value $$r$$ at every step of the simulation.
- A list of speeds: the speed of the apple at every step of the simulation.
- A list of times: the time value at every step of the simulation.

Using those lists, create a plot. Plot two lines:

- A green line for the distances (using the left y-axis)
- A blue line for the speeds (using the right y-axis)

## Tip

How do you know when the simulation should stop? It might be tricky to detect when the simulation has completed a full cycle, but don't hardcode this. It will not work to test if the distance $$r$$ is exactly the same as the starting distance, because of small rounding errors.

But, you can at first just let the simulation run for a long time (let's say 10000 seconds) and plot the results. Observe how the speed and distance change when you complete a cycle and use this information to determine a better stopping condition for the simulation.

## Testing

    checkpy tunnel
