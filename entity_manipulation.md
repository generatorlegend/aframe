# Entity Manipulation in A-Frame

This tutorial covers how to manipulate entities in A-Frame, including creating, positioning, and animating them. We'll also explore how to use the entity API to modify properties and components at runtime.

## Creating Entities

To create an entity in A-Frame, you can use the `<a-entity>` element in your HTML:

```html
<a-entity></a-entity>
```

You can also create entities dynamically using JavaScript:

```javascript
var el = document.createElement('a-entity');
document.querySelector('a-scene').appendChild(el);
```

## Positioning Entities

You can position entities using the `position` component:

```html
<a-entity position="1 2 3"></a-entity>
```

Or using JavaScript:

```javascript
el.setAttribute('position', {x: 1, y: 2, z: 3});
```

## Rotating and Scaling Entities

Similar to positioning, you can rotate and scale entities:

```html
<a-entity rotation="0 45 0" scale="2 2 2"></a-entity>
```

Using JavaScript:

```javascript
el.setAttribute('rotation', {x: 0, y: 45, z: 0});
el.setAttribute('scale', {x: 2, y: 2, z: 2});
```

## Adding Components

You can add components to entities to give them appearance, behavior, or functionality:

```html
<a-entity geometry="primitive: box" material="color: red"></a-entity>
```

Using JavaScript:

```javascript
el.setAttribute('geometry', {primitive: 'box'});
el.setAttribute('material', {color: 'red'});
```

## Animating Entities

A-Frame provides an animation component for easy animations:

```html
<a-entity position="0 0 0"
          animation="property: position; to: 0 2 0; dur: 2000; loop: true">
</a-entity>
```

You can also create animations dynamically:

```javascript
el.setAttribute('animation', {
  property: 'position',
  to: '0 2 0',
  dur: 2000,
  loop: true
});
```

## Modifying Properties and Components at Runtime

You can modify an entity's properties and components at runtime using the `setAttribute` method:

```javascript
el.setAttribute('position', {x: 1, y: 2, z: 3});
el.setAttribute('material', 'color', 'blue');
```

To get the current value of a component, use `getAttribute`:

```javascript
var position = el.getAttribute('position');
console.log(position.x, position.y, position.z);
```

## Working with the Object3D

Each entity has an `object3D` property, which is a Three.js Object3D. You can manipulate this directly for more advanced operations:

```javascript
el.object3D.position.set(1, 2, 3);
el.object3D.rotation.set(
  THREE.MathUtils.degToRad(30),
  THREE.MathUtils.degToRad(45),
  0
);
el.object3D.scale.set(2, 2, 2);
```

## Event Handling

Entities can emit and listen for events:

```javascript
el.emit('custom-event', {detail: 'Some data'});

el.addEventListener('custom-event', function (event) {
  console.log(event.detail);
});
```

## Removing Entities

To remove an entity from the scene:

```javascript
el.parentNode.removeChild(el);
```

Or, if you have a reference to the parent:

```javascript
parentEl.removeChild(el);
```

By understanding these concepts, you can effectively manipulate entities in A-Frame to create interactive and dynamic 3D web experiences.