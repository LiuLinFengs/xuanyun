<template>
  <div id="app">
    <router-view/>
  </div>

</template>

<style>
body{
  background-color: #f5f5f5;
  padding-inline-start: 0;
}
ul{
      padding-inline-start:0;
}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}
#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
</style>
