<template>
  <div class="tree">
    <node-tree :id="id"  :node="treeData"></node-tree>
  </div>
</template>

<script>
import NodeTree from "./NodeTree";

export default {
  data: function () {
    return {
      id : 'files'
    }

  },
  props: {
    treeData: Object
  },
  components: {
    NodeTree
  },
  methods: {
    updateTree: function (elt,event){
      if (elt['type'] == 'directory') {
        this.$parent.updateTree(elt)
      }
    }
  }
};
</script>

<style>
.tree-list ul {
  padding-left: 16px;
  margin: 6px 0;
}
</style>