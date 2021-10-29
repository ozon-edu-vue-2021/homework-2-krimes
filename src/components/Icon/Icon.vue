<template>
  <div class="icon">
    <icon-base>
      <component :is="name"></component>
    </icon-base>
  </div>
</template>

<script>
import { Folder, File, Link } from './base-icon'
import IconBase from './IconBase.vue'
export default {
  components: { IconBase, Folder, File, Link },
  props: {
    name: {
      type: String,
    }
  }
}
</script>

<style>

</style>