# Component Reference

This page serves as a comprehensive reference guide for all built-in A-Frame components. Each component is described with its properties, events, and usage examples.

## Table of Contents

1. [animation](#animation)
2. [camera](#camera)
3. [cursor](#cursor)
4. [geometry](#geometry)
5. [gltf-model](#gltf-model)
6. [light](#light)
7. [line](#line)
8. [link](#link)
9. [look-controls](#look-controls)
10. [material](#material)
11. [position](#position)
12. [raycaster](#raycaster)
13. [rotation](#rotation)
14. [scale](#scale)
15. [shadow](#shadow)
16. [sound](#sound)
17. [text](#text)
18. [visible](#visible)
19. [wasd-controls](#wasd-controls)

## animation

The animation component allows you to animate entity properties over time.

### Properties

- `property`: The property to animate.
- `from`: The starting value of the animation.
- `to`: The destination value of the animation.
- `dur`: Duration of the animation in milliseconds.
- `easing`: Easing function of the animation.

### Usage

```html
<a-box animation="property: rotation; to: 0 360 0; dur: 2000; easing: linear; loop: true"></a-box>
```

## camera

The camera component defines from which perspective the user views the scene.

### Properties

- `active`: Whether this camera is the active camera in a scene with multiple cameras.
- `far`: Camera frustum far clipping plane.
- `fov`: Field of view (in degrees).
- `near`: Camera frustum near clipping plane.

### Usage

```html
<a-entity camera="active: true; far: 1000; fov: 80; near: 0.1"></a-entity>
```

## cursor

The cursor component provides hover and click states for interaction on top of the raycaster component.

### Properties

- `fuse`: Whether cursor is fuse-based.
- `fuseTimeout`: How long to wait (in milliseconds) before triggering a fuse-based click event.

### Events

- `click`: Triggered when the cursor clicks an entity.
- `mouseenter`: Triggered when the cursor intersects with an entity.
- `mouseleave`: Triggered when the cursor no longer intersects with an entity.

### Usage

```html
<a-entity cursor="fuse: true; fuseTimeout: 500"
          position="0 0 -1"
          geometry="primitive: ring; radiusInner: 0.02; radiusOuter: 0.03"
          material="color: black; shader: flat">
</a-entity>
```

## geometry

The geometry component provides a basic shape for an entity.

### Properties

- `primitive`: Type of geometry (e.g., box, sphere, cylinder).
- `height`, `width`, `depth`: Dimensions of the geometry.
- `radius`: Radius of curved geometries.

### Usage

```html
<a-entity geometry="primitive: box; width: 1; height: 1; depth: 1"></a-entity>
```

## gltf-model

The gltf-model component loads a 3D model using the glTF (GL Transmission Format) specification.

### Properties

- `src`: URL to a glTF (.gltf or .glb) file, or selector to an asset.

### Usage

```html
<a-entity gltf-model="url(model.gltf)"></a-entity>
```

## light

The light component defines the entity as a source of light.

### Properties

- `type`: Type of light (ambient, directional, hemisphere, point, spot).
- `color`: Light color.
- `intensity`: Light strength.

### Usage

```html
<a-entity light="type: point; intensity: 2; distance: 20; color: yellow"></a-entity>
```

## line

The line component draws a line in 3D space.

### Properties

- `start`: Starting point of the line.
- `end`: End point of the line.
- `color`: Color of the line.

### Usage

```html
<a-entity line="start: 0 1 0; end: 2 0 -1; color: red"></a-entity>
```

## link

The link component provides a visual representation for linking to other pages or sites.

### Properties

- `href`: The URL to open on click.
- `title`: Text displayed on the link.

### Usage

```html
<a-entity link="href: https://aframe.io; title: A-Frame"></a-entity>
```

## look-controls

The look-controls component allows the user to look around the scene by dragging the mouse or moving a mobile device.

### Properties

- `enabled`: Whether look controls are enabled.
- `reverseMouseDrag`: Whether to reverse mouse drag.

### Usage

```html
<a-entity camera look-controls></a-entity>
```

## material

The material component gives appearance to an entity.

### Properties

- `color`: Base diffuse color.
- `shader`: Shader used to render the material.
- `opacity`: Extent of transparency.
- `side`: Which sides of the mesh to render.

### Usage

```html
<a-entity geometry="primitive: box" material="color: red; opacity: 0.5"></a-entity>
```

## position

The position component places an entity in a certain spot in 3D space.

### Properties

- `x`, `y`, `z`: Coordinates in 3D space.

### Usage

```html
<a-entity position="0 1 -3"></a-entity>
```

## raycaster

The raycaster component provides line-based intersection testing with a specified set of objects.

### Properties

- `far`: Maximum distance to check for intersections.
- `objects`: Query selector to test for intersections with.

### Usage

```html
<a-entity raycaster="objects: .clickable; far: 20"></a-entity>
```

## rotation

The rotation component defines the orientation of an entity in degrees.

### Properties

- `x`, `y`, `z`: Rotation around each axis in degrees.

### Usage

```html
<a-entity rotation="45 90 180"></a-entity>
```

## scale

The scale component defines the size of an entity in terms of its width, height, and depth.

### Properties

- `x`, `y`, `z`: Scale factor for each dimension.

### Usage

```html
<a-entity scale="2 0.5 1"></a-entity>
```

## shadow

The shadow component enables shadows for an entity and its children.

### Properties

- `cast`: Whether the entity casts shadows.
- `receive`: Whether the entity receives shadows.

### Usage

```html
<a-entity shadow="cast: true; receive: false"></a-entity>
```

## sound

The sound component defines the entity as a source of sound or audio.

### Properties

- `src`: URL to the sound file.
- `volume`: How loud to play the sound.
- `autoplay`: Whether to play the sound automatically.
- `loop`: Whether to loop the sound.

### Usage

```html
<a-entity sound="src: url(sound.mp3); autoplay: true; loop: true; volume: 0.5"></a-entity>
```

## text

The text component renders text as a texture on a plane.

### Properties

- `value`: The actual content of the text.
- `align`: Text alignment (left, center, right).
- `color`: Text color.
- `font`: Font to render the text with.

### Usage

```html
<a-entity text="value: Hello, A-Frame!; color: #BBB; align: center;"></a-entity>
```

## visible

The visible component determines whether an entity is visible.

### Properties

- `visible`: Whether the entity is visible (true or false).

### Usage

```html
<a-entity visible="false"></a-entity>
```

## wasd-controls

The wasd-controls component allows you to move around the scene using the WASD or arrow keys.

### Properties

- `acceleration`: How fast the entity accelerates when moving.
- `adAxis`: Axis that the A and D keys affect (can be "x" or "z").
- `wsAxis`: Axis that the W and S keys affect (can be "x" or "z").

### Usage

```html
<a-entity camera wasd-controls="acceleration: 100"></a-entity>
```

This reference guide covers the main built-in components in A-Frame. For more detailed information on each component and additional components, please refer to the official A-Frame documentation.