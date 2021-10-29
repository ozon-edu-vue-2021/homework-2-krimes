<template>
  <div id="app">
    <tree :item="treeData"></tree>
  </div>
</template>

<script>
import Tree from './components/Tree/Tree.vue'

export default {
  name: 'App',
  components: { 
    Tree,
  },
  data() {
    return {
      treeData: {},
    }
  },
  async mounted () {
    this.treeData = await fetch('/static/node_modules.json')
      .then(res => res.json())
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
