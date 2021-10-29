<template>
  <div :class="classes" @click="$emit('select', item.name)">
    <icon name="link"></icon>
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
        'link',
        isSelect === item.name && 'link__selected'
      ]
    }
  }
}
</script>

<style>
.link {
  display: flex;
}
.link__selected {
  text-decoration: underline;
  color: #ad65ff;
}
</style>