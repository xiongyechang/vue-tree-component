<template>
  <div class="tree">
    <tree-node
      :data="node"
      v-for="(node, index) of data"
      :key="index">
    </tree-node>
  </div>
</template>

<script type="text/ecmascript">
  import TreeNode from './tree-node.vue';
  export default {
    name: 'tree',
    components: { TreeNode },
    provide(){
      return {
        indent: this.indent, // 依赖注入的方式将值传到子组件,孙组件,避免使用props层层往下传递的麻烦
      }
    },
    props: {
      data: {
        type: Array
      },
      indent: {
        type: Number,
        default: 16, // 缩进默认16px,一个字的大小
      }
    },
    data(){
      return {
        treeData: null,
      }
    },
    watch: {
      data: {
        handler(){
          // 传入的数据变化的时候深拷贝到本地
          // this.treeData = _.deepClone(this.data);
        },
        deep: true,
      }
    },
    created(){
      // 创建的时候把传入的数据深拷贝到本地
      // this.treeData = _.deepClone(this.data);
    },
  }
</script>

<style lang="scss" scoped>
  .tree{}
</style>