<template>
  <select v-model="model" :multiple="conf.multiple" :style="{ width: conf.width }">
    <option v-for="opt in options" :value="opt.value">
      <template v-if="conf.showValInText">({{ opt.value }})</template>
      {{ opt.text }}
    </option>
  </select>
</template>
<script>
/**
 * Select2 encapsulation for Vue 1.x
 * (https://select2.github.io)
 */
export default {
  props: {
    model: { twoWay: true, default: '' },
    models: { twoWay: true, default: '' },
    options: { type: Array, required: true },
    config: { type: Object, default: () => ({}) }
  },
  computed: {
    conf () {
      return {
        width: '100%',
        allowClear: true,
        delimiter: ',', // for multi-select
        placeholder: '',
        // default config shown as above
        ...this.config
      }
    }
  },
  attached () {
    this.init()
    const $el = $(this.$el)
    $el.on('change', () => this.model = $el.val())
  },
  watch: {
    options () {
      this.init()
    },
    model (v) {
      this.init()
      this.sync(true)
    },
    models (v) {
      this.sync()
    }
  },
  methods: {
    init () {
      this.$nextTick(() => $(this.$el).select2(this.conf))
    },
    sync (flag) {
      const { multiple, delimiter } = this.conf
      if (!multiple) return
      flag ? // flag ? model ===> models : model <=== models
        this.models = (this.model || []).join(delimiter) :
        this.model = this.models.split(delimiter)
    }
  }
}
</script>
