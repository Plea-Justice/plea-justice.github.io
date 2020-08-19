---
layout: page
title: VueX
permalink: /console/docs/vuex
parent: Documentation
grand_parent: Researcher Console
---

# About VueX and Our Styling & Implementation

Here you will gain some general awareness of VueX, though mostly be provided to the official resources we (the designers) used as well as learning about our VueX style guide and design/implementation choices.

We are using [VueX Modules mode](https://vuex.vuejs.org/guide/modules.html) branching off of `client/stores/index.js` per the default [Nuxt Modules](https://nuxtjs.org/guide/vuex-store/) configuration.

### Sections

- [Styling](#Styling)
- [Reactivity Fundamentals](#Reactivity-Fundamentals)
- [Implementation](#Implementation-Flux-Design-Pattern)
- [Why Flux](#Why-Flux?)
- [Whats Next](#Whats-Next?)

## Styling

**Make sure to also read [Implementation](#Implementation)**

### State

[For more on State](https://vuex.vuejs.org/guide/state.html)

### Getters

Getters are named arrow functions.

`myGetter: state => state.thingIwantToReturn`

[For more on Getters](https://vuex.vuejs.org/guide/getters.html)

### Actions & Mutations

Actions & Mutations are both styled using the classic function shorthand.

`myFunction () {}`

#### Actions

Actions are used for committing to mutations or dispatching other Actions. Actions can also be async, while Mutations must be sync.

It is both recommended and we have found doing any and all logic in Actions is best as it makes mutations as simple as possible and often times re-usable resulting in cleaner, shorter, and better code.

[For more on Actions](https://vuex.vuejs.org/guide/actions.html)

For standardization **Actions** should call **Mutations** with any arguments encapsulated inside an object

`commit('myMutation', { arg1, arg2, ... })`.

This object should then be destructured in the corresponding **Mutation**

`myMutation(state, { arg1, arg2, ... })`

One notable exception that is made is for axios responses the response data should always just be one variable as:

1. these setter methods are unique to begin with
2. this reduces dot notation chaining for already embedded objects
3. the payload should only ever be the response for these type of actions

#### Mutations

Again, **Mutations** should be as simple as possible and defer all logic to the relevant **Actions**

In cases where an Action must have it's own Mutation or just in general Actions and Mutations **should be given different names for clarity**.

[For more on Mutations](https://vuex.vuejs.org/guide/mutations.html)

Beyond this it is recommended to [read the official VueX docs](https://vuex.vuejs.org).

## Reactivity Fundamentals

`Vue.set()` and `Vue.delete()` can be used for both arrays and objects. However, several array manipulations are wrapped `push(), pop(), splice(), etc.` to enable reactivity so they should be used for arrays. This can provide more specific context to a developer on how/where an array is being manipulated vs an object. For more insight read the [official Vue Docs on Reactivity](https://vuejs.org/v2/guide/reactivity.html).

Continue onto [Implementation](#Implementation-Flux-Design-Pattern) and [Why Flux](#Why-Flux?) to learn more about the design pattern.

## Implementation (Flux Design Pattern)

A [flattened or normalized pattern](https://forum.vuejs.org/t/vuex-best-practices-for-complex-objects/10143) is used where any nesting is extrapolated away.

What this means is the items are encapsulated as a set of items inside an object keyed by their (the items) unique id. While access, and any ordering to the item held inside the object is provided through an Array of these ids.

The naming convention is to have objects describe the items e.g. **boxes** and have the array have a postfix of _"List"_ after the singular of the singular form of the objects descriptor e.g. **boxList**.

This effect can then be chained, which is exactly how scenes are handled.

```js
frameList (array of frameIds) => frames[frameId] (Frame Object)
=> frame.scenes (array of sceneIds)
=> scene[sceneId] (Scene Object).
```

## Why Flux?

The [flux design pattern](<(https://facebook.github.io/flux/docs/in-depth-overview/)>) is popular across most state libraries, not just VueX. It aids in ensuring errors, performance issues, or other undesired side effects don't occur for reactivity and triggering re-renders, and creates a maintainable pattern since it's straightforward what each object should look like.

## Whats Next?

Once you've made it this far, you can learn more about the structure of our VueX implementation on the page
