<template>
  <div id="app">
    <div id="nav">
      <router-link to="/"><div class="divLink">Home</div></router-link>
      <router-link to="/about"><div class="divLink">About</div></router-link>
      <router-link to="/seedboxFiles"><div class="divLink">Seedbox Files</div></router-link>
    </div>
    <router-view/>
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
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding-top: 15vh;
  float:left;
  width: 10vw;
  height: 85vh;
  background-color: #1e1e1e;
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
</style>
