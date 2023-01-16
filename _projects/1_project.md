---
layout: page
title: terminal_rendering
description: A unicode terminal renderer.
img: assets/img/cube_1.png
importance: 1
category: programming
---


This project is perhaps my favourite dive into an unfamilliar topic. Getting to grips with rudimentary graphics programming has been foundational for my follow up projects. The project started with exploring Andy Sloane's (a1k0n) '[Donut math](https://www.a1k0n.net/2011/07/20/donut-math.html)' article, and has since led me to start learning OpenGL. 
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/sphere_rend.png" title="Sphere" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/torus_rend.png" title="Torus" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/cylinder_rend.png" title="Cylinder" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    New shapes! 
</div>
a1k0n's approach uses the typical features you'd expect when rendering, Z-buffers and transforming 3D->2D using some nifty linear algebra, though employs a unique technique of iterating over the surface of the donut in three dimensions. I've retained this 3D iteration model to produce cubes, spheres, donuts, and a cylinder. 
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/Bresenham_line.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    A Bresenham line with some sub-pixel resolution.
</div>
I'm considering replacing this with an implementation of Bresenham's line algorithm and some form of triangle rasterisation, probably the scanline algorithm, for some nice rendering and a standard implementation of sub-pixel resolution.

``` c++
#include <math.h>
#include <euch_vector.hxx>

#ifndef light_class
#define light_class

class light{

  public:
    euch_vector light_vec;
    light();
    light(float x_dir, float y_dir, float z_dir);

};
```

There's also a few extra funky features, such as light no longer being hard-baked into objects and is an independant universal parallel source, like you're on the moon. Probably the most distinct visual change is the utilisation of the unicode characters. This does cut down on the portability of the program, though the increase in rendering fidelity is more than worth it.
``` c++
while (true){
  dt = t_current - t_prev;
  t_prev += dt;
  t_acc += dt;
  while( t_acc > t_rate ){
    update();
    t_acc -= t_rate;
  }
  draw()
}
```
My next update to this will probably involve moving to a $\Delta t$  model of iteration with the proper accumulator and doing some calculations with respect to a previous or base state. This is really helpful as you can pin the execution of the physics to a specific rate, independent of the rendering process.
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/lorentz_cube.gif" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    A little Lorentz boost and bounce.
</div>
This will probably need some work in terms of the implemented Lorentz transforms in order to get the physics nice and correct. There's also the question of what to do next with this. I wonder about it's applications to my day to day work, and repeatedly land on if anyone needs to render ATLAS events quickly on the terminal?
