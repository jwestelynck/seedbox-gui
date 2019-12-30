<template>
  <div v-bind:class='id'>
    <input v-bind:class="['searchField']" v-model="searchString" placeholder="Search Field" />
    <div v-for="(elt,name) in node" class="node" v-bind:class="[elt.type,switchClass()]"  v-on:click="updateTree(elt)" v-if='filter(name)'>
      <span>{{name}}</span>
      <a v-if="elt.type == 'file'" v-bind:href="elt.link" class='right'>
        <img class="download" alt='Download' src='../assets/download.svg' />
      </a>
      <img  v-if="elt.type == 'file'" class="right download" alt='Remote Download' src='../assets/remote-download.svg' v-on:click="remoteDL(elt)"/>
      <span v-if="elt.type == 'file'" v-bind:class="['filesize','right']">{{fileConvertSize(elt.size)}}</span>
    </div>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: "node",
  data: function() {
    return {
      scid : 1,
      searchString: ""
    }
  },
  props: {
    node: Object,
    id: String
  },
  methods: {
    filter: function(name){
      var re = null;
      if(this.searchString == ""){
        re = new RegExp('.*', 'i');
      }else{
        re = new RegExp('.*'+this.searchString+'.*', 'i');
      }
      var result = name.match(re);
      if(result == null){
        return false;
      }else{
        return true
      }
    },
    fileConvertSize: function(aSize){
      aSize = Math.abs(parseInt(aSize, 10));
      var def = [[1, 'octets'], [1024, 'ko'], [1024*1024, 'Mo'], [1024*1024*1024, 'Go'], [1024*1024*1024*1024, 'To']];
      for(var i=0; i<def.length; i++){
        if(aSize<def[i][0]) return (aSize/def[i-1][0]).toFixed(2)+' '+def[i-1][1];
      }
    },
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
        .get("http://XXXX:5000/webapi/auth.cgi?api=SYNO.API.Auth&version=2&method=login&account=admin&passwd=AkzEak9%23&session=DownloadStation&format=cookie",)
        .then(alert(response))
    }
  }
};
</script>
