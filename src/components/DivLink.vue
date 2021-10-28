<template>
  <div-leaf
      class="div-link"
      :name="name"
      :title="target"
      @div-select="$emit('div-select', $event)"
      @div-unselect="$emit('div-unselect', $event)"
  ></div-leaf>
</template>

<script>
import DivLeaf from "@/components/DivLeaf";

export default {
  inheritAttrs: false,
  name: 'DivLink',
  components: {
    DivLeaf
  },
  props: {
    name: {
      type: String,
      required: true
    },
    target: {
      type: String,
      default: ''
    }
  }
}
</script>

<style scoped>

</style>