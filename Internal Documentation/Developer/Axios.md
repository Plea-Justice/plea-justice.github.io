---
layout: page
title: Using Axios in Nuxt
permalink: /internal/dev/axios
parent: Developers
grand_parent: Internal Documentation
---

### Sections

- [Usage](#Usage)
- [Environments: Deploying & Production](#Setting-up-Axios-for-Deploy)
- [Error Handling](#Error-Handling)

## Usage

The internal `@nuxtjs/axios` package should be used.

Do **NOT** `import axios from "axios"` this will work since `axios` is a sub dependency of `@nuxtjs/axios` however is incorrect.

Using the internal `@nuxtjs/axios` package doesn't require any imports and uses a special `$` prefix to identify itself and any of it's chained methods. For instance if you want to call `axios.get()` You would do `$axios.$get()`, more on this [here.](https://axios.nuxtjs.org/usage.html#store-actions)

The best and most expressive way to access axios from this package is by passing it as an argument inside curly braces to the components constructor, e.g. `thisIsAFunction ({ $axios }) { yourCodeHere }`.

Generally speaking axios get requests should be used with the `async asyncData() {}` parameter of a given Vue Page or Component.

A full example of this is offered below...

```
<script>
export default {
  name: "componentName",
  async asyncData({ $axios }) {
    let conditions = await $axios.$get("/expirement.json");

    return { conditions };
  },
  head() {
    return {
      title: `PleaBargain | StoryBoard`,
      meta: [
        {
          hid: "description",
          name: "description",
          content: "The StoryBoard Timeline"
        }
      ]
    };
  }
};
</script>
```

[More on Usage](https://axios.nuxtjs.org/usage.html)

## Setting up Axios for Deploy

While `npm run dev` will run axios correctly on your `localhost:{yourPortName}`, when deploying it will try to access localhost instead of the URL it has been deployed to.

One way to fix this is to add a static value for the URL being used; However, a much simpler way is to simply use '/' which will automatically resolve to itself.

To do this open the `nuxt.config.js` file in the root directory and add or modify the `axios: {}` options object underneath `modules: []`, for instance...

```

export default {
  .
  .
  .
  /*
  ** Nuxt.js modules
  */
  modules: [
    // Doc: https://axios.nuxtjs.org/usage
    '@nuxtjs/axios',
  ],
  /*
  ** Axios module configuration
  ** See https://axios.nuxtjs.org/options
  */
  axios: {
    baseURL: '/' //or add the static URL here (less convenient)
  }
  .
  .
  .
}

```

Described Method (Simpler, not quite as broad):
[Resource on using Axios baseURL option](https://github.com/nuxt-community/axios-module/issues/134)

Alternative (More complicated, uses global environment):
[Resource on using Axios plugin & env global](https://medium.com/from-zero-to-hero-of-free-web-development/vue-js-and-nuxt-js-quickstart-tutorial-part-3-c445c1a063ef)

## Error Handling

The vast majority of the research console relies on [axios error interceptors](https://axios.nuxtjs.org/helpers.html#interceptors), as most errors have the same outcome and this helps to prevent duplicate and/or poorly scoped code.

this file can be found under `~/client/plugins/axios.js`
