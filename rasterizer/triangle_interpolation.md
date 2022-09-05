---
layout: default
title: (Task 5) Triangles with Interpolation
parent: "A1: Rasterizer"
has_toc: false
nav_order: 4
permalink: /rasterizer/triangle_interpolation
usemathjax: true
---
## Task 5: Triangles with Interpolation

Search for: `//A1T5: screen-space smooth triangles` and `//A1T5: perspective-correct triangles` (in `src/rasterizer/pipeline.cpp`)
Test with: `./Scotty3D --run-tests a1.task5.`
Tests provided: `tests/a1/test.a1.task5.cpp`


[before: flat shaded] -> [after: smooth shading]

Fill in the `rasterize_triangle` function for the "screen" (screen-space interpolation) and "correct" (perspective-correct interpolation).

Notice that your code will now need to take care to compute derivatives.

[image: perspective correct vs non-perspective correct interpolation]
