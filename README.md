# Vue Select2 Component

[![npm version][npm-v-img]][npm-url]
[![npm download][npm-dl-img]][npm-url]

> Intellectual property of [Oneway.mobi](http://www.oneway.mobi/)

#### Requirement

* Vue 1.x
* jQuery ( available globally )
* [Select2](https://github.com/select2/select2)

#### Installation

`npm i vue-select2-component -S`

> alternatively: `<script src="dist/vue-select2-component.min.js"></script>`  
> which exposes **`VueSelect2`** as a global variable


#### Example
See [here](https://kenberkeley.github.io/vue-select2-component/example.html), source in [`example.html`](./example.html)
> I prefer inspecting it with [devtools](https://github.com/vuejs/vue-devtools)

#### Configuration

* `@prop {String/String[]} model (.sync!)`, defaults to `''`
* `@prop {String} models (.sync!)`, defaults to `''`
* `@prop {Object[]} options (required!)`, **must** in `[{ value: {String/Number}, text: {String} }]` pattern
* `@prop {Object} config`, defaults to `{}`. Besides the [basic configuration](http://select2.github.io/options.html) of Select2, we have some extra settings:
  * `multiple`: defaults to `undefined` ( Meaning default as a single select )
  * `width`: defaults to `100%`
  * `delimiter`: defaults to `,` ( Only for multiple select )
  * `showValInText`: defaults to `undefined`. If set to `true`, the render result would be:  
```
    <select>
      <option>(1) Apple</option>
      <option>(2) Banana</option>
      ...
    </select>
```

#### Build

`npm run build`

[npm-url]: https://www.npmjs.com/package/vue-select2-component
[npm-v-img]: http://img.shields.io/npm/v/vue-select2-component.svg
[npm-dl-img]: http://img.shields.io/npm/dm/vue-select2-component.svg
