# Scene Configuration in A-Frame

A-Frame scenes are the foundation of your virtual reality experiences. This guide will walk you through configuring A-Frame scenes, including setting up the renderer, camera, and lighting. We'll also explore how to customize your scene for different use cases and platforms.

## Basic Scene Setup

To create a basic A-Frame scene, you need to use the `<a-scene>` element in your HTML:

```html
<a-scene>
  <!-- Your A-Frame content goes here -->
</a-scene>
```

This creates a default scene with a camera, lights, and a renderer.

## Configuring the Renderer

A-Frame uses Three.js as its underlying rendering engine. You can customize the renderer by adding attributes to the `<a-scene>` element:

```html
<a-scene renderer="antialias: true; logarithmicDepthBuffer: true;">
  <!-- Scene content -->
</a-scene>
```

Common renderer options include:

- `antialias`: Enables antialiasing for smoother edges (default: `true` on desktop, `false` on mobile)
- `logarithmicDepthBuffer`: Improves rendering of scenes with large depth ranges (default: `false`)
- `precision`: Sets the precision of shader calculations (`highp`, `mediump`, or `lowp`)

## Setting Up the Camera

A-Frame automatically creates a default camera, but you can customize it or add multiple cameras:

```html
<a-scene>
  <a-camera position="0 1.6 0" fov="80" near="0.1" far="1000"></a-camera>
  <!-- Other scene content -->
</a-scene>
```

Camera properties include:

- `position`: Sets the camera's initial position
- `fov`: Field of view in degrees (default: 80)
- `near`: Near clipping plane (default: 0.005)
- `far`: Far clipping plane (default: 10000)
- `active`: Set to `true` for the primary camera (default: `true`)

## Configuring Lighting

Lighting is crucial for creating realistic scenes. A-Frame provides several light types:

```html
<a-scene>
  <a-light type="ambient" color="#BBB"></a-light>
  <a-light type="directional" position="0 1 1" intensity="0.5"></a-light>
  <a-light type="point" position="2 4 4"></a-light>
  <!-- Scene content -->
</a-scene>
```

Common light types and properties:

- `ambient`: Uniform light that affects all objects equally
- `directional`: Light that shines from a specific direction
- `point`: Light that emanates from a single point in all directions
- `spot`: Cone-shaped light source
- `color`: Light color
- `intensity`: Light strength (default: 1.0)
- `castShadow`: Enable shadow casting (for directional, point, and spot lights)

## Customizing for Different Platforms

A-Frame automatically adapts to different platforms, but you can optimize your scene for specific use cases:

### Mobile Optimization

```html
<a-scene renderer="antialias: false; precision: medium;">
  <!-- Use lower-poly models and fewer lights for better performance -->
</a-scene>
```

### VR Mode

A-Frame handles VR mode automatically, but you can customize the behavior:

```html
<a-scene vr-mode-ui="enabled: true">
  <!-- Scene content -->
</a-scene>
```

### AR Mode

For augmented reality experiences, you can use the `ar-mode` component:

```html
<a-scene ar-mode>
  <!-- AR content -->
</a-scene>
```

## Advanced Scene Configuration

For more complex scene setups, you can use JavaScript to configure your scene programmatically:

```javascript
AFRAME.registerComponent('custom-scene-config', {
  init: function () {
    var sceneEl = this.el;
    var renderer = sceneEl.renderer;
    
    // Customize renderer
    renderer.setPixelRatio(window.devicePixelRatio);
    
    // Adjust scene properties
    sceneEl.setAttribute('stats', 'true'); // Enable performance stats
    sceneEl.systems.renderer.setColorManagement(true);
    
    // Set up post-processing
    // ... (add post-processing setup code here)
  }
});
```

Then, add this component to your scene:

```html
<a-scene custom-scene-config>
  <!-- Scene content -->
</a-scene>
```

## Best Practices

1. Start with a simple scene and add complexity as needed.
2. Use the appropriate light types and settings for your scene.
3. Optimize for performance, especially on mobile devices.
4. Test your scene on multiple devices and platforms.
5. Use the A-Frame Inspector (press `<ctrl> + <alt> + i`) to fine-tune your scene configuration.

By following these guidelines and exploring the various configuration options, you can create immersive and performant A-Frame scenes tailored to your specific requirements and target platforms.