<template>
  <div class="div-selected-items">
    <h4 class="div-selected-items-header">Выбранные элементы:</h4>
    <ul class="div-selected-items-body">
      <li
          v-for="(item, idx) in selectedItems"
          :key="idx"
          class="div-selected-item"
      >
        {{ item }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'DivShowSelectedItems',
  props: {
    selectedItems: {
      type: Array,
      required: true
    }
  }
}
</script>
