---
title: Getting Started with A-Frame
---

# Getting Started with A-Frame

A-Frame is a web framework for building 3D, AR, and VR experiences using HTML. This guide will help you set up your first A-Frame scene and introduce you to key concepts.

## Setting Up Your First Scene

To create your first A-Frame scene, start with this basic HTML template:

```html
<!DOCTYPE html>
<html>
  <head>
    <script src="https://aframe.io/releases/1.7.0/aframe.min.js"></script>
  </head>
  <body>
    <a-scene>
      <!-- Your 3D content goes here -->
    </a-scene>
  </body>
</html>
```

Save this as `index.html` and open it in a web browser. You'll see a blank scene with a black background.

## Adding Entities

In A-Frame, everything in the scene is an entity. Let's add some basic shapes:

```html
<a-scene>
  <a-box position="-1 0.5 -3" rotation="0 45 0" color="#4CC3D9"></a-box>
  <a-sphere position="0 1.25 -5" radius="1.25" color="#EF2D5E"></a-sphere>
  <a-cylinder position="1 0.75 -3" radius="0.5" height="1.5" color="#FFC65D"></a-cylinder>
  <a-plane position="0 0 -4" rotation="-90 0 0" width="4" height="4" color="#7BC8A4"></a-plane>
  <a-sky color="#ECECEC"></a-sky>
</a-scene>
```

This creates a box, a sphere, a cylinder, a plane (ground), and a sky.

## Understanding Components

A-Frame uses an entity-component system. Entities are general-purpose objects, and components are reusable modules that add appearance, behavior, and functionality to entities.

For example, in `<a-box position="-1 0.5 -3" rotation="0 45 0" color="#4CC3D9"></a-box>`:

- `a-box` is the entity
- `position`, `rotation`, and `color` are components

## Using Basic Components

Here are some common components you can use:

- `position`: Sets the position in 3D space (x, y, z)
- `rotation`: Sets the rotation in degrees (x, y, z)
- `scale`: Sets the scale (x, y, z)
- `color`: Sets the color of the entity

Example:

```html
<a-entity geometry="primitive: box" material="color: red" position="0 1 -3"></a-entity>
```

This creates a red box positioned at (0, 1, -3).

## Adding a Camera and Cursor

To interact with your scene, add a camera and cursor:

```html
<a-entity camera look-controls>
  <a-entity cursor="fuse: true; fuseTimeout: 500"
            position="0 0 -1"
            geometry="primitive: ring; radiusInner: 0.02; radiusOuter: 0.03"
            material="color: black; shader: flat">
  </a-entity>
</a-entity>
```

This adds a camera that you can control by looking around, with a small ring cursor in the center.

## Next Steps

Now that you've created your first A-Frame scene, you can:

1. Experiment with different entities and components
2. Learn about more advanced features like animations and interactions
3. Explore the A-Frame documentation for in-depth information on components and best practices

Remember, A-Frame is built on top of three.js, so as you advance, you'll have access to the full power of WebGL through three.js.

Happy creating!