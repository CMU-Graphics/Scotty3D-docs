---
layout: default
title: (Task 3) Flat Triangles
parent: "A1: Rasterizer"
has_toc: false
nav_order: 2
permalink: /rasterizer/flat_triangles
usemathjax: true
---
## Task 3: Flat Triangles

Search for: `//A1T3: clip_triangle` `//A1T3: flat triangles` (in `src/rasterizer/pipeline.cpp`)
Test with: `./Scotty3D --run-tests a1.task3.`
Tests provided: `tests/a1/test.a1.task3.cpp`


[before: wireframe] -> [after: flat shaded]

You will also need to fix `clip_triangle` here, or triangles that go beyond the screen will do strange things.

Fill in the `rasterize_triangle` function for the case where the pipeline is using "flat" (every fragment gets the same attributes) interpolation.

Take care that if two triangles share an edge, and a sample point lies on that edge, exactly one of the triangles should emit a fragment for that sample.
One way to handle this is the ["top-left" rule](https://docs.microsoft.com/en-us/windows/win32/direct3d11/d3d10-graphics-programming-guide-rasterizer-stage-rules) used in Direct3D.

Use scan conversion:
for every horizontal line that covers the triangle:
  determine the minimum and maximum sample within the triangle
  for every sample position in this row:
    emit fragment