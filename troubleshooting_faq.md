# Troubleshooting FAQ

This document provides solutions to common issues and answers to frequently asked questions when working with A-Frame.

## Table of Contents

1. [General Issues](#general-issues)
2. [Performance](#performance)
3. [WebXR and VR Mode](#webxr-and-vr-mode)
4. [Asset Management](#asset-management)
5. [Components and Entities](#components-and-entities)
6. [Rendering and Visual Issues](#rendering-and-visual-issues)

## General Issues

### Q: My scene is not loading or displaying correctly. What should I check?

A: If your scene is not loading or displaying as expected, try the following:

1. Check the browser console for any error messages.
2. Ensure all required scripts are properly included, especially the A-Frame library.
3. Verify that your HTML structure is correct, with all entities properly nested within the `<a-scene>` element.
4. Make sure all assets are loading correctly and file paths are accurate.

### Q: How can I debug my A-Frame application?

A: A-Frame provides several tools for debugging:

1. Use the built-in Inspector by pressing `<ctrl> + <alt> + i` in your scene.
2. Enable debug mode by adding the `debug` attribute to your `<a-scene>` element.
3. Use the browser's developer tools to inspect the DOM and monitor the console for warnings or errors.
4. Utilize A-Frame's debug logs by enabling them in the console:

```javascript
debug.enable('*');
```

## Performance

### Q: My scene is running slowly. How can I improve performance?

A: To optimize your A-Frame scene:

1. Reduce polygon count in 3D models.
2. Use texture atlases to combine multiple textures.
3. Implement level-of-detail (LOD) for complex objects.
4. Use the `stats` component to monitor performance metrics:

```html
<a-scene stats>
  <!-- Your scene content -->
</a-scene>
```

5. Consider using the `pool` component for object pooling with frequently created/destroyed entities.

### Q: How can I make my A-Frame application mobile-friendly?

A: To optimize for mobile:

1. Use lower-resolution textures and simpler 3D models.
2. Reduce the number of lights and shadows in the scene.
3. Implement dynamic quality adjustments based on device capabilities.
4. Use the `device-orientation-permission-ui` component for handling orientation on mobile devices.

## WebXR and VR Mode

### Q: VR mode is not working. What could be the issue?

A: If VR mode is not functioning:

1. Ensure you're using a WebXR-compatible browser.
2. Check if your VR headset is properly connected and recognized by the system.
3. Verify that you're serving your content over HTTPS, which is required for WebXR.
4. Make sure you're calling `enterVR()` in response to a user gesture (e.g., button click).

Example of proper VR mode entry:

```javascript
document.querySelector('#enter-vr-button').addEventListener('click', function () {
  var scene = document.querySelector('a-scene');
  scene.enterVR();
});
```

### Q: How can I detect if WebXR is available?

A: You can check for WebXR support using the `utils.device` module:

```javascript
if (AFRAME.utils.device.checkHeadsetConnected()) {
  console.log('VR headset is connected');
}

if (AFRAME.utils.device.isWebXRAvailable) {
  console.log('WebXR is available');
}
```

## Asset Management

### Q: My assets are not loading. What should I check?

A: If assets fail to load:

1. Verify file paths and ensure they are correct relative to your HTML file.
2. Check for CORS issues if loading assets from a different domain.
3. Use the asset management system to preload assets:

```html
<a-scene>
  <a-assets>
    <img id="texture" src="texture.jpg">
    <a-asset-item id="model" src="model.gltf"></a-asset-item>
  </a-assets>
  
  <a-entity geometry="primitive: box" material="src: #texture"></a-entity>
  <a-entity gltf-model="#model"></a-entity>
</a-scene>
```

4. Listen for the `loaded` event on `<a-assets>` to ensure all assets are ready before using them.

## Components and Entities

### Q: How do I update a component's properties at runtime?

A: You can update component properties using the `setAttribute` method:

```javascript
var entity = document.querySelector('#myEntity');
entity.setAttribute('position', {x: 1, y: 2, z: 3});
entity.setAttribute('material', 'color', 'red');
```

### Q: I've added a custom component, but it's not working. What could be wrong?

A: If your custom component is not functioning:

1. Ensure the component is registered before the scene loads.
2. Check for any JavaScript errors in the console.
3. Verify that the component name in HTML matches the registered name.
4. Make sure the component's dependencies are properly handled in the `dependencies` array.

Example of proper component registration:

```javascript
AFRAME.registerComponent('my-component', {
  init: function () {
    console.log('My component initialized');
  }
});
```

## Rendering and Visual Issues

### Q: Objects in my scene are not visible. What could cause this?

A: If objects are not visible:

1. Check if the camera is positioned correctly relative to the objects.
2. Ensure lights are present in the scene if using materials that require lighting.
3. Verify that object scales are appropriate (not too small or too large).
4. Check if objects are obscured by other entities or if their material is set to be transparent.

### Q: How can I change the background of my scene?

A: You can change the scene background using the `background` component on the `<a-scene>` element:

```html
<a-scene background="color: #skyblue"></a-scene>
```

For a 360° background image:

```html
<a-scene>
  <a-sky src="sky.jpg"></a-sky>
</a-scene>
```

Remember that troubleshooting in A-Frame often involves a combination of checking the HTML structure, JavaScript code, and understanding how components and systems interact. Always refer to the official A-Frame documentation for the most up-to-date information on APIs and best practices.