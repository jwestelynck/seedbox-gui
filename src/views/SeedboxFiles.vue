<template>
  <div id='content'>
    <div id="header">
      Seedbox Files
    </div>
    <parent-tree :parents="parents"></parent-tree>
    <tree :tree-data="content"></tree>
  </div>
</template>

<script>
// @ is an alias to /src
import Tree from "@/components/Tree";
import ParentTree from "@/components/ParentTree";
import axios from 'axios';

export default {
  name: 'seedboxFiles',
  data: function() {
    return {
      content: [],
      parents : {}
    }
  },
  components: {
    Tree,
    ParentTree
  },
  mounted(){
      axios
      .get('https://kimsuffi1-api.westelynck.fr/cgi-bin/getPathContent.py')
      .then(response => (
        this.content = response['data']['content'],
        this.parents = response['data']['parents']
        )
      )
    },
  methods: {
    reorder: function(type,order){

      function nameasc(a,b){
        if(a.name < b.name)
          return -1;
        if(a.name > b.name)
          return 1;
        return 0;
      }
      
      function namedes(a,b){
        if(a.name < b.name)
          return 1;
        if(a.name > b.name)
          return -1;
        return 0;
      }
      
      function sizeasc(a,b){
        if(a.size < b.size)
          return -1;
        if(a.size > b.size)
          return 1;
        return 0;
      }
      
      function sizedes(a,b){
        if(a.size < b.size)
          return 1;
        if(a.size > b.size)
          return -1;
        return 0;
      }

      if(type == 'name' && order == 'asc'){
        this.content.sort(nameasc);
        console.log("nameasc");
      }else if(type == 'name' && order == 'des'){
        this.content.sort(namedes);
        console.log("namedes");
      }else if(type == 'size' && order == 'asc'){
        this.content.sort(sizeasc);
        console.log("sizeasc");
      }else if(type == 'size' && order == 'des'){
        this.content.sort(sizedes);
        console.log("sizedes");
      }
    },
    updateTree: function (elt,event){
      if (elt['type'] == 'directory') {
        axios
        .get('https://kimsuffi1-api.westelynck.fr/cgi-bin/getPathContent.py?id='+elt.id)
        .then(response => (
          this.content = response['data']['content'],
          this.parents = response['data']['parents']
          )
        )
      }
    }
  }
}
</script>

