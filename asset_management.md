---
title: Asset Management in A-Frame
type: guide
layout: docs
parent_section: guides
order: 3
---

# Asset Management in A-Frame

A-Frame provides a robust asset management system to help you efficiently load and manage resources in your VR projects. This guide will walk you through the process of using the asset management system, best practices for loading 3D models and textures, and how to optimize asset loading for better performance.

## Table of Contents

1. [Introduction to Asset Management](#introduction-to-asset-management)
2. [Using the `<a-assets>` Element](#using-the-a-assets-element)
3. [Loading 3D Models](#loading-3d-models)
4. [Managing Textures and Images](#managing-textures-and-images)
5. [Audio and Video Assets](#audio-and-video-assets)
6. [Optimizing Asset Loading](#optimizing-asset-loading)
7. [Best Practices](#best-practices)

## Introduction to Asset Management

A-Frame's asset management system is built around the `<a-assets>` element, which allows you to preload and cache assets before rendering your scene. This approach helps improve performance and ensures that all assets are available when needed.

## Using the `<a-assets>` Element

The `<a-assets>` element should be placed as a child of the `<a-scene>` element. Here's a basic example:

```html
<a-scene>
  <a-assets>
    <!-- Your assets will be defined here -->
  </a-assets>
  
  <!-- Your scene content goes here -->
</a-scene>
```

All assets defined within the `<a-assets>` element will be preloaded before the scene starts rendering. This includes 3D models, textures, audio, and video files.

## Loading 3D Models

To load 3D models, you can use the `<a-asset-item>` element within `<a-assets>`. A-Frame supports various 3D model formats, including glTF, which is recommended for optimal performance.

Here's an example of loading a glTF model:

```html
<a-assets>
  <a-asset-item id="tree-model" src="path/to/tree.gltf"></a-asset-item>
</a-assets>

<a-entity gltf-model="#tree-model"></a-entity>
```

The `gltf-model` component is used to reference and render the loaded model in your scene.

## Managing Textures and Images

For textures and images, use the standard `<img>` element within `<a-assets>`:

```html
<a-assets>
  <img id="grass-texture" src="path/to/grass.jpg">
</a-assets>

<a-plane material="src: #grass-texture"></a-plane>
```

## Audio and Video Assets

Audio and video assets can be preloaded using the `<audio>` and `<video>` elements:

```html
<a-assets>
  <audio id="background-music" src="path/to/music.mp3"></audio>
  <video id="video-texture" src="path/to/video.mp4"></video>
</a-assets>

<a-entity sound="src: #background-music"></a-entity>
<a-plane material="src: #video-texture"></a-plane>
```

## Optimizing Asset Loading

A-Frame's asset management system includes several features to optimize loading:

1. **Preloading**: Assets are automatically preloaded when defined in `<a-assets>`.

2. **Caching**: Loaded assets are cached to improve performance for repeated use.

3. **Timeout**: You can set a timeout attribute on `<a-assets>` to start rendering the scene even if all assets haven't finished loading:

   ```html
   <a-assets timeout="3000">
     <!-- Assets here -->
   </a-assets>
   ```

4. **Events**: The asset management system emits events that you can listen to for more granular control:

   ```javascript
   var scene = document.querySelector('a-scene');

   scene.addEventListener('loaded', function () {
     console.log('All assets have loaded.');
   });

   scene.addEventListener('timeout', function () {
     console.log('Asset loading timed out.');
   });
   ```

## Best Practices

1. **Use glTF for 3D models**: glTF is optimized for web delivery and supported by A-Frame's `gltf-model` component.

2. **Optimize textures**: Use appropriate image formats (e.g., JPG for photos, PNG for graphics with transparency) and compress them when possible.

3. **Lazy loading**: For large scenes, consider lazy loading assets that aren't immediately visible.

4. **Use a CDN**: Hosting your assets on a Content Delivery Network can improve loading times for users across different geographic locations.

5. **Monitor asset size**: Keep an eye on the total size of your assets to ensure quick initial loading times.

6. **Use low-poly models**: When possible, use low-poly models to reduce file size and improve rendering performance.

By following these guidelines and utilizing A-Frame's asset management system, you can create efficient and performant VR experiences with optimized asset loading.