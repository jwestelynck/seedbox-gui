<template>
  <div v-bind:class='id'>
    <div v-for="(elt,name) in node" class="node" v-bind:class="[elt.type,switchClass()]"  v-on:click="updateTree(elt)" >
      <span>{{name}}</span>
      <span>{{elt.size}}</span>
      <a v-if="elt.type == 'file'" v-bind:href="elt.link" class='right'>
        <img class="download" alt='Download' src='../assets/download.svg' />
      </a>
      <img  v-if="elt.type == 'file'" class="right download" alt='Remote Download' src='../assets/remote-download.svg' v-on:click="remoteDL(elt)"/>
    </div>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: "node",
  data: function() {
    return {
      scid : 1
    }
  },
  props: {
    node: Object,
    id: String
  },
  methods: {
    switchClass: function (){
      this.scid = 1 - this.scid
      return "line"+this.scid
    },
    updateTree: function (elt,event){
      if (elt['type'] == 'directory') {
        this.$parent.updateTree(elt)
      }
    },
    remoteDL: function(elt,event){
      alert(elt)
      axios
        .get("http://192.168.100.5:5000/webapi/auth.cgi?api=SYNO.API.Auth&version=2&method=login&account=admin&passwd=AkzEak9%23&session=DownloadStation&format=cookie",)
        .then(alert(response))
    }
  }
};
</script>
