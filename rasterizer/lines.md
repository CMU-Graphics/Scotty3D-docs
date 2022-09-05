---
layout: default
title: (Task 2) Lines
parent: "A1: Rasterizer"
has_toc: false
nav_order: 1
permalink: /rasterizer/lines
usemathjax: true
---
## Task 2: Lines

Search for: `//A1T2: rasterize_line` (in `src/rasterizer/pipeline.cpp`)
Test with: `./Scotty3D --run-tests a1.task2.`
Tests provided: `tests/a1/test.a1.task2.cpp`

[before: blank] -> [after: wireframes]

Drawing a scene in *wireframe* (that is: drawing just the edges of triangles) is both a fast preview method and an interesting stylistic choice (e.g., the "Outrun" art style).

As a rasterization warm-up, fill in the `Pipeline::rasterize_line( ... )` function.
This function is used by the pipeline when drawing any mesh whose "wireframe" flag is set.
More details of the function's specification are included in a block comment above the function in the source code.
*Read this specification carefully, as it contains some useful simplifications.*

TODO: diamond exit rule picture?

TODO: maybe should allow any line drawing method here. Could easily rabbit-hole on Bresenham.