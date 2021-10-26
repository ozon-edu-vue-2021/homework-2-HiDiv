<template>
  <div class="div-node">
    <span
        class="div-node_name"
        :class="{'div-node_expanded': expanded}"
        @click="onClick"
        @keypress.space.prevent="onClick"
        tabindex="0"
    >
      {{ name }}
    </span>
    <div class="div-node-contents" v-if="renderedNeed">
      <div-tree
          v-for="(item, idx) in contents"
          :key="`${item.name}-${idx}`"
          :item="item"
          v-show="expanded"
          @div-select="selectLeaf"
          @div-unselect="unselectLeaf"
      ></div-tree>
    </div>
  </div>
</template>

<script>
export default {
  inheritAttrs: false,
  name: 'DivNode',
  props: {
    name: {
      type: String,
      required: true
    },
    contents: {
      type: Array,
      required: true
    }
  },
  data: () => ({
    expanded: false,
    renderedNeed: false
  }),
  methods: {
    onClick() {
      this.renderedNeed = true
      this.expanded = !this.expanded
    },
    expandEvent(event) {
      return this.name + '/' + event
    },
    selectLeaf(event) {
      this.$emit('div-select', this.expandEvent(event))
    },
    unselectLeaf(event) {
      this.$emit('div-unselect', this.expandEvent(event))
    }
  }
}
</script>
