<template>
  <div class="parent-tree">
    <div class='parentHome' v-on:click="updateTree('Home')"></div>
    <section v-for="(elt,name) in parents">
      <div class='separator'>/</div>
      <div v-on:click="updateTree(elt)">{{name}}</div>
    </section>
  </div>
</template>

<script>
import Parent from "./Parent";

export default {
  props: {
    parents: Object
  },
  methods: {
    updateTree: function (elt,event){
      console.log(elt)
      if(elt == 'Home'){
        elt = {
          id : 'Home'
        }
        console.log(elt)
      }
      elt['type'] = 'directory'
      this.$parent.updateTree(elt)
    }
  }
};
</script>

<style>
div.parent-tree {
  padding-top: 4vh;
  padding-bottom: 1vh;
  padding-left: 1vw;
  float:left;
}

div.parent-tree div{
  font-weight:bold;
  float:left;
}

div.parent-tree div:hover{
  color: DarkBlue;
  cursor: pointer;
}

div.parent-tree section{
  float:left;  
  margin-top: 0.75em;
}
div.parent-tree .separator{
  height: 1em;
  width: 1em;
  text-align:center;
}

</style>