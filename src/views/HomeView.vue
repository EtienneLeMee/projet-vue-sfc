<template>
  <div class="home">
    <Header/>
  </div>
  <title>Hogwarts Wiki</title>
</template>

<script>
// @ is an alias to /src
import Header from '@/components/Header.vue'

export default {
  name: 'HomeView',
  components: {
    Header
  },
  title:'Hog'
}
</script>

<style>

</style>
