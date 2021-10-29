<template>
  <div class="folder">
    <div class="folder__container" @click="$emit('extend')">
      <div class="folder__extend">
        <button>
          {{ isExtend ? '-': '+' }}
        </button>
      </div>
      <icon name="folder"></icon>
      {{ item.name }} 
    </div>
    <slot></slot>
  </div>
</template>

<script>
import Icon from '../Icon/Icon.vue'
export default {
  components: {
    Icon,
  },

  props: {
    item: {
      type: Object,
      default: () => {}
    },
    level: {
      type: Number,
      default: () => 0,
    },
    isExtend: {
      type: Boolean,
      default: () => false
    }
  }
}
</script>

<style>
.folder__container {
  display: flex;
  padding-left: 2px;
  margin-top: 2px;
}

.folder__extend { 
  width: 25px;
}
</style>