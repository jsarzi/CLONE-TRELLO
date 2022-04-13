<template>
  <nav>
    <router-link to="/"></router-link>
    <router-link id ="about" to="/readme">Read Me</router-link>
    <img id="imgCoding" src="https://www.coding-academy.fr/wp-content/uploads/2017/10/EPITECH-LOGO-CODINGACADEMY-QUADRI-2021.png">
    <!--<router-link to="/test">App</router-link>-->
  </nav>
  <router-view/>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  overflow: scroll;
}
nav {
  padding: 30px;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
}

nav a.router-link-exact-active {
  color: #42b983;
}
#about{
  position: fixed;
  top: 3%;
  right: 5%;
  color:black;
  font-family: Avenir, Helvetica, Arial, sans-serif;
}
#imgCoding{
height: 100px;
width: 200px;
position: fixed;
  top: 5%;
  left: 2%;
}
</style>
