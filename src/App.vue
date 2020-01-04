<template>
  <div id="app">
    <div id="nav">
      <router-link to="/"><div class="divLink">Home</div></router-link>
      <router-link to="/about"><div class="divLink">About</div></router-link>
      <router-link to="/seedboxFiles"><div class="divLink">Seedbox Files</div></router-link>
    </div>
    <router-view/>
    <div id='footer'></div>
  </div>
</template>

<style>

* {
  margin: 0;
  padding: 0;
}

a:link {
  text-decoration: none;
}

body {
  font-size: 100%;
  margin: 0;
  min-height: 100vh;
}

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}

#nav {
  padding-top: 15vh;
  float:left;
  width: 10vw;
  height: 85vh;
  background-color: #1e1e1e;
  text-align:center;
}

#nav a {
  display: block;
}

#nav a:hover {
  background-color: #2E2E2E;
}

#nav a:active {
  background-color: #2E2E2E;
}

.divLink {  
  padding-top: 2vh;
  padding-bottom: 2vh;
  color:#E0E0E0;
}

#main {
  float:left;
  width: 85vw;
  height: 100vh;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
div.left {
  float: left;
}
#content {
  float: left;
  width:89vw;
  margin-bottom: 1vh;
  height: 98vh;
}

div.tree {
  float:left;
  height: 80vh;
  padding-left: 2vw;
  padding-top: 2vh;
  padding-bottom: 2vh;
  width:88vw;
  overflow-y:scroll;
  overflow-x:hidden;
}
#footer {
  float:left;
  background-color: #1e1e1e;
  min-height: 1vh;
  width: 90vw;
}

#header{
  float:left;
  width: 89vw;
  font-weight:bolder;
  padding-top: 3vh;
  padding-bottom: 3vh;
  padding-left: 1vw;
  background-color: #F0F0F0;
  color: #1e1e1e;
}

#main {
  float:left;
}

div.node {
  padding-top: 1.5vh;
  padding-bottom: 1.5vh;
  padding-left: 2.75em;
  padding-right: 1vw;
  width: 83vw;
  font-weight:500;
}

div.directory:hover {
  background-color: #E8E8E8;
  cursor:pointer;
  color:darkblue;
}

div.directory {
  background: url('assets/folder.svg') no-repeat;
  background-size: auto 1.5em;
  background-position: 0.5vw 50%;
  fill: DarkBlue;
}

div.file {
  background: url('assets/file.svg') no-repeat;
  background-size: auto 1.5em;
  background-position: 0.5vw 50%;
}

div.line0{
  background-color: #FAFAFA;
}

div.line1{
  background-color: #F3F3F3;
}
.right{
  float:right
}
img.download {
  height: 1.25em;
  margin-right: 1vw;
}
img.download:hover {
  cursor: pointer;
}

.filesize {
  color:rgb(3, 3, 73);
  font-weight:500;
  margin-right: 1vw;
}

.filesizeDir{
  color:rgb(3, 3, 73);
  font-weight:500;
  margin-right: 4.5vw;
}

.searchField {
  font-weight:500;
  margin-left: 1vw;
}

.FileMenu {
  padding-top: 1.5vh;
  padding-bottom: 1.5vh;
  padding-left: 2.75em;
  padding-right: 1vw;
  width: 83vw;
  font-weight: bold;
  background-color:#1e1e1e;
  color:#E0E0E0;
}

.FileMenuName {
  float:left;  
}

.FileMenuName:hover {
  cursor:pointer;
}

.FileMenuSize {  
  cursor:pointer;
  float:right;  
  padding-right:1vw;
}

.FileMenuActions {
  padding-left: 1.15vw;
  padding-right: 1.15vw;
  float:right;    
}

.sort {
  height:1em;
  width:1em;
  margin-left: 0.2em;
}
.sortasc{
  height: 0.5em;
  width: 1em;
  mask: url('assets/asc.svg') no-repeat;
  background-color: #E0E0E0;
  mask-size: 0.6em auto;
  mask-position:bottom;
}

.sortdes{
  height: 0.5em;
  width: 1em;
  mask: url('assets/des.svg') no-repeat;
  background-color: #E0E0E0;
  mask-size: 0.6em auto;
  mask-position:bottom;
}

.sortasc:hover{
  background-color: red;
  cursor:pointer;
}

.sortdes:hover{
  background-color: red;
  cursor:pointer;
}

.parentHome{
  height: 2.5em;
  width: 2.5em;
  mask: url('assets/home.svg') no-repeat;
  background-color: #1e1e1e;;
  mask-size:  2.5em auto;
  mask-position:bottom;
}
.parentHome:hover{
  cursor:pointer;
  background-color:DarkBlue;
}
</style>
