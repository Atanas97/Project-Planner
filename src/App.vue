<template>
  <Navbar />
  <router-view/>
</template>
<script>
import Navbar from './components/Navbar.vue'

export default{
  components:{
    Navbar
  }
}
</script>
<style>

  .main-nav {
    text-align: center;
    margin: 40px auto;
  }
  .main-nav a{
    display: inline-block;
    text-decoration: none;
    margin: 0 10px;
    color: #999;
    font-size: 18px;
    text-transform: capitalize;
  }
  a.router-link-active {
    border-bottom: 2px solid #00ce89;
    padding-bottom: 4px;
  }
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  max-width: 600px;
  margin: 0 auto;
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
