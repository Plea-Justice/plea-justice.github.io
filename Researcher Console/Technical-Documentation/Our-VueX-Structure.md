---
layout: page
title: Our VueX Structure
permalink: /console/docs/our-vuex-structure
parent: Technical Documentation
grand_parent: Researcher Console
---

### scenes.js

Manages the state of the layout from frames to scenes, any modification to those objects, and the exposes the default form information provided in each scene (but does not manage the form.)

The scenes state is comprised of four elements and is modeled below

```
conditionsLengths: [],
frames: {},
frameList: [],
scenes: {}
```

`condtionLenghts` serves as a reference for the length of each condition in their primitive/original orientation.

ex. `[1, 3, 5]` tells us there are 3 conditions where condition 1 has 1 scene, 2 has 3 scenes, etc.

`frames: {}` holds information for each frame.

- `id` allows a frame to be aware of itself when used in Vue Components
- `scenes` is a list of sceneId's within that frame

```
frames = {
  frameId: {
    id: frameId,
    scenes: [sceneId, ...]
  },
  ...
}
```

`scenes: {}` holds information for each scene

```
scenes = {
  sceneId: {
    id: sceneId,
    props: {
      /*
       This is where all the saved properties for a scene are held e.g. name, background, etc.
      */
    }
  }
}
```
