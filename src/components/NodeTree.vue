<template>
  <div>
    <div v-for="(elt,name) in node" v-bind:class='elt.type'>
      <span>{{elt.type}}</span> <span>{{name}}</span> <span>{{elt.size}}</span> <a v-if="elt.type == 'file'" v-bind:href="elt.link">Download</a>
      <div v-if="elt.type == 'directory'" v-bind:id="elt.id">
        <node :node="elt.content" ></node>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "node",
  props: {
    node: Object
  },
  computed: {
    seenArray: function(){
      var directoriesID = {}
      for(var elt in this.node){
        if(this.node[elt]['type'] == 'directory'){
          directoriesID[this.node[elt]['id']] = false
        }
      }
      return directoriesID
    }
  },
  methods: {
    changeVisibility: function(id){
      console.log(this.seenArray[id])
      this.seenArray[id] = !this.seenArray[id]
    }
  }
};
</script>
