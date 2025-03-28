# A-Frame Component Reference

This page provides a comprehensive reference guide for all built-in A-Frame components. Components are grouped by functionality, and for each component, we list its properties, types, default values, and provide usage examples.

## Table of Contents

1. [Geometry Components](#geometry-components)
2. [Material Components](#material-components)
3. [Control Components](#control-components)
4. [Animation and Visual Components](#animation-and-visual-components)
5. [Interaction Components](#interaction-components)
6. [Miscellaneous Components](#miscellaneous-components)

## Geometry Components

### geometry

The `geometry` component defines the shape or model of an entity.

| Property | Type   | Default Value | Description |
|----------|--------|---------------|-------------|
| primitive| string | 'box'         | One of 'box', 'circle', 'cone', 'cylinder', 'plane', 'sphere', 'torus', 'torusKnot' |
| radius   | number | 1             | Radius of the geometry (for circular shapes) |
| width    | number | 1             | Width of the geometry |
| height   | number | 1             | Height of the geometry |
| depth    | number | 1             | Depth of the geometry |

Example usage:

```html
<a-entity geometry="primitive: sphere; radius: 2"></a-entity>
```

## Material Components

### material

The `material` component gives appearance to an entity.

| Property     | Type   | Default Value | Description |
|--------------|--------|---------------|-------------|
| color        | string | '#FFF'        | Base color of the material |
| opacity      | number | 1.0           | Opacity of the material |
| transparent  | boolean| false         | Whether material is transparent |
| shader       | string | 'standard'    | Shading model ('standard', 'flat') |
| side         | string | 'front'       | Which side(s) of faces to render |

Example usage:

```html
<a-entity geometry="primitive: box" material="color: red; opacity: 0.5"></a-entity>
```

## Control Components

### wasd-controls

The `wasd-controls` component allows moving an entity using the WASD or arrow keys.

| Property   | Type   | Default Value | Description |
|------------|--------|---------------|-------------|
| acceleration| number | 65           | How fast the entity accelerates when moving |
| adAxis     | string | 'x'           | Axis that the A and D keys affect |
| adInverted | boolean| false         | Whether to invert the A and D keys |
| enabled    | boolean| true          | Whether the controls are enabled |
| fly        | boolean| false         | Whether to allow vertical movement |
| wsAxis     | string | 'z'           | Axis that the W and S keys affect |
| wsInverted | boolean| false         | Whether to invert the W and S keys |

Example usage:

```html
<a-entity camera look-controls wasd-controls="acceleration: 100; fly: true"></a-entity>
```

## Animation and Visual Components

### animation

The `animation` component animates an entity's components.

| Property   | Type   | Default Value | Description |
|------------|--------|---------------|-------------|
| property   | string | ''            | Property to animate |
| from       | *      | null          | Starting value |
| to         | *      | null          | Ending value |
| dur        | number | 1000          | Duration in milliseconds |
| easing     | string | 'easeInQuad'  | Easing function |
| loop       | boolean/number | false | Whether to loop the animation |

Example usage:

```html
<a-box animation="property: rotation; to: 0 360 0; loop: true; dur: 10000"></a-box>
```

## Interaction Components

### cursor

The `cursor` component provides hover and click states for interaction.

| Property   | Type   | Default Value | Description |
|------------|--------|---------------|-------------|
| fuse       | boolean| false         | Whether to trigger click event on fuse timeout |
| fuseTimeout| number | 1500          | How long to wait (ms) before triggering fuse click event |
| rayOrigin  | string | 'entity'      | Where the ray caster should originate from |

Example usage:

```html
<a-entity camera look-controls>
  <a-entity cursor="fuse: true; fuseTimeout: 500"
            position="0 0 -1"
            geometry="primitive: ring; radiusInner: 0.02; radiusOuter: 0.03"
            material="color: black; shader: flat">
  </a-entity>
</a-entity>
```

## Miscellaneous Components

### light

The `light` component defines a light source.

| Property    | Type   | Default Value | Description |
|-------------|--------|---------------|-------------|
| type        | string | 'directional' | One of 'ambient', 'directional', 'hemisphere', 'point', 'spot' |
| color       | string | '#fff'        | Light color |
| intensity   | number | 1.0           | Light strength |
| castShadow  | boolean| false         | Whether the light casts shadows |

Example usage:

```html
<a-entity light="type: point; intensity: 2; distance: 20; decay: 2"
          position="0 10 0"></a-entity>
```

This reference guide provides an overview of some of the core A-Frame components. For a complete list and more detailed information, please refer to the official A-Frame documentation.