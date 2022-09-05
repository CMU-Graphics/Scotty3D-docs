---
layout: default
title: (Task 7) Super-Sampling
parent: "A1: Rasterizer"
has_toc: false
nav_order: 6
permalink: /rasterizer/super-sampling
usemathjax: true
---
## Task 7: Super-Sampling

Where:
- `//A1T7: index` in `src/rasterizer/framebuffer.h`
- `//A1T7: resolve_colors` and `//A1T7: resolve_depths` in `src/rasterizer/rasterizer.cpp`
- ` .... ` in `src/rasterizer/pipeline.cpp`
Test with: `./Scotty3D --run-tests a1.task7.`
Tests provided: `tests/a1/test.a1.task-7.framebuffer.cpp`


[before: aliased edges] -> [after: smooth edges]

(Considers: variable sample positions)

When scenes contain high-frequency detail, point samples don't do a good job of reconstructing them, resulting in "jaggies" or "aliasing" artifacts. One simple way to smooth away these artifacts is to check pixel coverage and color at more than one point within each pixel and to make the final pixel color a weighted average of these points.

In this part of the assignment you will integrate such a "super-sampling" approach into our pipeline, by updating the code to:
- allocate a place to store extra sample information (in `Framebuffer::Framebuffer`)
- generate new fragments for these new samples (in `run_pipeline`)
- combine the samples into an image (in `Framebuffer::resolve()`)

The layout of the samples in the `Framebuffer` are up to you, as is how you choose to generate the samples (e.g., you might choose to modify `draw_triangles` and `fill_line` to be multisample-aware; or you might have `run_pipeline` shift vertex positions to change the effective pixel centers).

Test cases / scenes:
 - carefully constructed scene that spells out the name of each sampling pattern using microgeometry in such a way that only the currently selected sampling pattern renders as white text.

Write-up:
 - What did you pick for how `resolve_depths` should combine sample values?
