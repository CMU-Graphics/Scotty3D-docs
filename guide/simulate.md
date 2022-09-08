---
layout: default
title: "Simulate"
permalink: /guide/simulate_mode/
parent: User Guide
nav_order: 5
---

# Simulate

The simulation view provides a way to create and manage particle emitters. 

To add an emitter, simply create a new `Particles Instance` and adjust the parameters below.

![add emitter](add_emitter.png)

- `Gravity`: the gravitational force acting on particles that get emitted from this emitter.
- `Scale`: the scale factor to apply to the particle mesh when rendering particles.
- `Initial Velocity`: how fast each particle exits the emitter.
- `Spread Angle`: angle of cone within which particles are generated (pointing in the emitter object's direction).
- `Lifetime`: how long (in seconds) each particle should live before it is deleted.
- `Particles/Sec`: how many particles should be generated per second. The total amount of live particles is hence `lifetime * particles_per_second`.
- `Timestep`: the time interval between updating the position of particles on display. 

In order to enable the emitter, you need to toggled `Simulate Here` checkbox under `Object` tab that appears when you select your emitter.

Also note that the default `Mesh` attached to a new emitter instance is actually an empty mesh! You need to assign it a new mesh by selecting a mesh that has been already configured elsewhere or replacing it with a default mesh type.

Once an enabled emitter is added to the scene (and animation task 4: particle simulation is implemented), particles will start generating and following trajectories based on the emitter parameters. Particles should collide with scene objects. When moving existing objects that particles interact with, the simulation will not be updated until the movement is completed. 

For example, the `particles.s3d` test scene:

<video src="{{ site.baseurl }}/guide/simulate_mode/guide-simulate-1.mp4" controls preload muted loop style="max-width: 100%; margin: 0 auto;"></video>

Finally, note that you can render particles just like any other scene objects. Rendering `particles.s3d` with depth of field:

![particles render](render.png)
