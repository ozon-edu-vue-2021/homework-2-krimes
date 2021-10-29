<template>
  <div class="folder">
    <div class="folder__container">
      <div class="folder__extend">
        <button @click="$emit('extend')">
          {{ isExtend ? '-': '+' }}
        </button>
      </div>
      Folder: {{ item.name }} 
    </div>
    <slot></slot>
  </div>
</template>

<script>
export default {
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
}

.folder__extend { 
  width: 25px;
}
</style>