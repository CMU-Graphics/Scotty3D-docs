---
layout: default
title: "A1: Rasterizer"
permalink: /rasterizer/
nav_order: 5
has_children: true
has_toc: false
---

# Rasterizer Overview

Modern GPUs implement an abstraction called the Rasterization Pipeline.
This abstraction breaks the process of converting 3D triangles into 2D pixels into several highly-parallel stages, allowing for a variety of efficient hardware implementations.
In this assignment, you will be implementing parts of a simplified rasterization pipeline *in software*.
Though simplified, your pipeline will be sufficient to allow Scotty3D to create preview renders without a GPU!

[rasterization pipeline image goes here: world vertices -> (vertex program) -> ndc vertices -> (primitive assembly) -> ndc triangles -> (clipping) -> ndc triangles -> (viewport) -> viewport triangles -> (rasterization) -> fragment attributes -> (fragment program) -> shaded fragments -> (z test, blending) <-> framebuffer]

Different graphics APIs may present this pipeline in different ways, but the core steps remains consistent: a GPU draws things by running code (in parallel) on a list of vertices to produce homogeneous screen positions (+ extra varying data), building triangles from that list of vertices, clipping the triangles to remove parts not visible on the screen, performing a division to compute screen positions, computing a list of "fragments" covered by those triangles, running code on each fragment, and composing the results into a framebuffer.

The following sections contain guidelines for implementing the functionality of Rasterizer:

**A1.0**

- [(Task 1) Scene Functions](scene_functions)
- [(Task 2) Lines](lines)
- [(Task 3) Flat Triangles](flat_triangles)
- [(Task 4) Depth Testing and Blending](depth_and_blend)

**A1.5**

- [(Task 5) Triangles with Interpolation](triangle_interpolation)
- [(Task 6) Mip-Mapping](mip-mapping)
- [(Task 7) Super-Sampling](super-sampling)
- [Extra Credits](extra_credits)


## Manual Testing

In this assignment, you will be working with software rasterization code. You have two ways of running this code.

You can run the code interactively from the GUI:
- Load a scene.
- Click the "Render" tab at the top of the screen.
- Click the "Open Render Window" button in the left pane.
- Select "Software Rasterize" from the "Method" drop-down in the "Render Image" window.
- Select a "Camera Instance" in the "Render Image" window.
- Click the "Start Render" button in the "Render Image" window.

You can also run the code from the CLI:
```
./Scotty3D --scene media/A1-basic.s3d --camera "Camera Instance" --rasterize --output A1-basic.png
```

## Automated Testing

For all of the tasks below we provide a basic set of functionality tests in the corresponding `tests/a1/test.a1.*.cpp` file(s). You can run these tests with `./Scotty3D --run-tests a1.`.

**Be Warned**, however, that we provide *only* basic functionality tests; when we grade your assignment, we will also (a) read your code and (b) use an expanded set of test cases.

You may add test cases by creating new `.cpp` files in the `tests/a1/` folder. We encourage you to develop and share test cases on Piazza. (Reminder: Test cases are the *only* source code you should *ever* post on our class Piazza.)

Writing automated test cases can help you isolate and test individual functions in your code.

