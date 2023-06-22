<template>
  <nav>
    <router-link to="/">Home</router-link> |
    <router-link to="/list">List</router-link>
  </nav>
  <router-view/>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  color: #f5f5f5db;
}
body {
  padding: 0;
  margin: 0;
  height: 100%;
  max-height: 100vh;
  overflow: auto;
  background: #084040e8;
}
nav {
  padding: 50px;
}

nav a {
  font-weight: bold;
  color: #f5f5f5db;
}

nav a.router-link-exact-active {
  color: #adf;
}
</style>
