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

#### Usage

This is a simple *Choose your favorite fruits* **multiple** select:

```
<template>
  <div>
    <label>My favorite fruits:</label>
    <select2
      :options="options"
      :model.sync="selectedIdsInArr"
      :models.sync="selectedIds"
      :config="{ multiple: true, delimiter: '|' }">
    </select2>
  </div>
</template>
<script>
import Select2 from 'vue-select2-component'

export default {
  components: { Select2 },
  data: () => ({
    options: [
      { value: 1, text: 'Apple' },
      { value: 2, text: 'Banana' },
      { value: 3, text: 'Orange' },
      { value: 4, text: 'Grape' }
    ],
    selectedIdsInArr: [],
    selectedIds: ''
  })
}
</script>
```

If `Apple` and `Orange` are selected:  
```
$vm.selectedIdsInArr // ['1', '3']
$vm.selectedIds // '1|3'
```

#### Configuration

* `@prop {String/String[]} model (.sync!)`, defaults to `''`
* `@prop {String} models (.sync!)`, defaults to `''`
* `@prop {Object[]} options (required!)`, **must** format in `[{ value: {String/Number}, text: {String} }, ...]` pattern
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
