<template>
  <div id="app">
    <nav>
      <router-link to="/">Home</router-link>
      <router-link to="/about">About</router-link>
    </nav>

    <router-view />
  </div>
</template>

<script>

export default {
  name: 'App',
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Montserrat:wght@400;700&display=swap');

body {
  background-color: #eee;
  font-family: 'Montserrat', sans-serif;
  display: grid;
  grid-template-rows: auto;
  justify-items: center;
  padding-top: 50px;
}
body, html {
  margin: 0;
  height: 100%;
}
#app {
  width: 50%;
}

nav {
  margin: 0 0 50px;
}

nav a {
  padding: 10px;
  text-decoration: none;
  background-color: #fff;
  border-radius: 3px;
  color: rgb(0,110,255);
  margin-right: 15px;
}
</style>
