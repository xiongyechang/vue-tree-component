<template>
  <div id="app">
    <tree :data="data"></tree>
  </div>
</template>

<script type="text/ecmascript">
import tree from './components/tree.vue'

export default {
  name: 'app',
  components: {
    tree
  },
  data(){
    return {
      data: [{
        title: '一级标题1',
        expand: false,
        level: 0,
        children: [{
          title: '二级标题1-1',
          expand: false,
          level: 1,
          children: [],
        }]
      },{
          title: '一级标题2',
          expand: false,
          level: 0,
          children: [{
            title: '二级标题2-1',
            expand: false,
            level:1,
            children: [],
          }]
        }]
    }
  },
}
</script>

<style>
</style>
