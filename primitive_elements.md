---
title: Primitive Elements in A-Frame
type: primitives
layout: docs
parent_section: introduction
order: 5
---

# Primitive Elements in A-Frame

## Introduction

A-Frame provides a set of primitive elements that simplify the process of creating 3D scenes. These primitives are pre-configured entities with default components and properties, allowing developers to quickly build scenes without having to manually set up complex entity-component structures.

## Purpose of Primitives

Primitives serve several purposes in A-Frame:

1. **Convenience**: They offer a shorthand for creating common 3D objects.
2. **Abstraction**: They hide the complexity of the underlying entity-component system.
3. **Accessibility**: They make it easier for beginners to start building 3D scenes.

## Using Primitives

To use a primitive, simply add it to your A-Frame scene using HTML-like syntax:

```html
<a-scene>
  <a-box position="-1 0.5 -3" rotation="0 45 0" color="#4CC3D9"></a-box>
  <a-sphere position="0 1.25 -5" radius="1.25" color="#EF2D5E"></a-sphere>
  <a-cylinder position="1 0.75 -3" radius="0.5" height="1.5" color="#FFC65D"></a-cylinder>
  <a-plane position="0 0 -4" rotation="-90 0 0" width="4" height="4" color="#7BC8A4"></a-plane>
  <a-sky color="#ECECEC"></a-sky>
</a-scene>
```

## Available Primitives

A-Frame provides several built-in primitives. Here's a list of some commonly used ones and their corresponding components:

| Primitive | Main Components | Description |
|-----------|-----------------|-------------|
| `<a-box>` | geometry, material | A cube or cuboid |
| `<a-sphere>` | geometry, material | A sphere |
| `<a-cylinder>` | geometry, material | A cylinder |
| `<a-plane>` | geometry, material | A flat plane |
| `<a-sky>` | geometry, material | A 360-degree background |
| `<a-image>` | material | A flat image |
| `<a-video>` | material | A flat video |
| `<a-videosphere>` | geometry, material | A 360-degree video background |
| `<a-light>` | light | A light source |
| `<a-camera>` | camera | A camera view |
| `<a-cursor>` | cursor | A cursor for interaction |
| `<a-link>` | link | A link to navigate between scenes |
| `<a-text>` | text | 3D text |
| `<a-gltf-model>` | gltf-model | 3D model loader for glTF format |
| `<a-obj-model>` | obj-model | 3D model loader for OBJ format |

## Customizing Primitives

While primitives come with default components and properties, you can easily customize them by adding or overriding attributes:

```html
<a-box position="0 2 -5" rotation="0 45 45" scale="2 2 2" color="red"></a-box>
```

## Creating Custom Primitives

A-Frame allows you to create custom primitives for your specific needs. This is done using the `registerPrimitive` function:

```javascript
AFRAME.registerPrimitive('a-custom-box', {
  defaultComponents: {
    geometry: {primitive: 'box'},
    material: {color: 'red'}
  },
  mappings: {
    depth: 'geometry.depth',
    height: 'geometry.height',
    width: 'geometry.width'
  }
});
```

You can then use your custom primitive in your A-Frame scene:

```html
<a-custom-box depth="2" height="2" width="2"></a-custom-box>
```

## Conclusion

Primitives in A-Frame provide an easy way to create 3D scenes quickly. They abstract away the complexity of the entity-component system, making it accessible for beginners while still allowing for customization and extension by more advanced users.

For more detailed information on each primitive and its properties, refer to the individual primitive documentation pages.