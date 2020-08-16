---
layout: page
title: VueX
permalink: /console/docs/vuex
parent: Technical Documentation
grand_parent: Researcher Console
---

# VueX

The VueX implementation uses the Modules mode branching off of `index.js` per the [Nuxt Modules ](https://nuxtjs.org/guide/vuex-store/) standard.

## Styling

Getters are names arrow functions
`myGetter: state => state.thingIwantToReturn`

Actions, and Mutations are both styled as classic functions.

Actions do any logic before state is touched and are primarily used for committing to mutations. Actions are async, while mutations are sync.

For standardization **Actions** should call **Mutations** with any arguments encapsulated inside an object `{ arg1, arg2, ... }`. This object should then be captured in the corresponding **Mutation** as **payload** `(state, payload)`.

One notable exception that is made is for axios responses the response data is sent as:

1. these setter methods are different to begin with
2. this reduces dot notation chaining for already embedded objects
3. the payload should only ever be the response for these type of actions.

Actions and Mutations should also be given different names for clarity.

### Modifying State

`Vue.set()` and `Vue.delete()` can be used for both arrays and objects. However, several array manipulations are wrapped `push(), pop(), splice(), etc.` to allow reactivity so they should be used for arrays. This can provide more specific context on how an array is being manipulated and makes differentiating between wether a stateful arrays or objects is being modified easier. See the [Vue Docs on Reactivity](https://vuejs.org/v2/guide/reactivity.html) for more information on what's possible.

## Implementation

A [flattened or normalized pattern](https://forum.vuejs.org/t/vuex-best-practices-for-complex-objects/10143) is used where any nesting is extrapolated away.

What this basically means is individual item objects are encapsulated inside an object keyed by their (the items) ID. While access to their ID's is provided through an Array, generally these arrays should also be ordered and are where all the ordering happens.

The naming convention is to have objects describe the items e.g. **boxes** and the array have a postfix of List after the singular of the singular form of the objects descriptor e.g. **boxList**.

This effect can then be chained. `boxList (array) -> boxes[boxId] (Object) -> boxes[boxId].scenes (array of itemId's) -> items[itemId] (Object).`

### Why

This pattern is popular across several other state libraries as well as VueX, helps to ensure errors or performance issues don't occur regarding reactivity and triggering re-renders, and creates a maintainable pattern since it's straightforward what each object should look like.

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
