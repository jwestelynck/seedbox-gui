<template>
  <div class="seedboxFiles">
    <img alt="Vue logo" src="../assets/logo.png">
    <tree :tree-data="tree"></tree>
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
      tree: {}
    }
  },
  components: {
    Tree
  },
  mounted(){
      axios
      .get('https://kimsuffi1-api.westelynck.fr/cgi-bin/getPathContent.py')
      .then(response => (this.tree = response['data']))
    }
}
</script>

