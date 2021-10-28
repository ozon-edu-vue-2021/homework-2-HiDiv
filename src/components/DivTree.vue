<template>
  <div class="div-tree">
    <div-node
        v-if="type === 'directory'"
        :name="name"
        :contents="contents"
        @div-select="$emit('div-select', $event)"
        @div-unselect="$emit('div-unselect', $event)"
    ></div-node>

    <div-link
        v-else-if="type === 'link'"
        :name="name"
        :target="target"
        @div-select="$emit('div-select', $event)"
        @div-unselect="$emit('div-unselect', $event)"
    ></div-link>

    <div-leaf
        v-else
        :name="name"
        @div-select="$emit('div-select', $event)"
        @div-unselect="$emit('div-unselect', $event)"
    ></div-leaf>
  </div>
</template>

<script>
import DivLeaf from "@/components/DivLeaf.vue"
import DivLink from "@/components/DivLink.vue"
import DivNode from "@/components/DivNode.vue"

export default {
  inheritAttrs: false,
  name: 'DivTree',
  components: {
    DivLeaf,
    DivLink,
    DivNode
  },
  props: {
    item: {
      type: Object,
      required: true
    }
  },
  computed: {
    name() {
      return this.item.name ?? ''
    },
    type() {
      return this.item.type ?? 'file'
    },
    target() {
      return this.type === 'link' && this.item.target ? this.item.target : undefined
    },
    contents() {
      return this.type !== 'directory' ? undefined : this.item.contents ?? []
    }
  }
}
</script>
