---
layout: default
title: (Task 6) Mip-Mapping
parent: "A1: Rasterizer"
has_toc: false
nav_order: 5
permalink: /rasterizer/mip-mapping
usemathjax: true
---
## Task 6: Mip-Mapping

Search for: `//A1T6: lod` (in `src/rasterizer/programs.h`), `//A1T6: generate` + `//A1T6: sample` (in `src/scene/texture.cpp`)
Test with: `./Scotty3D --run-tests a1.task6`
Tests provided: `tests/a1/test.a1.task6.cpp`

Implement mipmap generation, sampling, and lod determination from derivatives.

[before: aliased grid] -> [after: smooth grid]
