<template>
  <div class="tree">
    <button v-if="isDirectory" @click="isDirectoryExtend = !isDirectoryExtend">
      {{ isDirectoryExtend ? '-': '+' }}
    </button>
    <component 
      :is="componentItemType"
      :item="item"
    >
      <template v-if="isDirectory && isDirectoryExtend">
        <tree
          v-for="(subItem, index) of item.contents"
          :key="subItem.name+index"
          :item="subItem"></tree>
      </template>
    </component>
  </div>
</template>

<script>
import { File, Folder, Link } from '../TreeItem'

const TYPE = {
  DIRECTORY: "directory",
  FILE: "file",
  LINK: "link",
}
export default {
  name: 'Tree',

  components: {
    File, Folder, Link
  },

  props:{
    item: {
      type: Object,
      required: true,
    }
  },

  data() {
    return {
      isDirectoryExtend: false,
    }
  },

  computed: {
    isDirectory () {
      return this.item.type === TYPE.DIRECTORY
    },

    componentItemType () {
      const { item } = this

      switch (item.type) {
        case TYPE.DIRECTORY:
          return 'Folder'
        case TYPE.FILE:
          return 'File'
        case TYPE.LINK:
          return 'Link'
        default:
          return null
      }
    },
  },
}
</script>

<style>

</style>