---
layout: page
title: Importing and Fetching Data
permalink: /console/docs/importing-and-fetching-data
parent: Documentation
grand_parent: Researcher Console
---

### sections

- [Static Data](#Static-Data)
- [When to use `/static` vs `/assets`](#When-to-use-/static-vs-/assets)
- [Lazy Load Assets](#Lazy-loading-assets)

## Static Data

Static data is data that can't and won't be changed while the app is running. When this is known, optimizations can be made in the way of code-splitting, etc.

## When to use `/static` vs `/assets`

### Static

Static data is independently served from the server after being built no matters what. Static data should only ever by used by `href` this can be useful for things like default img `src` like an icon used throughout the site.

### Assets

Data that is in anyway imported and/or un-compiled should always be in assets. Assets is essentially a place put there by Nuxt for you to access any data that you may want to use across your application.

For instance we have global styles which are imported in `nuxt.config.js`, `util.js` utility functions that can be accessed by anywhere in the app appropriate, or even `spec.json` even though it a JSON is completely static notice since it is an imported resource it goes in `assets/`

## Lazy Load Assets

[More Info](https://github.com/nuxt/nuxt.js/issues/123)

```js
<script>
  export default {
    async asyncData({ params }) {
      const spec = await (() => import(`~/assets/spec.json`).then(m => m.default || m))();
      return { spec };
    }
  }
<script/>
```
