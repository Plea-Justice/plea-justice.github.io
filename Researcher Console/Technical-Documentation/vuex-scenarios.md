---
layout: page
title: Our VueX Structure
permalink: /console/docs/our-vuex-structure
parent: Technical Documentation
grand_parent: Researcher Console
---

# What is a Scenario

For clarity it is important to first note that scenarios are handled in two separate ways. The Vue app sees the data fetched in `/scenarios` and `/scenario/scenario_id` as separate unlike the backend which has scope to all the data at all times.

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

```js
state = {
  id: String,
  numScenes: 0,
  meta: {
    name: string,
    description: "",
    survey: "",
    live: "",
    public: false,
    readOnly: false,
    version: "",
  },
  conditions: {},
  conditionList: [],
  frames: {},
  frameList: [],
  scenes: {},
  status: {
    valid: false,
    frameErrors: [],
    sceneErrors: [],
    dirty: 0,
  },
};
```

**scenario**

- `id` corresponding scenario's id
- `numScenes` tracks how many non-blank scenes there are
- `meta: {}` basic metadata for a scenario, and it's properties should be self explanatory
- `status: {}` tracks the validation status and errors present within a frame, composed of the following:
  - `valid` simple `Boolean` to track a scenarios validity
  - `frameErrors` list of frame `id`'s relating to erroneous frames
  - `sceneErrors` list of scene `id`'s relating to erroneous scenes
  - `dirty` tracks if any updates to the store are processing (essentially a sequencer)

**frames**

- `frames: {}` holds information for each frame, composed of the following:
  - `id` corresponding frame's id
  - `scenes` ordered list of scene `id`'s within that frame (controls the order scenes are rendered in a frame)
- `frameList: []` ordered list of the frames `id`'s (controls the order frames are rendered)

```js
frames = {
  frameId: {
    id: frameId,
    scenes: [sceneId, ...]
  },
  ...
},
frameList = [frameId, ...]
```

**scenes**

- `scenes: {}` holds information for each scene
  - `id` corresponding scenes's id
  - `props` scene's form information e.g. actor, background, etc.

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
