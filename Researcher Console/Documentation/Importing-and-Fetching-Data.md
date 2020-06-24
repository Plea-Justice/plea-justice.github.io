---
layout: page
title: Importing and Fetching Data
permalink: /console/docs/importing-and-fetching-data
parent: Documentation
grand_parent: Researcher Console
---
## Static Data
This is data that isn't and can't be changed while the app is running. Instead, it makes use of code-splitting and builds optimizations.

This data should also generally not be put into the `static/` since everything in that folder is served after being built and the data is already injected in by the bundler (WebPack) at build time. Currently, the `~/data/` is being used for this.

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
Data that needs to be called dynamically or might change during runtime but is/should be packed into the build can be accessed internally by directing Axios to the `static/` as explained in the **Axios** section.

