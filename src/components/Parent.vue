<template>
    <span v-on:click="updateTree('test')">test</span>
</template>

<script>

export default {
  methods: {
    updateTree: function (elt,event){
      if (elt['type'] == 'directory') {
        this.$parent.updateTree(elt)
      }
    }
  }
};
</script>