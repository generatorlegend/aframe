# Custom Component Tutorial

## Introduction

A-Frame's component system allows you to extend its functionality by creating custom components. This tutorial will guide you through the process of building custom components, explaining how to define a component, set up its schema, and implement lifecycle methods.

## Defining a Component

To create a custom component, use the `AFRAME.registerComponent()` method. Here's a basic structure:

```javascript
AFRAME.registerComponent('component-name', {
  schema: {
    // Define the component's properties here
  },

  init: function () {
    // Called once when the component is initialized
  },

  update: function () {
    // Called when the component's data changes
  },

  remove: function () {
    // Called when the component is removed
  },

  tick: function (time, timeDelta) {
    // Called on every frame
  }
});
```

## Component Schema

The schema defines the properties of your component. It can be a single property or multiple properties:

```javascript
// Single property schema
schema: {
  type: 'number',
  default: 1
}

// Multiple property schema
schema: {
  color: { type: 'color', default: '#FFF' },
  size: { type: 'number', default: 1 }
}
```

A-Frame supports various property types, including string, number, boolean, array, and more. Each property can have a default value and other attributes like min, max, or parse functions.

## Lifecycle Methods

Components have several lifecycle methods:

- `init()`: Called once when the component is initialized.
- `update(oldData)`: Called when component data changes.
- `remove()`: Called when the component or its entity is removed.
- `tick(time, timeDelta)`: Called on every frame.
- `play()`: Called when the entity is set to play.
- `pause()`: Called when the entity is set to pause.

## Example: Color Changing Component

Let's create a component that changes an entity's color over time:

```javascript
AFRAME.registerComponent('color-cycle', {
  schema: {
    speed: { type: 'number', default: 1 }
  },

  init: function () {
    this.el.setAttribute('material', 'color', '#FF0000');
    this.time = 0;
  },

  tick: function (time, timeDelta) {
    this.time += timeDelta * this.data.speed * 0.001;
    var hue = (Math.sin(this.time) + 1) / 2;
    this.el.setAttribute('material', 'color', `hsl(${hue * 360}, 100%, 50%)`);
  }
});
```

To use this component:

```html
<a-box color-cycle="speed: 2"></a-box>
```

## Interacting with Other Components

Components can interact with other components on the same entity or other entities:

```javascript
AFRAME.registerComponent('scale-on-click', {
  init: function () {
    var el = this.el;
    el.addEventListener('click', function () {
      el.setAttribute('scale', {x: 2, y: 2, z: 2});
    });
  }
});
```

## Integrating External Libraries

You can integrate external libraries into your components. Here's an example using the Three.js library:

```javascript
AFRAME.registerComponent('custom-geometry', {
  init: function () {
    var geometry = new THREE.TorusKnotGeometry(1, 0.3, 100, 16);
    var material = new THREE.MeshStandardMaterial({color: '#FF6B6B'});
    var mesh = new THREE.Mesh(geometry, material);
    this.el.setObject3D('mesh', mesh);
  },

  remove: function () {
    this.el.removeObject3D('mesh');
  }
});
```

## Best Practices

1. Use the schema to define and validate component properties.
2. Implement the `remove()` method to clean up resources and event listeners.
3. Use `this.el` to access the entity the component is attached to.
4. Optimize performance in the `tick()` method, especially for components that run every frame.

## Conclusion

Custom components are a powerful way to extend A-Frame's functionality. By understanding the component lifecycle and schema system, you can create reusable and interactive components for your A-Frame applications.