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
  height: 86vh;
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
</style>
