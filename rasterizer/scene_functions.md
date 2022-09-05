---
layout: default
title: (Task 1) Scene Functions
parent: "A1: Rasterizer"
has_toc: false
nav_order: 0
permalink: /rasterizer/scene_functions
usemathjax: true
---
## Task 1: Scene Functions

Where: `//A1T1: local_to_world` and `//A1T1: world_to_local` (in `src/scene/transform.cpp`)
Test with: `./Scotty3D --run-tests a1.task1.`
Tests provided: `tests/a1/test.a1.task-1.cpp`

[before: all objects at origin] -> [after: objects nicely organized]

Your first task is to complete the scene graph implementation in Scotty3D by filling in two functions in the `Transform` class (used to represent object positions).

As discussed in our lecture on 3D transformations, Scotty3D represents the positions of objects in a scene with a scene graph.

Our scene graph (`src/scene/scene.h`) represents the transformations between object space and world space using `Transform` objects (`src/scene/transform.h`) that record the scaling, rotation, and translation (in that order!) that must be applied to move from object-local positions to positions relative to each object's parent.

Indeed, `Transform::local_to_parent` conveniently returns these transformations as a 4x4 matrix (`Mat4`).

Your job is to fill in `Transform::local_to_world` and `Transform::world_to_local` -- functions that produce return `Mat4`'s representing the transformation from object space all the way to / from world space.

Note that `Transform::parent` is a [`std::weak_ptr< Transform >`](https://en.cppreference.com/w/cpp/memory/weak_ptr), so you'll need to call `parent->lock()` to retrieve a [`std::shared_ptr< Transform >`](https://en.cppreference.com/w/cpp/memory/shared_ptr) from which to access the parent's member functions. A good way to do this is to use an [`if` statement containing an `init-statement`](https://en.cppreference.com/w/cpp/language/if).
Thus, your code will probably look something like this:

```cpp
Mat4 Transform::local_to_world() const {
	//A1T1: local_to_world
	//...
	if (std::shared_ptr< Transform > parent_ = parent.lock()) {
		//case where transform has a parent
		//...
	} else {
		//case where transform doesn't have a parent
		//...
	}
	//...
}
```