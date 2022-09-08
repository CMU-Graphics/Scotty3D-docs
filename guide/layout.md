---
layout: default
title: "Layout"
permalink: /guide/layout_mode/
parent: User Guide
nav_order: 0
---

# Layout

This is the main scene editing mode in Scotty3D, and does not contain tasks for the student to implement.
This mode allows you to load full scenes from disk, create or load new objects, export your scene (S3D format), and edit transformations that place each object into your scene.

## Creating Objects

There are three ways to add objects to your scene:
- `Open Scene`: clears the current scene (!) and replaces it with objects loaded from a file on disk.
- `Append Objects`: loads objects from a file, adding them to the current scene.
- `Create Object`: creates a new object or an instance of an object from a choice of various object types.

To save your scene to disk (including all meshes and their transformations) use the `Save Scene` option.

Scotty3D currently only supports loading and exporting scenes of .s3d format.

## Resources and Instances

Scotty3D makes an important distinction between resource objects and instance objects.

Resource objects created are not present immediately inside `Scene Graph`, but rather under the list of all objects in `Resources` tab.
These objects contain basic configuration information that can be used as basic building blocks for creating an instance object in a scene.

An instance object is a combination of references to resource objects that have been put together to create an entity that lives inside a scene.
Since an instance objects consists of various references, these objects can have their references altered while keeping the rest of the properties constant.

## Managing Objects

Left clicking on your instance object under `Scene Graph` will select it.
Various information about that object will appear at the bottom of `Menu`, beneath the `Resources` list.

The `Object` tab contains basic information about the object such as its name, visibility, or rendering style if applicable.

Under `Transform` tab, you may directly edit the values of the object's position, rotation (X->Y->Z Euler angles), and scale. Note that clicking and dragging on the values will smoothly scale them, and Control/Command/Double-clicking on the value will let you edit it as text.

You can also edit the transformation using the `Move`, `Rotate`, and `Scale` tools. One of these options is always active. This determines the transformation widgets that appear at the origin of the object model.
- `Move`: click and drag on the red (X), green (Y), or blue (Z) arrow to move the object along the X/Y/Z axis. Click and drag on the red (YZ), green (XZ), or blue (XY) squares to move the object in the YZ/XZ/XY plane.
- `Rotate`: click and drag on the red (X), green (Y), or blue (Z) loop to rotate the object about the X/Y/Z axis. Note that these rotations are applied relative to the current pose, so they do not necessarily correspond to smooth transformations of the X/Y/Z Euler angles.
- `Scale`: click and drag on the red (X), green (Y), or blue(Z) block to scale the object about the X/Y/Z axis. Again note that this scale is applied relative to the current pose.

You may remove the object from the scene by pressing `Delete` or hitting the Delete key.

Depending on the type of the instance object, other tabs may appear as well, such as `Mesh`, `Shape`, `Material`, `Light`, and so on. These tabs are additional information needed to define the entity for the functionalities used by Scotty3D. Changing the property values of the references inside an instance object will also apply the same changes to the referenced resource object.

If you have selected an object with a `Mesh` tab, you may swap to `Model` mode by pressing `Edit` under `Mesh` tab. Note that if this mesh is non-manifold, this option will not appear.

Also, note that the default `Mesh` is an empty mesh. You must select one of the default mesh types at click `Replace` to substitute the empty mesh with a visible, solid mesh.

## Key Bindings

| Key                   | Command                                            |
| :-------------------: | :--------------------------------------------:     |
| `m` | Use the `Move` tool. |
| `r` | Use the `Rotate` tool. |
| `s` | Use the `Scale` tool. |
| `delete` | Delete the currently selected object. |

## Demo

<video src="{{ site.baseurl }}/guide/layout_mode/layout.mp4" controls preload muted loop style="max-width: 100%; margin: 0 auto;"></video>
