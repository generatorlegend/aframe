---
title: Animation Guide
type: guides
layout: docs
parent_section: guides
order: 10
---

# Animation Guide

A-Frame provides a powerful animation system that allows you to bring your scenes to life. This guide will cover both the built-in animation component and how to use external animation libraries with A-Frame.

## Table of Contents

1. [Built-in Animation System](#built-in-animation-system)
   - [Basic Usage](#basic-usage)
   - [Animation Properties](#animation-properties)
   - [Multiple Animations](#multiple-animations)
2. [Animating Different Properties](#animating-different-properties)
   - [Position](#position)
   - [Rotation](#rotation)
   - [Scale](#scale)
   - [Component Properties](#component-properties)
3. [Advanced Animation Techniques](#advanced-animation-techniques)
   - [Chaining Animations](#chaining-animations)
   - [Using Events](#using-events)
4. [Using External Animation Libraries](#using-external-animation-libraries)

## Built-in Animation System

A-Frame's built-in animation system is based on the `animation` component, which uses the [anime.js](https://animejs.com/) library under the hood.

### Basic Usage

To animate an entity, add the `animation` component to it and specify the properties you want to animate:

```html
<a-box position="0 1.5 -5" rotation="0 45 0" color="#4CC3D9"
       animation="property: rotation; to: 0 360 0; loop: true; dur: 10000">
</a-box>
```

This will create a rotating box that completes a full rotation every 10 seconds.

### Animation Properties

The `animation` component accepts several properties to control the animation:

- `property`: The property to animate (e.g., position, rotation, scale)
- `from`: The starting value (optional, defaults to the current value)
- `to`: The ending value
- `dur`: Duration of the animation in milliseconds
- `delay`: Delay before the animation starts in milliseconds
- `dir`: Direction of the animation (normal, reverse, alternate)
- `easing`: Easing function for the animation
- `loop`: Number of times to repeat the animation (true for infinite)
- `startEvents`: Events to start the animation
- `pauseEvents`: Events to pause the animation
- `resumeEvents`: Events to resume the animation

### Multiple Animations

You can add multiple animations to a single entity by using the multiple component syntax:

```html
<a-entity
  animation__rotate="property: rotation; to: 0 360 0; loop: true; dur: 10000"
  animation__scale="property: scale; to: 1.5 1.5 1.5; loop: true; dir: alternate; dur: 5000">
</a-entity>
```

## Animating Different Properties

### Position

To animate an entity's position:

```html
<a-entity position="0 0 -5"
          animation="property: position; to: 0 2 -5; dur: 2000; easing: easeInOutQuad">
</a-entity>
```

### Rotation

To animate an entity's rotation:

```html
<a-entity rotation="0 0 0"
          animation="property: rotation; to: 0 360 0; loop: true; dur: 10000">
</a-entity>
```

### Scale

To animate an entity's scale:

```html
<a-entity scale="1 1 1"
          animation="property: scale; to: 2 2 2; dur: 2000; easing: easeInOutElastic">
</a-entity>
```

### Component Properties

You can also animate properties of other components:

```html
<a-entity material="opacity: 1"
          animation="property: material.opacity; to: 0; dur: 2000">
</a-entity>
```

## Advanced Animation Techniques

### Chaining Animations

You can chain animations using the `startEvents` property:

```html
<a-entity
  animation__1="property: position; to: 0 2 0; dur: 2000"
  animation__2="property: scale; to: 2 2 2; dur: 2000; startEvents: animationcomplete__1">
</a-entity>
```

### Using Events

You can start, pause, and resume animations using events:

```html
<a-entity
  animation="property: rotation; to: 0 360 0; startEvents: go; pauseEvents: stop; resumeEvents: continue">
</a-entity>

<a-entity id="controller">
  <a-button onclick="document.querySelector('a-entity').emit('go')">Start</a-button>
  <a-button onclick="document.querySelector('a-entity').emit('stop')">Pause</a-button>
  <a-button onclick="document.querySelector('a-entity').emit('continue')">Resume</a-button>
</a-entity>
```

## Using External Animation Libraries

While A-Frame's built-in animation system is powerful, you may want to use external animation libraries for more complex animations or to leverage existing skills. Here's an example using GreenSock (GSAP):

First, include the GSAP library in your HTML:

```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.9.1/gsap.min.js"></script>
```

Then, you can use GSAP in your A-Frame scene:

```html
<a-scene>
  <a-box id="animated-box" position="0 1.5 -5" rotation="0 45 0" color="#4CC3D9"></a-box>
</a-scene>

<script>
  // Wait for the scene to load
  document.querySelector('a-scene').addEventListener('loaded', function () {
    var box = document.querySelector('#animated-box').object3D;
    
    gsap.to(box.position, {
      y: 3,
      duration: 2,
      yoyo: true,
      repeat: -1,
      ease: "power1.inOut"
    });
    
    gsap.to(box.rotation, {
      y: Math.PI * 2,
      duration: 5,
      repeat: -1,
      ease: "none"
    });
  });
</script>
```

This example creates a box that bounces up and down while rotating continuously.

By mastering both the built-in animation system and external libraries, you can create rich, interactive experiences in your A-Frame projects.