<template>
  <div>
    Folder: {{ item.name }} 
    <slot></slot>
  </div>
</template>

<script>
export default {
  props: {
    item: {
      type: Object,
      default: () => {}
    }
  }
}
</script>

<style>

</style>