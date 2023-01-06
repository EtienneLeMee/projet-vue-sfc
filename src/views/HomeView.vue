<template>
  <div class="home">
    <Home/>
  </div>
  <div class="nav">
    <Nav/>
  </div>
  
  <title>Hogwarts Wiki</title>
</template>

<script>
// @ is an alias to /src
import Home from '@/components/Home.vue'
import Nav from '@/components/Nav.vue'

export default {
  name: 'HomeView',
  components: {
    Home,
    Nav
  },
  title:'Hog'
}
</script>

<style>
  nav {
    position: absolute;
    z-index: 3;
    right: 0;
    margin-right: 40px;
  }

  .home {
    position: absolute;
  }


</style>
