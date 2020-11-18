<template> </template>

<script lang="tsx">
import * as tsx from 'vue-tsx-support'

export default tsx.componentFactory.create({
  // It's not working.
  data() {
    return {
      a: 1,
    }
  },
  // It's working.
  // data: () => ({
  //   a: 1,
  // }),
  props: {
    text: {type: String, required: true},
    important: Boolean,
  } as const, // `as const` is needed in some cases.
  computed: {
    className(): string {
      return this.important ? 'label-important' : 'label-normal'
    },
  },
  methods: {
    onClick(event) {
      this.$emit('ok', event)
    },
  },
  render(): VNode {
    return (
      <span class={this.className} onClick={this.onClick}>
        {this.text}
      </span>
    )
  },
})
</script>
