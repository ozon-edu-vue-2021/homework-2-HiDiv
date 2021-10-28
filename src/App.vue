<template>
  <div id="app">
    <div>
      <div-show-selected-items :selected-items="selected"></div-show-selected-items>
    </div>
    <div>
      <div-tree
          class="div-root-node"
          :item="items"
          @div-select="selectItem"
          @div-unselect="unselectItem"
      ></div-tree>
    </div>
  </div>
</template>

<script>
import items from '/public/static/node_modules.json'
import DivTree from "@/components/DivTree.vue"
import DivShowSelectedItems from "@/components/DivShowSelectedItems";
import Vue from "vue";

Vue.component('div-tree', DivTree)

export default {
  name: 'App',
  components: {
    DivShowSelectedItems
  },
  data: () => ({
    items: items,
    selected: []
  }),
  methods: {
    selectItem(event) {
      this.selected.push(event)
    },
    unselectItem(event) {
      const idx = this.selected.indexOf(event)
      if (~idx) {
        this.selected.splice(idx, 1)
      }
    }
  }
}
</script>

<style>
body {
  margin: 0;
  padding: 20px;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: black;
  font-size: 16px;
  margin-top: 20px;
}

.div-root-node {
  display: inline-flex;
  background-color: beige;
  border-radius: 8px;
  font-size: 16px;
  line-height: 1;
  color: black;
  box-sizing: border-box;
  padding: 8px;
  margin-top: 16px;
  outline: none;
}

.div-tree {
  display: inline-flex;
  flex-direction: column;
  flex-wrap: nowrap;
}

.div-node {
  display: inline-flex;
  flex-direction: column;
  flex-wrap: nowrap;
}

.div-node_name {
  display: inline-flex;
  cursor: pointer;
  padding: 8px;
}

.div-node_name:hover {
  background-color: #00000026;
}

.div-node_name:focus-visible {
  background-color: #00000026;
  outline: #00000080 solid 1px;
}

.div-node_name:before {
  content: '';
  display: block;
  width: 16px;
  height: 16px;
  margin-right: 4px;
  background-image: url("assets/folder.svg");
  background-size: contain;
  background-repeat: no-repeat;
}

.div-node_name.div-node_expanded:before {
  background-image: url("assets/folder-open.svg");
}

.div-node-contents {
  display: inline-flex;
  flex-direction: column;
  flex-wrap: nowrap;
  padding-left: 18px;
}

.div-leaf {
  display: inline-flex;
  flex-direction: column;
  flex-wrap: nowrap;
}

.div-leaf_name {
  display: inline-flex;
  cursor: pointer;
  padding: 8px;
}

.div-leaf_name:hover {
  background-color: #00000026;
}

.div-leaf_name:focus-visible {
  background-color: #00000026;
  outline: #00000080 solid 1px;
}

.div-leaf_name:before {
  content: '';
  display: block;
  width: 16px;
  height: 16px;
  margin-right: 4px;
  background-image: url("assets/file-alt.svg");
  background-size: contain;
  background-repeat: no-repeat;
}

.div-leaf_name__selected {
  font-weight: bold;
  color: #476fac;
}

.div-leaf.div-link .div-leaf_name:before {
  background-image: url("assets/link.svg");
}

.div-selected-items {
  display: inline-flex;
  flex-direction: column;
  flex-wrap: nowrap;
  background-color: beige;
  border-radius: 8px;
  font-size: 16px;
  line-height: 1;
  color: black;
  box-sizing: border-box;
  padding: 8px;
  outline: none;
}

.div-selected-items-header {
  font-size: 1.5em;
  font-weight: bold;
  margin: 16px 0;
}

.div-selected-items-body {
  margin: 0;
  padding: 0 0 0 20px;
}

.div-selected-item {
  padding: 8px;
}
.div-selected-item:hover {
  background-color: #00000026;
}
</style>
