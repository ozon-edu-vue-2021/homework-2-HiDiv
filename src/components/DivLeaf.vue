<template>
  <div class="div-leaf">
    <span
      class="div-leaf_name"
      :class="{'div-leaf_name__selected': selected}"
      :title="$attrs.title"
      @click="onClick"
      @keypress.space.prevent="onClick"
      tabindex="0"
    >
      {{ name }}
    </span>
  </div>
</template>

<script>
export default {
  inheritAttrs: false,
  name: 'DivLeaf',
  props: {
    name: {
      type: String,
      required: true
    }
  },
  data: () => ({
    selected: false
  }),
  methods: {
    onClick() {
      this.selected = !this.selected

      this.$emit(this.selected ? 'div-select' : 'div-unselect', this.name)
    }
  }
}
</script>
