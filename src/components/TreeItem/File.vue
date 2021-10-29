<template>
  <div :class="classes" @click="$emit('select', item.name)">
    <icon name="file"></icon>
    {{ item.name }} 
  </div>
</template>

<script>
import Icon from '../Icon/Icon.vue'
export default {
  components: {
    Icon
  },
  props: {
    item: {
      type: Object,
      default: () => {}
    },
    isSelect: {
      type: String,
      default: () => ''
    }
  },
  computed: {
    classes () {
      const { isSelect, item } = this

      return [
        'file',
        isSelect === item.name && 'file__selected'
      ]
    }
  }
}
</script>

<style>
.file {
  display: flex;
}
.file__selected {
  text-decoration: underline;
  color: #06a800;
}
</style>