# HubSpot Vue Form

A Vue wrapper for HubSpot Forms

## Usage

```shell
npm install @jagaad/vue-hubspot-form
```

````vue
<template>
  <!-- using callback onReady -->
  <HubspotForm
    :onReady="onReady"
    :options="options"
    :fallback="fallback"
    :error="error"
  />

  <!-- using emit onReady -->
  <HubspotForm
    @ready="onReady"
    :options="options"
    :fallback="fallback"
    :error="error"
  />
</template>

<script setup lang="ts">
import { defineComponent } from "vue";
import HubspotForm, { Payload, CreateOptions } from "@jagaad/vue-hubspot-form";

// these values are fake, add your own
const options: CreateOptions = {
  region: "eu1",
  portalId: "83991272",
  formId: "25f1e214-1236-45c3-810m-d8dk31736c72",
  cssRequired: `.hubspot-link__container { display: none }`,
  // ...
};

/**
 * `onReady` is supoprted using callbacks or using emits
 *
 * using emit
 * ```
 * @ready="onReady"
 * ```
 *
 * using callback, can be async, loading will show until resolved
 * ```
 * :onReady="onReady"
 * ```
 */
const onReady = (payload: Payload) => console.log(payload);

// Loading Component
const fallback = defineComponent({
  /* ... */
});
// Error Component
const error = defineComponent({
  /* ... */
});
</script>
````

## Contributing

```shell
git clone git@github.com:jagaad/vue-hubspot-form.git
cd vue-hubspot-form
npm install
```

- Create a copy of `.env` file to `.env.local`
- Adjust `.env.local` to your HubSpot values

```
npm run dev
```

## Links

- https://developers.hubspot.com/docs/cms/building-blocks/forms
- https://legacydocs.hubspot.com/docs/methods/forms/advanced_form_options
- https://github.com/escaladesports/react-hubspot-form/blob/master/src/index.js

# Vue 3 + Typescript + Vite

This template should help get you started developing with Vue 3 and Typescript in Vite. The template uses Vue 3 `<script setup>` SFCs, check out the [script setup docs](https://v3.vuejs.org/api/sfc-script-setup.html#sfc-script-setup) to learn more.

## Recommended IDE Setup

- [VSCode](https://code.visualstudio.com/) + [Volar](https://marketplace.visualstudio.com/items?itemName=johnsoncodehk.volar)

## Type Support For `.vue` Imports in TS

Since TypeScript cannot handle type information for `.vue` imports, they are shimmed to be a generic Vue component type by default. In most cases this is fine if you don't really care about component prop types outside of templates. However, if you wish to get actual prop types in `.vue` imports (for example to get props validation when using manual `h(...)` calls), you can enable Volar's `.vue` type support plugin by running `Volar: Switch TS Plugin on/off` from VSCode command palette.
