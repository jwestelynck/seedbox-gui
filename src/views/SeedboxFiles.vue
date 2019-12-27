<template>
  <div id='content'>
    <div id="header">
      Seedbox Files
    </div>
    <tree :tree-data="content"></tree>
  </div>
</template>

<script>
// @ is an alias to /src
import Tree from "@/components/Tree";
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
    Tree
  },
  mounted(){
      axios
      .get('https://kimsuffi1-api.westelynck.fr/cgi-bin/getPathContent.py')
      .then(response => (
        this.content = response['data']['content'],
        this.parents = response['data']['parents']
        )
      )
    }
}
</script>

