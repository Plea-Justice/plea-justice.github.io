---
layout: page
title: Our VueX Structure
permalink: /console/docs/our-vuex-structure
parent: Technical Documentation
grand_parent: Researcher Console
---

# What is a Scenario

For clarity it is important to note that scenarios are handled in two separate ways. The Vue app sees the data fetched in `/scenarios` and `/scenario/scenario_id` as separate unlike the backend which has scope to all the data at all times.

### Scenarios

`store/scenarios.js` holds the card data for `/scenarios`. It holds a list of all the available scenarios but only has access to the limited amount of that data that it needs, specifically the metadata for a scenario.

[Jump to scenarios.js](#scenarios.js)

### Scenes (current working scenario)

`store/scenes.js` holds the full set of data for the current open scenario. It's name, while not perfect, was given to help prevent the ambiguity if it were called "scenario".

The reason the VueX store simply does not hold the full state of data is stores can also be seen as a cache of data, from that perspective it is useless, excessive, and simply less clear (due to lack of focus) for the application to scope the full set of every scenario's data in one place. Modularity and compartmentalization is our friend here for performance and clarity.

[Jump to scenes.js](#scenes.js)

## scenarios.js

**This is currently a stub, WIP**

## scenes.js

Manages the state of the layout from frames to scenes, and any modification to those objects.

The following sections will provide a breakdown of the `scenes.js` store.

### State

Scenes store state is comprised of several elements modeled below

| Props       | Type     | Description                                                                               |
| ----------- | -------- | ----------------------------------------------------------------------------------------- |
| `id`        | `String` | Corresponding scenario's id                                                               |
| `numScenes` | `Number` | Tracks how many non-blank scenes there are                                                |
| `meta`      | `Object` | Basic metadata for a scenario, and it's properties should be self explanatory             |
| `status`    | `Object` | Tracks the validation status and errors present within a frame, composed of the following |
| `frames`    | `Object` | Holds information for each frame                                                          |
| `frameList` | `Array`  | Ordered list of the frames `id`'s (controls the order frames are rendered)                |
| `scenes`    | `Object` | Holds information for each scene                                                          |

#### status

> Tracks the validation status and errors present within a frame

| Props         | Type      | Description                                                                 |
| ------------- | --------- | --------------------------------------------------------------------------- |
| `valid`       | `Boolean` | Tracks a scenarios validity                                                 |
| `frameErrors` | `Array`   | List of frame `id`'s relating to erroneous frames                           |
| `sceneErrors` | `Array`   | List of scene `id`'s relating to erroneous scenes                           |
| `dirty`       | `Number`  | Tracks if any updates to the store are processing (essentially a sequencer) |

#### frames

> Holds information for each frame, composed of the following:

| Props    | Type     | Description                                                                                      |
| -------- | -------- | ------------------------------------------------------------------------------------------------ |
| `id`     | `String` | Corresponding frame's id                                                                         |
| `scenes` | `Array`  | Ordered list of scene `id`'s within that frame (determines order scenes are rendered in a frame) |

Code Outline:

```js
frames = {
  frameId: {
    id: frameId,
    scenes: [sceneId, ...]
  },
  ...
}
```

#### scenes

> Holds information for each scene

| Props   | Type     | Description                                           |
| ------- | -------- | ----------------------------------------------------- |
| `id`    | `String` | Corresponding scenes's id                             |
| `props` | `Object` | Scene's form information e.g. actor, background, etc. |

Code Outline:

```js
scenes = {
  sceneId: {
    id: sceneId,
    props: {},
  },
};
```

### Actions

```js
actions = {
  // **** Axios Actions ****
  async getScenario({ commit, dispatch, state }, id) {},
  async saveScenario({ state }) {},
  async saveMeta({ state }) {},

  // **** Scenario Actions ****
  updateMeta({ commit }, meta) {},

  // **** Condition Actions ****
  addCondition({ commit }) {},
  removeCondition({ commit, dispatch, state }, id) {},
  async copyConditions({ dispatch, state, getters }, idList) {},
  updateTags({ commit }, { id, tags }) {},

  // **** Frame Actions ****
  addFrame({ commit, state }, frameId = null) {},
  removeFrame({ commit, state }, id) {},
  moveFrameDown({ commit }, id) {},
  moveFrameUp({ commit }, id) {},
  setFrameLabel({ commit }, { id, value, valid }) {},

  // **** Scene Actions ****
  addScene({ commit, state, getters }, id) {},
  removeScene({ commit, state, getters }, id) {},
  updateScene({ commit }, { valid, id, props }) {},
  copyScenes({ commit, state }, [parentId, ...childIds]) {},
  bindScenes({ commit, state }, [parentId, ...childIds]) {},
  unbindScene({ commit, state }, { id, props }) {},
  swapScene({ commit, state }, [id1, id2]) {},
};
```

### Mutations

```js
export const mutations = {
  // **** Module Mutations ****
  resetState(state) {},

  // **** Axios Mutations ****
  setScenario(state, scenario) {},

  // **** Scenario Mutations ****
  updateMeta(state, payload) {},
  updateSceneCount(state, { modifier, frameId }) {},
  updateFrameErrors(state, { valid, id }) {},

  // **** Condition Mutations ****
  newCondition(state) {},
  deleteCondition(state, { index, id, isLast }) {},
  setTags(state, { id, tags }) {},

  // **** Frame Mutations ****
  newFrame(state, { index, id, frame }) {},
  deleteFrame(state, { id }) {},

  // **** Scene Mutations ****
  setScene(state, { id, scene }) {},
  setSceneProps(state, payload) {},
};
```
