<template>
  <div class="tree">
    <div class="tree__item">
      <component 
        :is="componentItemType"
        :item="item"
        :is-extend="isDirectoryExtend"
        :is-select="isSelect"
        @extend="doExtend"
        @select="$listeners.select"
      >
        <template v-if="isDirectory && isDirectoryExtend">
          <tree
            v-for="(subItem, index) of item.contents"
            :key="subItem.name+index"
            :item="subItem"
            :level="level + 1"
            :is-select="isItemSelected"
            @select="(item) => isItemSelected = item"
          ></tree>
        </template>
      </component>
    </div>
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
    },
    level: {
      type: Number,
      default: () => 0
    },
    isSelect: {
      type: String,
    },
  },

  data() {
    return {
      isDirectoryExtend: false,
      isItemSelected: null,
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

    // calcMargin () {
    //   const { level } = this

    //   return { marginLeft: level * 25 + 'px' }
    // }
  },

  methods: {
    doExtend () {
      if (this.isDirectoryExtend) {
        this.isItemSelected = null
      }
      this.isDirectoryExtend = !this.isDirectoryExtend
    },
  }
}
</script>

<style>
.tree {
  display: block;
  margin-left: 25px;
}
</style>