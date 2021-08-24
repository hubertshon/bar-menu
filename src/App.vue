<template>
  <div id="app">
    <router-view/>
  </div>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #dedede;
  background-color: rgb(55, 55, 55);
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

.bs-popover-right > .arrow::after{
  border-right-color: #1f1f1f !important;
}

.bs-popover-left > .arrow::after{
  border-left-color: #1f1f1f !important;
}

@import'~bootstrap/dist/css/bootstrap.css'


</style>
