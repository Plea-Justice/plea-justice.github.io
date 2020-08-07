---
layout: page
title: Importing and Fetching Data
permalink: /console/docs/importing-and-fetching-data
parent: Technical Documentation
grand_parent: Researcher Console
---

## Static Data

This is data that can't and won't be changed while the app is running. So instead, it makes use of code-splitting for optimization.

This data should also not be put into the `static/` directory as everything in that folder is served after being built. `assets/` would be an appropriate place for this.

[More Info](https://github.com/nuxt/nuxt.js/issues/123)

```
<script>
  export default {
    async asyncData({ params }) {
      const spec = await (() => import(`~/data/spec.json`).then(m => m.default || m))();
      return { spec };
    }
  }
<script/>
```

## Dynamic access to Static Data

Data that needs to be called dynamically or might change during runtime but is/should be packed into the build can be accessed internally by directing Axios to `static/` as described on the [Axios](/console/docs/axios) page
