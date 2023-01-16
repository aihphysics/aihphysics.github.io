---
layout: page
title: terminal_rendering
description: A unicode terminal renderer.
img: assets/img/cube_1.png
importance: 1
category: programming
---


This project is perhaps my favourite dive into an unfamilliar topic. Getting to grips with rudimentary graphics programming has been foundational for my follow up projects. The project started with exploring Andy Sloane's (a1k0n) '[Donut math](https://www.a1k0n.net/2011/07/20/donut-math.html)' article, and has since led me to start learning OpenGL. 

a1k0n's approach uses the typical features you'd expect when rendering, Z-buffers and transforming 3D->2D using some nifty linear algebra, though employs a unique technique of iterating over the surface of the donut in three dimensions. I've retained this 3D iteration model to produce cubes, spheres, donuts, and a cylinder. 

I'm considering replacing this with an implementation of Bresenham's line algorithm and some form of triangle rasterisation. 

There's also a few extra funky features, such as light no longer being hard-baked into objects and is an independant universal parallel source, like you're on the moon. Probably the most distinct visual change is the utilisation of the unicode characters. I'll admit that this does cut down on the portability of the 

My next update to this will probably involve moving to a $ \Delta t $ model of iteration with the proper accumulator and doing some calculations with respect to a previous or base state. This is really helpful as you can pin the execution of the physics to a specific rate, independent of the rendering process.

This will probably need some work in terms of the implemented Lorentz transforms in order to get the physics nice and correct.
