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
      content: {},
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

