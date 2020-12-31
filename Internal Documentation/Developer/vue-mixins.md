---
layout: page
title: Vue Mixins
permalink: /internal/dev/vue-mixins
parent: Developers
grand_parent: Internal Documentation
---

# Mixins

[Mixins](https://vuejs.org/v2/guide/mixins.html) are a useful tool not only to repeat redundant code but in some instances can also to isolate large related chunks of code that otherwise might bloat a component.

### Table of Content

[Selection Mixin](#selection-mixin)

## Selection Mixin

Isolates the parent selection logic responsible for managing the selection state and passing it down to selectable children.

Child items inheriting props from the selection system/filters generally use a `isSelectable()` function in the `computed` section of a component. However, additional computed values may further derive state from `isSelectable` or from the inherited props as well for additional functionality.

### Overview

### State

```js
// Enum for the set of modes
const Modes = {
  DEFAULT: 0,
  COPY: 1,
  BIND: 2,
  SWAP: 3,
};
```

```js
// Enum for the set of selectable types
const Select = {
  NONE: 0,
  ANY: 1,
  SCENE: 2,
  CONDITION: 3,
};
```

`modeOptions`

> defines the master object that defines all the state information in the following format

```js
[Modes.my_mode]: {                  // Name Object using an enum from Modes
  type: Number,                     // Select Enum for valid type (use `Select.ANY` for all)
  filters: [String, ...],           // Array of string filters
  actions: {                        // Holds action set that to define what action each allowed select type uses
    [Select.my_select]: function,
    ...
  },
  messages: [                       // Defines messages to display before/after
    'Select an element to copy from',
    'Select element(s) to paste to'
  ]
}
```

### Functions

```js
selectionReset();
```

**Description:**
Resets the state for selection management so it's empty

```js
addToSelection(eventId, selectedType) {
  eventId       // emitted id of item just selected
  selectedType  // type corresponding to the id of the item emitted
}
```

**Description:**
Handles adding an item to the selection system
