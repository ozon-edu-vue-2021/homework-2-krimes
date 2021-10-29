<template>
  <div class="link">
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
    }
  }
}
</script>

<style>
.link {
  display: flex;
}
</style>